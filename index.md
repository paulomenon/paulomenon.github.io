---
layout: single
author_profile: true
title: "Paulo Menon — Senior Architect | Cloud, AI, DevOps & Open Source"
description: "Paulo Menon's blog — Senior Architect with 26+ years in IT sharing insights on cloud architecture, AI, MLOps, DevOps, GitOps, Kubernetes, and open-source solutions."
---

Welcome to my personal website! I'm Paulo Menon, a Senior Architect with over 26 years of expertise in IT.

I specialise in cloud solutions, software architecture, AI, MLOps, GitOps, DevOps, and open-source technologies, leveraging Kubernetes and other cloud platforms. My experience spans application development, cloud architecture, automation, CI/CD pipelines, cloud migration, and AI solutions. [Learn more about me](/welcome-page/)

---

# About This Blog

This blog is where I share insights, tutorials, and experiences from my work.
Whether you're looking to learn about cloud architecture, DevOps best practices,
or software development patterns, you'll find practical content drawn from
real-world projects.

Feel free to explore the [Blog](/blog/) for my latest posts, or connect with me
on [LinkedIn](https://linkedin.com/in/paulomenon) or
[GitHub](https://github.com/paulomenon).

---

# Recent Publications

{% assign count = 0 %}
{% for post in site.posts %}
{% unless post.hidden %}
{% if count < 5 %}
- [{{ post.title }}]({{ post.url }}) — *{{ post.date | date: "%b %Y" }}*
{% assign count = count | plus: 1 %}
{% endif %}
{% endunless %}
{% endfor %}

[View all publications &rarr;](/publications/)
