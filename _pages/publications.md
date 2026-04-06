---
permalink: /publications/
title: "Publications"
author_profile: true
---

{% for post in site.posts %}
{% unless post.hidden %}
- [{{ post.title }}]({{ post.url }}) — *{{ post.date | date: "%b %Y" }}*
{% endunless %}
{% endfor %}
