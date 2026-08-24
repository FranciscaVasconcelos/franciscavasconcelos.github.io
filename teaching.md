---
layout: default
title: Teaching
permalink: /teaching/
published: false
---

<header class="page-header">
  <p class="eyebrow">Teaching + outreach</p>
  <h1>Teaching</h1>
  <p>{{ site.data.teaching.intro }}</p>
</header>

<section class="section-block">
  <p class="section-label">Courses</p>
  <div class="card-grid single-column">
    {% for course in site.data.teaching.courses %}
      <article class="info-card">
        <div class="card-topline">
          <h2>{{ course.role }}</h2>
          <span>{{ course.dates }}</span>
        </div>
        <p class="muted">{{ course.institution }}</p>
        <ul>
          {% for bullet in course.bullets %}
            <li>{{ bullet }}</li>
          {% endfor %}
        </ul>
      </article>
    {% endfor %}
  </div>
</section>

<section class="section-block">
  <p class="section-label">Outreach + mentoring</p>
  <div class="card-grid">
    {% for item in site.data.teaching.outreach %}
      <article class="info-card">
        <div class="card-topline">
          <h2>{{ item.role }}</h2>
          <span>{{ item.dates }}</span>
        </div>
        <p class="muted">{{ item.institution }}</p>
        <ul>
          {% for bullet in item.bullets %}
            <li>{{ bullet }}</li>
          {% endfor %}
        </ul>
      </article>
    {% endfor %}
  </div>
</section>

<section class="section-block">
  <p class="section-label">Selected outreach talks</p>
  <div class="talk-list">
    {% for talk in site.data.teaching.talks %}
      <article class="talk-item">
        <span>{{ talk.year }}</span>
        <div>
          <h2>{{ talk.title }}</h2>
          <p>{{ talk.description }}</p>
        </div>
      </article>
    {% endfor %}
  </div>
</section>
