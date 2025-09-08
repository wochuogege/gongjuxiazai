---
layout: default
title: 安卓APP
permalink: /android-apps/
---

# 安卓APP

这里提供各种实用的安卓应用程序，满足您在移动设备上的各种需求。

## 所有应用

<div class="app-list">
  {% assign sorted_apps = site.android_apps | sort: 'date' | reverse %}
  {% if sorted_apps.size > 0 %}
    {% for app in sorted_apps %}
      <div class="app-item">
        <h3><a href="{{ app.url }}">{{ app.title }}</a></h3>
        <div class="app-meta">
          <span class="app-date">{{ app.date | date: "%Y年%m月%d日" }}</span>
          {% if app.version %}
            <span class="app-version">版本：{{ app.version }}</span>
          {% endif %}
        </div>
        <div class="app-excerpt">
          {{ app.content | strip_html | truncate: 150 }}
        </div>
        <a href="{{ app.url }}" class="read-more">查看详情 →</a>
      </div>
    {% endfor %}
  {% else %}
    <p class="no-content">暂无应用内容，请在 _android_apps 目录下添加应用介绍文章。</p>
  {% endif %}
</div>

<style>
  .app-list {
    margin-top: 30px;
  }
  
  .app-item {
    background-color: #f9f9f9;
    border-radius: 8px;
    padding: 20px;
    margin-bottom: 20px;
    transition: transform 0.3s ease, box-shadow 0.3s ease;
  }
  
  .app-item:hover {
    transform: translateY(-3px);
    box-shadow: 0 5px 15px rgba(0,0,0,0.1);
  }
  
  .app-item h3 {
    margin-top: 0;
  }
  
  .app-meta {
    color: #666;
    font-size: 0.9em;
    margin-bottom: 10px;
    display: flex;
    gap: 20px;
  }
  
  .app-excerpt {
    margin-bottom: 15px;
  }
  
  .read-more {
    color: #0366d6;
    text-decoration: none;
    font-weight: 500;
  }
  
  .read-more:hover {
    text-decoration: underline;
  }
  
  .no-content {
    text-align: center;
    padding: 40px;
    color: #666;
  }
</style>