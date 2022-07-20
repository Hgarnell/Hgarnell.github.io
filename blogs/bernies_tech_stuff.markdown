---
layout: page
permalink: blogs/bernies_tech_stuff
title: Bernies Tech Stuff Blog
---
#Bernies Tech Stuff

A place to share my progress in learing cybersecurity and other techy ventures I do :)

{% for bernies_tech_stuff in site.bernies_tech_stuff %}
- <a href = "{{bernies_tech_stuff.url | prepend: site.baseur}}" >
 {bernies_tech_stuff.date | date: "%Y-%m-%d"}}  {{ bernies_tech_stuff.title }}
</a>

{% endfor %}
