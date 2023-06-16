---
layout: page
permalink: blogs/bernies_tech_stuff
title: Bernies Tech Stuff Blog
---

# Bernies Tech Stuff

A place to share my progress in learing cybersecurity and other techy ventures I do :)

{% assign blog_posts = site.bernies_tech_stuff | where: "tags", "blog" | sort: 'date' | reverse %}
{% assign project_posts = site.bernies_tech_stuff | where: "tags", "project" | sort: 'date' | reverse %}

<h2>Projects</h2>
{% for post in project_posts %}
<a href = "{{post.url | prepend: site.baseurl}}" > - {{post.date | date: "%Y-%m-%d"}}  {{ post.title }}</a>
{% endfor %}

<h2>Blogs</h2>
    {% for post in blog_posts %}
<a href = "{{post.url | prepend: site.baseurl}}" > - {{post.date | date: "%Y-%m-%d"}}  {{ post.title }}</a>
{% endfor %}

