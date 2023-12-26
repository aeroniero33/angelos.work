---
layout: home
author_profile: true
---

# Welcome to My Website

Hello! I'm Angelos Perivolaropoulos, and this is my personal website. Here, you'll find my blog posts, projects, and more about my professional and personal interests.

## About Me

[Briefly introduce yourself. Mention your professional background, interests, or any other information you'd like to share.]

## Featured Posts

Here are some of my featured blog posts:

- [Post Title 1](link-to-post-1)
- [Post Title 2](link-to-post-2)
- [Post Title 3](link-to-post-3)

[You can replace this section with any other content you'd like to highlight on your homepage.]

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

## Contact

Feel free to [contact me](contact-page-link) for collaborations, questions, or just to say hi!

---

Thank you for visiting my site!