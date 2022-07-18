---
layout: page
permalink: blogs/sauls_phd_log
title: Recipe index
---
# Saul's PHD Log

Saul is a current PHD canidate at [Auckland University of Technology](https://aut.ac.nz/A)

His Thesis will attempt to find key patterns and non-biological analogues that can simulate a Minimal Affective System (MAS) by experimentation with Computational Biology. Broken into three phases, the Thesis will be grounded in well-established priors from Mathematics, Neurophysiology and Computational Biology. The first phase will establish a Bayesian statistical Inference framework (Free Energy Principle) to meaningfully correlate the phenomenal activity of a biological organism. The second phase focuses on the research needed to explore and construct neurophysiological models of affects. The research will attempt to build an initial model based on the connectome of a Fruit Fly, Drosophila Melanogaster. The third phase will formulate a computational model that rigorously describes the framework and data needed to support the simulation of an artificial MAS.

{% for sauls_phd_log in site.sauls_phd_log %}

<a href="{{ sauls_phd_log.url | prepend: site.baseurl }}">
  <p> - {"{sauls_phd_log.date | date: "%Y-%m-&d" }" | sauls_phd_log.title }</p>
</a>

{% endfor %}
