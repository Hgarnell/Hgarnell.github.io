---
layout: page
title: Bernies Tech Stuff Blog
---
#Bernies Tech Stuff

Here are a few of mapanese homecooking that frequents my stomach often

{% for bernies_tech_stuff in site.bernies_tech_stuff %}

<a href="{{ bernies_tech_stuff.url | prepend: site.baseurl }}">
  - <p>{"{{ bernies_tech_stuff.date | date: "%Y-%m-&d" }}" |  bernies_tech_stuff.title}</p>
</a>

{% endfor}
