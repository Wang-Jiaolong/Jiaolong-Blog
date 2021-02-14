---
layout: page
title: Links
description: 没有链接的博客是孤独的
keywords: 友情链接
comments: false
menu: 链接
permalink: /links/
---

# My Projects

> Something useless but interesting

<ul>
{% for link in site.data.links %}
  {% if link.src == 'life' %}
  <li><a href="{{ link.url }}" target="_blank" style="color: gray">{{ link.name}}</a></li>
  {% endif %}
{% endfor %}
</ul>

# 常用网站

> Official Website

<ul>
{% for link in site.data.links %}
  {% if link.src == 'www' %}
  <li><a href="{{ link.url }}" target="_blank" style="color: gray">{{ link.name}}</a></li>
  {% endif %}
{% endfor %}
</ul>


> Online Tools

<ul>
{% for link in site.data.links %}
  {% if link.src == 'tool' %}
  <li><a href="{{ link.url }}" target="_blank" style="color: gray">{{ link.name}}</a></li>
  {% endif %}
{% endfor %}
</ul>