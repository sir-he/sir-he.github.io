---
layout: page
title: Article
permalink: /article/
---

Reprinted please indicate the source by:<a href="https://sir-he.github.io">sir-he blog</a>

| Fecha					| Article					|
|---------------------------------------|-----------------------------------------------| {% for post in site.posts %}
| {{ post.date | date: "%-d %b %Y" }}	| <a href="{{ post.url }}">{{ post.title }}</a> | {% endfor %}
