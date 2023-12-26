---
layout: home
author_profile: true
---

# Welcome to My Website

Welcome to my website! Here you can find more information about me along with several projects that I have worked on. Check out the rest of the pages for more information.

## About Me

An enthusiastic and dedicated Platform Engineer specializing in cloud-native technologies and Kubernetes, committed to innovating and optimizing cloud infrastructures."

## Latest Posts

<ul>
  {% for post in site.posts limit:5 %}
    <li>
      <h2><a href="{{ post.url }}">{{ post.title }}</a></h2>
      <p>{{ post.excerpt | strip_html | truncatewords: 50 }}</p>
    </li>
  {% endfor %}
</ul>

[This section automatically lists your latest blog posts.]

---

Thank you for visiting my site!