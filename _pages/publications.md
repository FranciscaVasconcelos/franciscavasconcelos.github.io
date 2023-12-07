---
layout: page
permalink: /publications/
title: publications
description: Publications by categories in reversed chronological order. * denotes equal contribution or alphabetical ordering.
years: [2023, 2022, 2021, 2020, 2019, 2016] 
display_categories: [preprint, journal, conference, article, thesis]
nav: true
nav_order: 1
---

<div class="publications">
{% for category in page.display_categories %}
  <h2 class="category">{{category}}</h2>
  {% for y in page.years %}
<!---    <h2 class="year">{{y}}</h2> --->
    {% bibliography -f papers -q @*[dcat={{category}} && year={{y}}]* %}
  {% endfor %}
{% endfor %}

</div>