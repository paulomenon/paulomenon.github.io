---
layout: post
title: AVI networks proxy for Kafka Streams on Openshift
date: 2024-04-16 12:00:00 +0000
description: AVI proxy configuration for AMQ Stream aka Kafka Stream using Strimiz on Openshift/Kubernets. # Add post description (optional)
img: modernisation_dict.jpg # Add image post (optional)
tags: [AVI network,RH AMQ Stream,Kafka Stream,Strimiz] # add tag

---
Today I want to show you a real scenario that I configured a few years ago, I was using Strimzi 0.15.0 and Kafka Steams  2.2.x.  which could be something you will be facing as well.

In this scenario, I am using Openshift 4.x (community version known as OKD.oi) and deploying Kafka using the Strimzi operator.


<!--more-->
For this use case, all traffic goes through AVI, therefore it’s necessary to configure the AMQ Stream (Kafka) cluster for the external router via AVI proxy. 

**Problem** 

After your RH AMQ Stream cluster has deployed the cluster operator uses Strimizi with the AVI annotation as you can see below. 

<div class="code-snippet">
  <div class="highlight">
{% highlight yaml %}
template:
  externalBootstrapRoute:
    metadata:
      annotations:
        avi_proxy: '{"dedicated_route": true}'
        openshift.io/host.generated: 'true'
  externalBootstrapService:
    metadata:
      annotations:
        avi_proxy: >-
          {"virtualservice":{"services": [{"port": 443,
          "enable_ssl":true}],"auto_allocate_ip":true,"east_west_placement":false}}
  perPodRoute:
    metadata:
      annotations:
        avi_proxy: '{"dedicated_route": true}'
        openshift.io/host.generated: 'true'
{% endhighlight %}
<button class="copy-button" onclick="copyCode(this)" title="Copy to Clipboard"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" width="24" height="24"><path d="M 8 2 L 8 4 L 4 4 L 4 20 L 16 20 L 16 16 L 18 16 L 18 22 L 2 22 L 2 2 Z M 10 4 L 18 4 L 18 14 L 16 14 L 16 6 L 10 6 Z M 6 8 L 14 8 L 14 18 L 6 18 Z M 10 10 L 12 10 L 12 16 L 10 16 Z"></path></svg></button>
</div>
</div>

Then AVI will configure the service route using the service port 9094 by default.


When you try to send messages using the consumer like this command below for testing propose:
<div class="code-snippet">
  <div class="highlight">
{% highlight shell %}
./kafka-console-producer.sh --broker-list <external bootstap route hostname>:443 --topic <your topic name> --producer.config sslconfig.properties
{% endhighlight %}
<button class="copy-button" onclick="copyCode(this)" title="Copy to Clipboard"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" width="24" height="24"><path d="M 8 2 L 8 4 L 4 4 L 4 20 L 16 20 L 16 16 L 18 16 L 18 22 L 2 22 L 2 2 Z M 10 4 L 18 4 L 18 14 L 16 14 L 16 6 L 10 6 Z M 6 8 L 14 8 L 14 18 L 6 18 Z M 10 10 L 12 10 L 12 16 L 10 16 Z"></path></svg></button>
</div>
</div>

**You will get this following ERROR:**

//add code here

**Solution**

RH AMQ Stream cluster/Kafka Stream cluster talks with every single member of the cluster via TLS port 443 when it’s exposed as mentioned before AVI picked up the Openshift service port in every cluster member which is 9094, therefore this needs to be changed in AVI in every single service port it to 443.

At the AVI network dashboard click on service go to > edit virtual service in Service Port then change it from 9094 to 443 in every cluster member including the external bootstrap service route shown in the AVI configuration.

Some useful links:

• [Openshift community](https://www.okd.io/)

• [Strimzi operator](https://strimzi.io/)

• [AVI networks proxy support page](https://avinetworks.com/docs/17.2/proxy-protocol-support/)

• [AVI documentation](https://avinetworks.com/docs/)


>This page was last update at {{ "now" | date: "%Y-%m-%d %H:%M" }} 


