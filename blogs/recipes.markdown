---
layout: page
permalink: blogs/recipes
title: Recipe index
---
# Recipes

Here are a few of my recipes that I make most often! Mostly Japanese homecooking that frequents my stomach often

{% for recipes in site.recipes %}
-<a href="{{ recipes.url | prepend: site.baseurl }}"> {{ recipes.date | date: "%Y-%m-%d" }} {{recipes.title}}
</a>
{% endfor %}
