---
layout: default
title: Takagi Works
permalink: /
---
<section class="hero">
  <div class="hero-content">
    <p class="eyebrow">Developer tools without bloat</p>
    <h1>Takagi Works</h1>
    <p class="lead">Takagi Works builds Ruby tooling for hardware, edge computing, and real IoT systems.</p>
    <div class="list-inline">
      <a class="button" href="/takagi.html">View Takagi</a>
      <a class="button hako" href="/hako.html">View Hako</a>
      <a class="button ghost" href="/blog/">View blog</a>
    </div>
  </div>
</section>

<section class="section-grid">
  <div class="card">
    <p class="eyebrow">Takagi</p>
    <h2>CoAP and IoT in Ruby </h2>
    <div class="logo-row">
      <div class="logo-mark takagi">
        <div class="logo-mark-line">[波]</div>
      </div>
      <p class="lead">CoAP framework that finally makes sense</p>
    </div>
    <p>Takagi brings Ruby ergonomics to CoAP. Build fast, modular IoT services on edge devices and gateways. Clean API, lightweight design, real IoT performance.</p>
    <a class="button ghost" href="/takagi.html">Dive into Takagi</a>
  </div>
  <div class="card">
    <p class="eyebrow">Hako</p>
    <h2>Ruby runtime for Zephyr RTOS</h2>
    <div class="logo-row">
      <div class="logo-mark hako">
        <div class="logo-mark-line">[箱]</div>
      </div>
      <p class="lead">Ruby runtime for Zephyr powered by mruby/c, with optional PicoRuby compiler.</p>
    </div>
    <p>Run Ruby on microcontrollers: choose VM-only builds for small footprints or enable compiler and shell for interactive development.</p>
    <a class="button ghost" href="/hako.html">Dive into Hako</a>
  </div>
</section>

<section class="content-block">
  <h2>Latest notes</h2>
  {% assign recent_posts = site.posts | slice: 0, 3 %}
  {% if recent_posts.size == 0 %}
    <p>No posts yet. Check back soon.</p>
  {% else %}
    <div class="blog-list">
      {% for post in recent_posts %}
        <article class="blog-card">
          <p class="eyebrow">{{ post.date | date: '%b %d, %Y' }}</p>
          <h3><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h3>
          <p>{{ post.excerpt | strip_html | truncate: 140 }}</p>
        </article>
      {% endfor %}
    </div>
  {% endif %}
</section>
