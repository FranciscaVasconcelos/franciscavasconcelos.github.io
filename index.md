---
layout: default
title: Home
---

{% assign profile = site.data.profile %}

<section class="hero">
  <div class="hero-copy">
    <p class="eyebrow">{{ profile.subtitle }}</p>
    <h1>{{ profile.name }}</h1>
    <p class="lead">{{ profile.tagline }}</p>
    <p class="contact-line"><a href="mailto:{{ profile.email }}">{{ profile.email_display }}</a></p>
    <div class="quick-links" aria-label="Quick links">
      {% for link in profile.links %}
        {% include link.html url=link.url label=link.label %}
      {% endfor %}
    </div>
  </div>
  <figure class="portrait-card">
    <img src="{{ profile.portrait | relative_url }}" alt="{{ profile.portrait_alt }}">
  </figure>
</section>

<section class="two-column">
  <div class="panel about-panel">
    <p class="section-label">About</p>
    {% for paragraph in profile.bio %}
      <p>{{ paragraph }}</p>
    {% endfor %}
  </div>

  <div class="news-panel-slot">
    <aside class="panel sidebar-panel news-panel">
      <div class="section-heading-row">
        <p class="section-label">Recent News</p>
        <a class="text-link" href="{{ '/news/' | relative_url }}">all news</a>
      </div>
      <div class="news-scroll">
        {% include news-list.html items=site.data.news limit=4 compact=true %}
      </div>
    </aside>
  </div>
</section>

{% include affiliations.html groups=site.data.affiliations %}

{% include fellowships.html items=site.data.fellowships %}

<section class="section-block">
  <div class="section-heading-row">
    <div>
      <h2>Selected Publications</h2>
    </div>
    <a class="text-link" href="{{ '/publications/' | relative_url }}">all publications</a>
  </div>
  <div class="pub-list compact-list">
    {% assign selected_pubs = site.data.publications | where: "selected", true | sort: "sort_date" | reverse %}
    {% for pub in selected_pubs %}
      {% include publication.html pub=pub compact=true %}
    {% endfor %}
  </div>
</section>
