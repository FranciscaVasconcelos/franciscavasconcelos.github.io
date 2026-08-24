---
layout: default
title: Beyond academia
permalink: /beyond/
published: false
---

<header class="page-header">
  <p class="eyebrow">Outside research</p>
  <h1>Beyond academia</h1>
  <p>{{ site.data.personal.intro }}</p>
</header>

<section class="personal-grid">
  {% for item in site.data.personal.sections %}
    <article class="personal-card">
      <img src="{{ item.image | relative_url }}" alt="{{ item.alt }}" loading="lazy">
      <div>
        <h2>{{ item.title }}</h2>
        <p>{{ item.blurb }}</p>
        {% if item.tags %}
          <div class="tag-row">
            {% for tag in item.tags %}<span>{{ tag }}</span>{% endfor %}
          </div>
        {% endif %}
      </div>
    </article>
  {% endfor %}
</section>

<section class="panel page-panel replace-note">
  <p class="section-label">How to add photos</p>
  <p>Drop images into <code>assets/img/personal/</code>, then edit <code>_data/personal.yml</code>. Each section has an <code>image</code>, <code>alt</code>, <code>blurb</code>, and optional tags. This keeps the page easy to update without touching HTML.</p>
</section>
