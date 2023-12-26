---
layout: home
author_profile: true
---

# Welcome
Welcome to my website! Here you can find tutorials I made and more information about me along with several projects that I have worked on.

## About Me
An enthusiastic and dedicated Platform Engineer specializing in cloud-native technologies and Kubernetes, committed to innovating and optimizing cloud infrastructures.

## Latest Tutorials
<ul>
  {% for tutorial in site.tutorials limit:5 %}
    <li>
      <h2><a href="{{ tutorial.url }}">{{ tutorial.title }}</a></h2>
      <p>{{ post.excerpt | strip_html | truncatewords: 50 }}</p>
    </li>
  {% endfor %}
</ul>

---

Thank you for visiting my site!