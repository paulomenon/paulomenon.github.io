---
layout: post
title: Cloud Architecture Your Guide to Unlocking Digital Transformation! 
date: 2024-04-25 12:00:00 +0000
description: Cloud Architecture guide on Openshift/Kubernets. Your guide to unlocking digital transformation # Add post description (optional)
img: cloudcity_part1.png # Add image post (optional)
tags: [Cloud Architecture, Kubernetes, Openshift] # add tag

---

# Live in the Cloud Part 1

Are you new to cloud architecture or cloud in general? You came to the right place. Today I explore some cloud architecture key concepts and clarify some myths around the digital transformation journey.

This is part 1 of 4 a series of blogs to guide you to unlocking digital transformation.
<!--more-->

A few years ago a new starter junior IT person moved from network admin to more cloud admin DevOps type of role to try his luck in the new world of the cloud platform. This person's misconception was that cloud architecture gives you a client to be installed in the local user machine when they need to use an app or a simple pipeline app running in the cloud platform basically, anything that you need to use app-related in the cloud platform. Then the cloud platform will use the user's local machine resources.  

As a consultant in this area, I need to help people understand things and bring them up to speed for more than I was tempted to make a joke about it. So to clarify this whole confusion I asked back to him some questions to make him question himself and to understand why and where he got this concept from, soon after he started questioning himself I explained the basic concept of the cloud platform which is the complete opposite of what this person thought it was. 

As cloud platforms become more popular in different industries, some key concepts that used to be specialised knowledge are more common nowadays.

Still, I would like to debunk a few myths related to cloud workload migration and app modernisation/digital transformation journey.

<img src="../assets/img/myths.png">

**How to do the initial Sizing?**

One common question I get when teams prepare to move to the cloud is container sizing, determining the amount of space they need to configure for that particular application they are planning to move to the cloud. The answer is simple: regardless of how your application is utilising the cloud, it will continue to be used.

**What about Memory and CPU usage?**

Again another misconception people sometimes think is that because they move their workloads to the cloud it will magically use less memory or that the cloud platform will have a button to click to adjust the storage and memory use correctly. Unfortunately, that wasn’t the case by the time I wrote this, shortly a button with an AI behind it will calculate this base in some previous data analyses. 

**Will Performance improve?**

If you thought I would say “same” again you were wrong 😀 So it depends You can guess now, so the answers are the same as well, but the importance here is this now that you are moving your workload to the cloud it’s a great opportunity to run all the load and performance tests to get the correct memory and sizing to adjust correctly your quota that will create a more cost effect configuration for your applications. Platforms like Kubernetes can make use of HorizontalPodAutosacler (HPA), VerticalPodAutoscaler (VPA) and Kubernetes Event Driven Autoscaler (KEDA).

**Will my application work in High Availability?** 

Platforms like Kubernetes can make use of HorizontalPodAutosacler (HPA), VerticalPodAutoscaler (VPA) and Kubernetes Event Driven Autoscaler (KEDA).
However, if you are migrating your application the chances are that you don’t have health check endpoints exposed that could be used for such tools to collect those metrics. I will show you how to do this in another blog post.

# Conclusion

In conclusion, it’s fundamental to understand cloud architecture concepts for anyone looking to navigate the complexities of digital transformation. Remember moving to the cloud is not just about transferring your existing workloads, it’s about rethinking your architecture, and culture change to adopt a more DevOps approach and optimising them to fully leverage cloud capabilities.

I hope this helps you to start your journey to learn more about the cloud basic concepts even though I use Kubernetes as the example platform. 

Whether you're a beginner or looking to refine your expertise, this series will equip you with the knowledge to succeed in the evolving landscape of cloud computing.



>This page was last update at {{ "now" | date: "%Y-%m-%d %H:%M" }} 


