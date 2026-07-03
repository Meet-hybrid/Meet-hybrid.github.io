---
layout: default
title: "Blog — Michael Philip"
description: "Writing by Michael Philip on software engineering, cybersecurity, psychology, entrepreneurship, and being human."
permalink: /blog/
---

<section class="page-header">
  <div class="container">
    <p class="section-label">Blog</p>
    <h1 class="section-title" style="font-size:clamp(2rem,4vw,3.25rem);">Writing</h1>
    <p class="section-subtitle">Notes on engineering, security, product, psychology, and life. Published when something is worth saying.</p>
  </div>
</section>

<section class="section">
  <div class="container">

    <!-- Search -->
    <div style="margin-bottom:32px;max-width:400px;">
      <input type="text" class="form-control" id="blogSearch" placeholder="Search posts..." />
    </div>

    <!-- Category filter -->
    <div class="filter-tabs" id="categoryFilter">
      <button class="filter-tab active" data-cat="all">All</button>
      <button class="filter-tab" data-cat="engineering">Engineering</button>
      <button class="filter-tab" data-cat="cybersecurity">Cybersecurity</button>
      <button class="filter-tab" data-cat="product">Product</button>
      <button class="filter-tab" data-cat="psychology">Psychology</button>
      <button class="filter-tab" data-cat="entrepreneurship">Entrepreneurship</button>
      <button class="filter-tab" data-cat="personal">Personal Growth</button>
    </div>

    {% assign categories_order = "Engineering,Cybersecurity,Product,Psychology,Entrepreneurship,Personal Growth" | split: "," %}
    {% if site.posts.size > 0 %}
    <div class="posts-grid" id="postsGrid">
      {% for category in categories_order %}
        {% assign cat_posts = site.posts | where_exp: "post", "post.categories contains category" %}
        {% for post in cat_posts %}
        <article class="post-card" data-category="{{ post.categories | join: ' ' | downcase }}">
          <div class="post-card__category">{{ post.categories | first | default: "General" }}</div>
          <a href="{{ post.url | relative_url }}" style="color:inherit;">
            <h2 class="post-card__title">{{ post.title }}</h2>
          </a>
          <p class="post-card__excerpt">{{ post.excerpt | strip_html | truncate: 120 }}</p>
          <div class="post-card__meta">
            <span>{{ post.date | date: "%b %d, %Y" }}</span>
            {% if post.read_time %}<span>{{ post.read_time }} min read</span>{% endif %}
          </div>
        </article>
        {% endfor %}
      {% endfor %}
    </div>
    {% else %}
    <!-- Placeholder posts when no posts yet -->
    <div class="posts-grid">
      <div class="post-card">
        <div class="post-card__category">Engineering</div>
        <div class="post-card__title">What six months of professional code review taught me about writing software</div>
        <p class="post-card__excerpt">The difference between code that works and code that communicates — and why that gap matters more than I expected.</p>
        <div class="post-card__meta"><span>Coming soon</span><span>6 min read</span></div>
      </div>
      <div class="post-card">
        <div class="post-card__category">Cybersecurity</div>
        <div class="post-card__title">Why every software engineer should understand the OWASP Top 10</div>
        <p class="post-card__excerpt">You built the API. Now learn how someone would try to break it — and what you can do before they get the chance.</p>
        <div class="post-card__meta"><span>Coming soon</span><span>8 min read</span></div>
      </div>
      <div class="post-card">
        <div class="post-card__category">Product</div>
        <div class="post-card__title">The user on the other side of the interface</div>
        <p class="post-card__excerpt">Product thinking isn't a role — it's a lens. Here's how thinking about real people changes how you write code.</p>
        <div class="post-card__meta"><span>Coming soon</span><span>5 min read</span></div>
      </div>
      <div class="post-card">
        <div class="post-card__category">Psychology</div>
        <div class="post-card__title">What behavioral psychology explains about why software gets adopted (or doesn't)</div>
        <p class="post-card__excerpt">Habits, friction, defaults, and the invisible forces that determine whether your product becomes part of someone's life.</p>
        <div class="post-card__meta"><span>Coming soon</span><span>7 min read</span></div>
      </div>
      <div class="post-card">
        <div class="post-card__category">Entrepreneurship</div>
        <div class="post-card__title">From business school to engineering — what I kept and what I left behind</div>
        <p class="post-card__excerpt">Studying business gave me a way of seeing the world that I carry into every codebase I touch. Here's what transferred.</p>
        <div class="post-card__meta"><span>Coming soon</span><span>6 min read</span></div>
      </div>
      <div class="post-card">
        <div class="post-card__category">Personal Growth</div>
        <div class="post-card__title">On learning in public as a developer in Nigeria</div>
        <p class="post-card__excerpt">Visibility costs something. But the alternative — building in silence, growing alone — costs more.</p>
        <div class="post-card__meta"><span>Coming soon</span><span>4 min read</span></div>
      </div>
    </div>
    {% endif %}

    <!-- Newsletter CTA -->
    <div class="newsletter-strip" style="margin-top:64px;">
      <p class="section-label" style="text-align:center;">Stay Updated</p>
      <h2 class="section-title" style="text-align:center;font-size:1.5rem;">Get New Posts in Your Inbox</h2>
      <p style="color:var(--grey-2);text-align:center;max-width:400px;margin:0 auto 20px;">Engineering notes, security learnings, product thinking, and the occasional life observation.</p>
      <form class="newsletter-form" onsubmit="return false;">
        <input type="email" class="form-control" placeholder="you@example.com" />
        <button type="submit" class="btn btn--primary">Subscribe</button>
      </form>
    </div>

  </div>
</section>
