---
layout: default
title: News
permalink: /news/
---

<header class="page-header">
  <p class="eyebrow">Updates</p>
  <h1>News</h1>
  <p>A lightweight timeline for talks, papers, teaching, and other updates.</p>
</header>

<section class="panel page-panel">
  {% include news-list.html items=site.data.news %}
</section>
