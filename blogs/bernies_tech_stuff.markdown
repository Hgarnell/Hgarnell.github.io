---
layout: page
permalink: blogs/bernies_tech_stuff
title: Bernies Tech Stuff Blog
---
# Bernies Tech Stuff

A place to share my progress in learing cybersecurity and other techy ventures I do :)

{% assign posts = site.bernies_tech_stuff | sort: 'date' | reverse %}
{% for post in posts %}
<a href = "{{post.url | prepend: site.baseurl}}" > - {{post.date | date: "%Y-%m-%d"}}  {{ post.title }}</a>
{% endfor %}
