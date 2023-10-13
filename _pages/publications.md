---
layout: page
permalink: /publications/
title: publications
description: publications in journals and conferences.
nav: true
years: [2023]
nav_order: 1
---

<!-- _pages/publications.md -->
<div class="publications">

{%- for y in page.years %}
  <h2 class="year">{{y}}</h2>
  {% bibliography -f papers -q @*[year={{y}}]* %}
{% endfor %}

</div>