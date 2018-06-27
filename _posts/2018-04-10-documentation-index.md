---
layout: documentation
title: Índice
description: 
categories:
comments: false
permalink: docs
---

<ul>
  {% for post in site.posts reversed %}
    {% if post.title != 'Índice' %}
      <li><a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a></li>
    {% endif %}    
  {% endfor %}
</ul>
