---
layout: page
title: About
description: Stay Hungry, Stay Foolish.
keywords: Jiaolong
comments: false
menu: 关于
permalink: /about/
---

我是Jiaolong

一个不懂艺术的艺术家

一个还没想好做什么的个人开发者

一个正在成长的程序员

## 联系

<ul>
{% for website in site.data.social %}
<li>{{website.sitename }}：<a href="{{ website.url }}" target="_blank">@{{ website.name }}</a></li>
{% endfor %}
<!-- {% if site.url contains 'jiaolong.space' %}
<li>
<img style="height:192px;width:192px;border:1px solid lightgrey;" src="{{ assets_base_url }}/assets/images/qrcode.jpg"/>
</li>
{% endif %} -->
</ul>
<svg id="mindmap"></svg>
<script src="https://cdn.jsdelivr.net/npm/d3@6.6.0"></script><script src="https://cdn.jsdelivr.net/npm/markmap-view@0.2.3"></script>
<script>((e,t,r)=>{const{Markmap:n}=e();window.mm=n.create("svg#mindmap",null==t?void 0:t(),r)})(()=>window.markmap,t=>{return t=t||window.d3,{color:(n=t.scaleOrdinal(t.schemeCategory10),t=>n(t.p.i))};var n},{"t":"heading","d":1,"p":{"lines":[0,1]},"v":"技能树","c":[{"t":"heading","d":2,"p":{"lines":[2,3]},"v":"后端","c":[{"t":"heading","d":3,"p":{"lines":[4,5]},"v":"Java","c":[{"t":"list_item","d":5,"p":{"lines":[6,7]},"v":"基础","c":[{"t":"list_item","d":7,"p":{"lines":[8,9]},"v":"基础"},{"t":"list_item","d":7,"p":{"lines":[9,10]},"v":"集合"},{"t":"list_item","d":7,"p":{"lines":[10,11]},"v":"多线程"},{"t":"list_item","d":7,"p":{"lines":[11,12]},"v":"反射"}]},{"t":"list_item","d":5,"p":{"lines":[13,14]},"v":"web"},{"t":"list_item","d":5,"p":{"lines":[14,15]},"v":"框架","c":[{"t":"list_item","d":7,"p":{"lines":[16,17]},"v":"Spring","c":[{"t":"list_item","d":9,"p":{"lines":[18,19]},"v":"SpringMVC"},{"t":"list_item","d":9,"p":{"lines":[19,20]},"v":"SpringBoot"},{"t":"list_item","d":9,"p":{"lines":[20,21]},"v":"SpringCloud"}]},{"t":"list_item","d":7,"p":{"lines":[22,23]},"v":"MyBatis"},{"t":"list_item","d":7,"p":{"lines":[23,24]},"v":"Shiro"}]}]}]},{"t":"heading","d":2,"p":{"lines":[25,26]},"v":"前端","c":[{"t":"heading","d":3,"p":{"lines":[27,28]},"v":"基础","c":[{"t":"list_item","d":5,"p":{"lines":[29,30]},"v":"HTML"},{"t":"list_item","d":5,"p":{"lines":[30,31]},"v":"CSS"},{"t":"list_item","d":5,"p":{"lines":[31,32]},"v":"jQuery"},{"t":"list_item","d":5,"p":{"lines":[32,33]},"v":"JavaScript"}]},{"t":"heading","d":3,"p":{"lines":[34,35]},"v":"框架","c":[{"t":"list_item","d":5,"p":{"lines":[36,37]},"v":"Vue"}]}]},{"t":"heading","d":2,"p":{"lines":[38,39]},"v":"操作系统","c":[{"t":"heading","d":3,"p":{"lines":[40,41]},"v":"Linux"}]},{"t":"heading","d":2,"p":{"lines":[42,43]},"v":"数据库","c":[{"t":"heading","d":3,"p":{"lines":[44,45]},"v":"MySQL"}]}]})</script>


## Skill Keywords

{% for skill in site.data.skills %}
### {{ skill.name }}
<div class="btn-inline">
{% for keyword in skill.keywords %}
<button class="btn btn-outline" type="button">{{ keyword }}</button>
{% endfor %}
</div>
{% endfor %}
