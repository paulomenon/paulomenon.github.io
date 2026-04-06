---
layout: single
title: "Red Hat Connectivity Link and MetalLB BGP Mode"
date: 2026-04-06 12:00:00 +0000
description: "How to configure Red Hat Connectivity Link with MetalLB in BGP mode on OpenShift, including F5 integration and traffic flow."
tags: [metallb, bgp, openshift, connectivity link, rhcl, f5, envoy, kubernetes, gateway api, real-world]
---

## Red Hat Connectivity Link and MetalLB BGP Mode on OpenShift

In this article, I want to walk you through a practical setup combining **Red Hat Connectivity Link (RHCL)** with **MetalLB in BGP mode** on OpenShift. This is a generic example where the architecture uses an external load balancer like **F5** in front of MetalLB to handle TLS termination and external traffic management. However, keep in mind that using an external load balancer is **not mandatory**. You can absolutely run MetalLB on its own without another load balancer — MetalLB is fully capable of assigning and advertising external IPs to your services by itself. The F5 integration shown here is just one common pattern you'll see in enterprise environments where centralised certificate management and advanced traffic policies are already in place.

Whether you're running a full production setup with F5 or a simpler lab environment with MetalLB only, the core concepts and configurations covered here still apply. Let's dive in!

---

## Red Hat Connectivity Link

Red Hat Connectivity Link uses the **Gateway API** to create a load balancer service for OpenShift Container Platform. This exposes the gateway directly from the cluster with a routable IP address. This is different from the traditional OCP routes exposed through the ingress controller. The Gateway is defined via a separate **Gateway custom resource**. The gateway uses a Redis (or compatible) database to store rate-limiting information when rate-limiting policies are in effect. The gateway will define a list of allowed host names for applications. Wild cards are supported (for example, `*.apps.example.com`). Gateway admins can set base policies for the gateway in the gateway namespace. The application admins can add and override these policies for each application. As you can see in the diagram below:

![Connectivity Link Application Flow](/assets/images/connectivityLinkApplicationFlow.png)

Application traffic flows directly through the gateway to the API producer. The application will define an **HTTPRoute** custom resource to expose the application through the gateway. The HTTPRoute object will define the application's host names.

For more detailed examples on configuring Red Hat Connectivity Link including gateways, HTTPRoutes, DNS policies, rate limiting, and auth policies, check out this reference repository: [connectivity-link-example](https://github.com/paulomenon/connectivity-link-example)

---

## MetalLB in BGP (Border Gateway Protocol) Mode

MetalLB is a load balancer implementation for bare-metal OpenShift clusters. It provides a way to expose services externally by assigning them IP addresses from a pool of available addresses. It is particularly useful in environments where cloud provider load balancers are not available, such as on-premises or edge deployments. It works by using standard networking protocols to allocate and manage IP addresses for services, allowing OpenShift to function similarly to cloud environments.

MetalLB operates in two modes:

- **Layer2 mode:** Only assigns IPs on the same subnet as the node interfaces.
- **BGP mode:** Advertises assigned IPs over BGP to your physical router/switch — IPs can be on any routable subnet, even public ones.

For more details, you can read the full article [HERE](https://docs.openshift.com/container-platform/latest/networking/metallb/metallb-configure-bgp-peers.html).

The article from Red Hat explains how to configure MetalLB in BGP (Border Gateway Protocol) mode to provide load balancing for Kubernetes clusters. It outlines the steps to set up MetalLB for dynamic IP allocation using BGP, enabling high availability and improved networking efficiency. The article also covers important concepts like peering with BGP routers and ensuring reliable communication between services within the cluster.

---

## F5 + MetalLB + Envoy Architecture

You can set up the F5 load balancer in front of the IP used by your OpenShift cluster. This works with MetalLB configured in BGP mode. In this setup, F5 manages the SSL/TLS certificates and routes traffic to the right services handled by Envoy inside OpenShift. This ensures proper traffic flow and centralised certificate management. Just make sure F5 is configured to efficiently handle traffic to your OpenShift services.

BGP mode is ideal, as you can assign public IPs or external VLAN-routed subnets and perform IP-level routing outside the node.

---

## Traffic Flow Overview

The traffic flow in this setup is as follows:

![Traffic Flow](/assets/images/trafficFlow.png)

1. **F5 load balancer** receives incoming traffic and forwards it to the MetalLB-assigned IP address.
2. **MetalLB** assigns an IP from the configured pool to the LoadBalancer service.
3. The **BGP peer** (your router) learns about the assigned IP and routes traffic to the OpenShift cluster.
4. The **Envoy proxy** within the OpenShift cluster processes the incoming traffic and forwards it to the appropriate service or pod.
5. The service or pod responds, and the response is sent back through the Envoy proxy to the F5 load balancer, which then returns it to the client.

---

## MetalLB Configuration

### Step 1: Create the IPAddressPool

The configuration will look something like this. Create the MetalLB pool to include the desired range:

<div class="code-snippet">
  <div class="highlight">
{% highlight yaml %}
apiVersion: metallb.io/v1beta1
kind: IPAddressPool
metadata:
  name: f5-ip-pool
  namespace: metallb-system
spec:
  addresses:
    - 192.168.2.10-192.168.2.50  # A pool of IPs you want MetalLB to assign
  autoAssign: true                # MetalLB will automatically assign IPs from this range
  avoidBuggyIPs: false            # BGP for routing IPs to your network
{% endhighlight %}
<button class="copy-button" onclick="copyCode(this)" title="Copy to Clipboard"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" width="24" height="24"><path d="M 8 2 L 8 4 L 4 4 L 4 20 L 16 20 L 16 16 L 18 16 L 18 22 L 2 22 L 2 2 Z M 10 4 L 18 4 L 18 14 L 16 14 L 16 6 L 10 6 Z M 6 8 L 14 8 L 14 18 L 6 18 Z M 10 10 L 12 10 L 12 16 L 10 16 Z"></path></svg></button>
</div>
</div>

In this example, it will allow MetalLB to assign IP addresses in the range `192.168.2.10-192.168.2.50` to any LoadBalancer service.

![IP Address Pools](/assets/images/ipAddressPool.png)

---

### Step 2: Deploy a BGP Peer

Then, any LoadBalancer service can be assigned one of those IPs, even if it's outside the host subnet. Deploy a BGP peer to your network's router:

<div class="code-snippet">
  <div class="highlight">
{% highlight yaml %}
apiVersion: metallb.io/v1beta2
kind: BGPPeer
metadata:
  name: f5-bgp-peer
  namespace: metallb-system
spec:
  peerAddress: 192.168.2.1    # IP of the F5 (or upstream BGP router)
  peerASN: 65001              # ASN of the F5 BGP speaker
  myASN: 64512                # ASN assigned to MetalLB
  #ebgpMultihop: true         # To set if the BGPPeer is multi-hops away. Needed for FRR mode only.
{% endhighlight %}
<button class="copy-button" onclick="copyCode(this)" title="Copy to Clipboard"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" width="24" height="24"><path d="M 8 2 L 8 4 L 4 4 L 4 20 L 16 20 L 16 16 L 18 16 L 18 22 L 2 22 L 2 2 Z M 10 4 L 18 4 L 18 14 L 16 14 L 16 6 L 10 6 Z M 6 8 L 14 8 L 14 18 L 6 18 Z M 10 10 L 12 10 L 12 16 L 10 16 Z"></path></svg></button>
</div>
</div>

- **peerAddress: 192.168.2.1** — This is the IP address of your router that will be used for BGP peering.
- **peerASN: 65001** — This is the ASN of your router. You need to know this from your router's configuration.
- **myASN: 64512** — This is the ASN for MetalLB. Typically, clusters use a private ASN such as 64512, but you can adjust it if needed.


> You can also enable **BFD (Bidirectional Forwarding Detection)** for fast failure detection by adding `bfdprofile: default` to the spec. This is optional but recommended for production environments where fast failover is critical.

---

### Step 3: Create the BGP Advertisement

The **BGPAdvertisement** resource tells MetalLB which IP address pools it is allowed to advertise to the network. Without this object, MetalLB will not publish any IPs, and services will remain unreachable, even if they have an assigned IP from a pool. Without a corresponding BGPAdvertisement, the IPAddressPool is considered inactive. This is a necessary step to "enable" the pool for assignment and advertisement, even in BGP mode.

Create a BGP advertisement object:

<div class="code-snippet">
  <div class="highlight">
{% highlight yaml %}
kind: BGPAdvertisement
apiVersion: metallb.io/v1beta1
metadata:
  name: advertise-bgp-pool
  namespace: metallb-system
spec:
  ipAddressPools:
    - f5-ip-pool
{% endhighlight %}
<button class="copy-button" onclick="copyCode(this)" title="Copy to Clipboard"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" width="24" height="24"><path d="M 8 2 L 8 4 L 4 4 L 4 20 L 16 20 L 16 16 L 18 16 L 18 22 L 2 22 L 2 2 Z M 10 4 L 18 4 L 18 14 L 16 14 L 16 6 L 10 6 Z M 6 8 L 14 8 L 14 18 L 6 18 Z M 10 10 L 12 10 L 12 16 L 10 16 Z"></path></svg></button>
</div>
</div>

This command below applies BGP peer on OpenShift.

<div class="code-snippet">
  <div class="highlight">
{% highlight bash %}
oc apply -f bgp-peer.yaml
{% endhighlight %}
<button class="copy-button" onclick="copyCode(this)" title="Copy to Clipboard"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" width="24" height="24"><path d="M 8 2 L 8 4 L 4 4 L 4 20 L 16 20 L 16 16 L 18 16 L 18 22 L 2 22 L 2 2 Z M 10 4 L 18 4 L 18 14 L 16 14 L 16 6 L 10 6 Z M 6 8 L 14 8 L 14 18 L 6 18 Z M 10 10 L 12 10 L 12 16 L 10 16 Z"></path></svg></button>
</div>
</div>

![BGP Peer](/assets/images/bgpPeer.png)

---

### Step 4: Create the Gateway Service

Now, create a service that will get an IP from MetalLB and be advertised via BGP:

<div class="code-snippet">
  <div class="highlight">
{% highlight yaml %}
apiVersion: v1
kind: Service
metadata:
  name: envoy
  namespace: rhcl-sandbox
  annotations:
    metallb.universe.tf/address-pool: f5-ip-pool
spec:
  type: LoadBalancer
  selector:
    app: envoy
  ports:
    - name: http
      protocol: TCP
      port: 80
      targetPort: 8080
    - name: https
      protocol: TCP
      port: 443
      targetPort: 8443
{% endhighlight %}
<button class="copy-button" onclick="copyCode(this)" title="Copy to Clipboard"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" width="24" height="24"><path d="M 8 2 L 8 4 L 4 4 L 4 20 L 16 20 L 16 16 L 18 16 L 18 22 L 2 22 L 2 2 Z M 10 4 L 18 4 L 18 14 L 16 14 L 16 6 L 10 6 Z M 6 8 L 14 8 L 14 18 L 6 18 Z M 10 10 L 12 10 L 12 16 L 10 16 Z"></path></svg></button>
</div>
</div>

MetalLB will assign an IP from the pool, and your router will learn that route via BGP. In this service example:

![Create Service](/assets/images/createService.png)

- MetalLB will automatically assign an IP from the IP pool (`192.168.2.10-192.168.2.50`).
- The IP will be advertised to your router via BGP, allowing external access to your service.

---

## How BGP Mode Works

When MetalLB is in BGP mode, it acts like a router:

- It advertises the IP addresses (from your LoadBalancer services) to your physical network routers.
- This way, traffic for those IPs is routed directly to the cluster nodes, even if the IPs are not in the node's local subnet.
- MetalLB advertises `192.168.2.x` to your router at `192.168.2.1`.
- Your router knows: *"If I get traffic for 192.168.2.10, send it to the OpenShift cluster."*
- BGP allows MetalLB to "announce" LoadBalancer IPs to your network routers.
- So when a Gateway (Ingress or API) gets an IP from MetalLB, your physical network knows how to reach it.

---

## Envoy Deployment and Service Integration

The Deployment named **envoy** manages the lifecycle of Envoy proxy pods, ensuring high availability and scalability. The corresponding Service, also named **envoy**, is defined as a `LoadBalancer` type, which allows MetalLB to assign an external IP address to it. This IP is then advertised to the F5 load balancer via BGP. F5, serving as the external gateway, forwards incoming HTTPS traffic to the MetalLB-assigned IP address. Upon arrival, the traffic is routed to the Envoy pods by the Service, where Envoy processes and forwards it to the appropriate services and pods within the OpenShift cluster. This coordinated interaction ensures seamless external-to-internal traffic flow within the architecture.

Here is an example of the Envoy deployment:

<div class="code-snippet">
  <div class="highlight">
{% highlight yaml %}
apiVersion: apps/v1
kind: Deployment
metadata:
  name: envoy
  namespace: rhcl-sandbox
spec:
  replicas: 2
  selector:
    matchLabels:
      app: envoy
  template:
    metadata:
      labels:
        app: envoy
    spec:
      containers:
        - name: envoy
          image: envoyproxy/envoy:v1.25-latest
          ports:
            - containerPort: 8080
            - containerPort: 8443
          volumeMounts:
            - name: config
              mountPath: /etc/envoy
      volumes:
        - name: config
          configMap:
            name: envoy-config
{% endhighlight %}
<button class="copy-button" onclick="copyCode(this)" title="Copy to Clipboard"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" width="24" height="24"><path d="M 8 2 L 8 4 L 4 4 L 4 20 L 16 20 L 16 16 L 18 16 L 18 22 L 2 22 L 2 2 Z M 10 4 L 18 4 L 18 14 L 16 14 L 16 6 L 10 6 Z M 6 8 L 14 8 L 14 18 L 6 18 Z M 10 10 L 12 10 L 12 16 L 10 16 Z"></path></svg></button>
</div>
</div>

---

## Reference Repositories

All the configuration files used in this article are available in the following repositories:

- [metallb-bgp-example](https://github.com/paulomenon/metallb-bgp-example) — MetalLB BGP mode configuration examples including IPAddressPool, BGPPeer, BGPAdvertisement, and sample services.
- [connectivity-link-example](https://github.com/paulomenon/connectivity-link-example) — Red Hat Connectivity Link (RHCL) examples for gateways, DNS policies, rate limiting, auth policies, and more.

---

## Conclusion

Combining Red Hat Connectivity Link with MetalLB in BGP mode gives you a powerful and flexible way to expose your OpenShift services with proper routing, load balancing, and traffic management — all without depending on a cloud provider. Whether you're integrating with an external load balancer like F5 for centralised TLS termination or running MetalLB standalone in a simpler setup, the Gateway API approach provides a clean and scalable model for managing ingress traffic.

I hope this guide helps you get started with your own setup. As always, adapt the configurations to match your specific environment, network topology, and security requirements. Thanks for reading, and see you next time! 👋


>This page was last update at {{ "now" | date: "%Y-%m-%d %H:%M" }} 

