---
layout: page
title: Recipes by Tags
---

{% assign tags_list = site.tags %}  
{% if tags_list.first[0] == null %}
{% for tag in tags_list %} 
<a href="#{{ tag }}" class="big-button gray">{{ tag | capitalize }} {{ site.tags[tag].size }}</a>
{% endfor %}
{% else %}
{% for tag in tags_list %} 
<a href="#{{ tag[0] }}" class="big-button gray">{{ tag[0] | capitalize }} {{ tag[1].size }}</a>
{% endfor %}
{% endif %}
{% assign tags_list = nil %}
</ul>

{% for tag in site.tags %} 
<h2 id="{{ tag[0] }}">{{ tag[0] | capitalize }}</h2>
<ul class="post-list">
{% assign pages_list = tag[1] %}  
{% for post in pages_list %}
{% if post.title != null %}
{% if group == null or group == post.group %}
<li><a href="{{ site.url }}{{ post.url }}">{{ post.title }}<span class="entry-date"><time datetime="{{ post.date | date_to_xmlschema }}" itemprop="datePublished">{{ post.date | date: "%B %d, %Y" }}</time></a></li>
{% endif %}
{% endif %}
{% endfor %}
{% assign pages_list = nil %}
{% assign group = nil %}
</ul>
{% endfor %}
