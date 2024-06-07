---
layout: post
title: Cloud Features - Live in the Cloud Part 3! 
date: 2024-06-07 12:00:00 +0000
description: Discover why moving your workload to the cloud offers more than just maintaining the same resource usage. This blog highlights the strategic benefits of cloud architecture, including scalability, high availability, observability, flexibility, faster delivery, automation, serverless computing, and cloud-native design. Learn how to leverage these advantages to transform your business. # Add post description (optional)
img: cloud_part3.png # Add image post (optional)
tags: [Cloud Architecture, Kubernetes, Cloud Migration Benefits, High Availability,Scalability,Flexibility, Pipelines, Automation, Digital Transformation] # add tag

---

# Live in the Cloud Part 3 - Cloud Features

After considering all the four points in the previous post, [Cloud Architecture Part 1](https://paulomenon.github.io/cloud-architecture-your-guide-to-unlocking-digital-transformation/), when you move your workload to the cloud, it has the same CPU, memory and storage usage as before why bother to move to the cloud?

The simple answer is that Steve Jobs moved to iCloud 😂 I will move as well, no, of course not, the motivations are broader and more strategic, such as you can scale your business faster, deliver more features, and plugin more resources with zero downtime, so on and so for. We will explore more about a few points in the cloud architecture that motivate people to move to this platform in the next section below  

Now I will give some overview of a few basic cloud architecture concepts that you need to keep in mind

Designing a cloud architecture involves various considerations to ensure scalability, reliability, security, and cost-effectiveness. Here are some key aspects to consider:

**1. Scalability** 

You can add more resources to it, making horizontal scale easy to increase loads more memory, CPU and storage space.

Features like auto scaling provided by cloud services providers dynamically adjust resources based on demand, however, be aware that some providers will charge extra for any extra resources over the limit allowance agreed in the contract.

In Kubernetes, for example, you can use HorizontalPodAutosacler (HPA) which will create the number of pod replicas based on CPU usage or custom metrics. You can also use VerticalPodAutoscaler (VPA) to adjust pod resource requests and limits based on the actual usage of those resources. That will allow you to be more cost efficient and make your application use the correct sizing 

However it’s not magic here if you are moving a legacy workload to the cloud it will require some level of refractory to add health checks in your application so the platform can collect those metrics, if you are starting from a green field project then keep this in mind to implement health check endpoints to achieve better scalability and other benefits you can see in this post here.
 

**2. High Availability and Fault Tolerance**

Ok, I know you can achieve high availability and fault tolerance using VMs, I can also do that using cloud architecture, you may learn in this next session the benefits and why people are moving to the cloud to achieve this too.

You can have multiple data centres distributed across different regions to implement fault tolerance and recovery scenarios.

Use a high available load balance to distribute incoming traffic avoiding a single point of failure. 

Normally implementing HA and fault tolerance in a virtual environment typically involves investing in hardware, additional servers, storage, and networking equipment. The cloud often offers more cost-effective HA solutions with pricing modules from cloud providers allowing them to scale resources based on demand. 

Moreover, in a VM environment achieving zero downtime periods for maintenance can be challenged due to the limitations of traditional hardware-based redundancy

Cloud platforms like Kubernetes offer built-in tools and services for achieving high availability and near-zero downtime such as HorizontalPodAutosacler (HPA), VerticalPodAutoscaler (VPA), Kubernetes Event Driven Autoscaler (KEDA), Kubernetes Cluster Management Services, Automated Load Balancing,
Cluster Autoscaler and more.
   

**3. Observability and Monitoring** 

Add a monitoring system for container and application health and configure alerts to respond to failures quickly

Logging aggregation to collect application, infra and system logs to a centralised solution to store it and a dashboard to visualise it. 

Implement redundancy for critical components such as databases, storage, and compute instances.

**4. Flexibility**

You can easily scale resources up or down in response to changing workload demands.

You can automate this, allowing applications to quickly respond to changing business needs and market conditions. This is achieved through microservice architecture, loosely decoupled architectures that can be easily modified or extended, with independent life cycles, deployment and features.

**5. Deliver faster** 

You can apply GitOps methodologies to manage and automate infrastructure and applications' deployment, configuration, and operation. In Kubernetes, you can use Helm charts, which function as managed packages similar to DNF, npm, and homebrew for their respective environments/systems.

You can use CiCd pipeline tools such as Jenkins, Travis, Tekton, GitLab flow, GitHub Actions, and others.

For GitOps tools I recommend having a look into Argod CD and Flux. 

Potentially for example you can implement your pipelines using GitHub Actions that will trigger pipelines to build and package the application into Helm charts, which will create a version for that helm chart, Once the Helm charts are built, GitHub Actions can use ArgoCD's API to initiate a deployment by updating the Git repository containing the manifests.

Argo CD, configured to watch the Git repository, detects the changes and automatically applies them to the Kubernetes cluster, ensuring that the desired state is synchronised with the cluster state.


**6. Automation**
 
Automate routine management tasks using infrastructure as code (IaC) and configuration management tools. Popular tools for that is Terraform and Ansible

**7. Serverless Computing**
 
Serverless computing platforms abstract away infrastructure management, allowing you to focus solely on writing code. These platforms automatically handle scaling, fault tolerance, and high availability, making it easier to build resilient applications without managing servers.

**8. Cloud Native**

In the simplest terms, "cloud native" means designing and running applications specifically for cloud environments, taking full advantage of cloud services and principles to be more agile, scalable, and efficient. In another term, you will compile your code to binary native to that container OS which will move across different environments.

Traditional Java applications often entail property configurations, component scanning, dependency injection, runtime initialisation, and more. These can contribute to longer startup times that make it difficult to scale faster a Cloud Native application will move some of those times from the startup time to compilation time focusing on minimal dependencies and a lightweight framework, leading to faster startup time making it faster to horizontal scale.



# Conclusion

Leveraging features like auto-scaling, high-availability configurations, robust monitoring systems, and flexible resource management, businesses can scale faster, ensure reliability, and optimize costs. Cloud platforms such as Kubernetes offer built-in tools to enhance scalability and minimize downtime, making it easier to manage resources and respond to changing demands.

Moreover, automation and serverless computing simplify infrastructure management, allowing teams to focus on innovation and delivering new features. Embracing cloud-native design ensures that applications are agile, efficient, and ready to meet the needs of modern business environments.

As you continue your journey into cloud architecture, keep these foundational concepts in mind to fully realize the benefits of cloud computing. Stay tuned for more insights and practical tips in future posts to help you navigate and optimize your cloud transformation.



>This page was last update at {{ "now" | date: "%Y-%m-%d %H:%M" }} 


