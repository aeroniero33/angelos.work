---
layout: home
author_profile: true
---

# Welcome
My name is Angelos Perivolaropoulos and I am a Platform Engineer based in London, UK. I am passionate in cloud-native technologies and Kubernetes.

## Latest Tutorials
<ul>
  {% for tutorial in site.tutorials limit:5 %}
    <li>
      <h3><a href="{{ tutorial.url }}">{{ tutorial.title }}</a></h3>
      <p>{{ post.excerpt | strip_html | truncatewords: 50 }}</p>
    </li>
  {% endfor %}
</ul>

---

Thank you for visiting my site!
