---
layout: default
title: 网站首页
---

# 欢迎来到我的网站！

这是一个由 Jekyll 和 GitHub Actions 自动生成的网站，包含多个栏目和丰富的内容。

## 各栏目最新内容

{% for category in site.categories %}
  <section class="category-latest">
    <h2><a href="{{ site.baseurl }}/categories/{{ category | first | slugify }}/">{{ category | first }}</a></h2>
    
    <div class="post-list">
      {% assign sorted_posts = category[1] | sort: 'date' | reverse | slice: 0, 5 %}
      {% for post in sorted_posts %}
        <div class="post-item">
          <h3><a href="{{ post.url }}">{{ post.title }}</a></h3>
          <p class="post-date">{{ post.date | date: "%Y年%m月%d日" }}</p>
          <div class="post-excerpt">{{ post.excerpt | strip_html | truncate: 100 }}</div>
        </div>
      {% endfor %}
    </div>
    
    {% if category[1].size > 5 %}
      <div class="view-more">
        <a href="{{ site.baseurl }}/categories/{{ category | first | slugify }}/">查看更多 {{ category | first }} 文章 →</a>
      </div>
    {% endif %}
  </section>
{% endfor %}

{% if site.categories.size == 0 %}
  <p>暂无文章内容，请添加文章到 _posts 目录下。</p>
{% endif %}