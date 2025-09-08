---
layout: default
title: 安卓APP
permalink: /android-apps/
---

# 安卓APP

这里提供各种实用的安卓应用程序，满足您在移动设备上的各种需求。

## 所有应用

<div class="app-grid">
  {% assign sorted_apps = site.android_apps | sort: 'date' | reverse %}
  {% if sorted_apps.size > 0 %}
    {% for app in sorted_apps %}
      <div class="app-card">
        {% if app.icon %}
          <div class="app-image">
            <img src="{{ app.icon }}" alt="{{ app.title }}" loading="lazy">
          </div>
        {% else %}
          <div class="app-image placeholder">
            <div class="placeholder-icon">📱</div>
          </div>
        {% endif %}
        <div class="app-info">
          <h3><a href="{{ app.url }}">{{ app.title }}</a></h3>
          <div class="app-meta">
            <span class="app-date">{{ app.date | date: "%Y年%m月%d日" }}</span>
            {% if app.version %}
              <span class="app-version">版本：{{ app.version }}</span>
            {% endif %}
          </div>
          <div class="app-excerpt">
            {{ app.content | strip_html | truncate: 100 }}
          </div>
          <a href="{{ app.url }}" class="read-more">查看详情 →</a>
        </div>
      </div>
    {% endfor %}
  {% else %}
    <p class="no-content">暂无应用内容，请在 _android_apps 目录下添加应用介绍文章。</p>
  {% endif %}
</div>

<style>
  .app-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
    gap: 20px;
    margin-top: 30px;
  }
  
  .app-card {
    background-color: #ffffff;
    border: 1px solid #eaeaea;
    border-radius: 12px;
    overflow: hidden;
    transition: transform 0.3s ease, box-shadow 0.3s ease;
    display: flex;
    flex-direction: column;
    height: 100%;
  }
  
  .app-card:hover {
    transform: translateY(-5px);
    box-shadow: 0 10px 20px rgba(0,0,0,0.1);
  }
  
  .app-image {
    height: 180px;
    overflow: hidden;
    background-color: #f5f5f5;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  
  .app-image img {
    width: 120px;
    height: 120px;
    object-fit: contain;
    transition: transform 0.3s ease;
  }
  
  .app-card:hover .app-image img {
    transform: scale(1.1);
  }
  
  .app-image.placeholder {
    display: flex;
    align-items: center;
    justify-content: center;
  }
  
  .placeholder-icon {
    font-size: 64px;
  }
  
  .app-info {
    padding: 15px;
    flex: 1;
    display: flex;
    flex-direction: column;
  }
  
  .app-info h3 {
    margin-top: 0;
    margin-bottom: 10px;
    font-size: 1.2rem;
  }
  
  .app-info h3 a {
    color: #333;
    text-decoration: none;
  }
  
  .app-info h3 a:hover {
    color: #007bff;
  }
  
  .app-meta {
    color: #666;
    font-size: 0.85em;
    margin-bottom: 10px;
    display: flex;
    gap: 15px;
    flex-wrap: wrap;
  }
  
  .app-excerpt {
    color: #555;
    margin-bottom: 15px;
    flex: 1;
    font-size: 0.95em;
    line-height: 1.5;
  }
  
  .read-more {
    color: #007bff;
    text-decoration: none;
    font-weight: 500;
    font-size: 0.9em;
  }
  
  .read-more:hover {
    text-decoration: underline;
  }
  
  .no-content {
    grid-column: 1 / -1;
    text-align: center;
    padding: 60px 20px;
    color: #666;
    background-color: #f9f9f9;
    border-radius: 12px;
  }
  
  @media (max-width: 768px) {
    .app-grid {
      grid-template-columns: 1fr;
      gap: 15px;
    }
    
    .app-image {
      height: 160px;
    }
    
    .app-image img {
      width: 100px;
      height: 100px;
    }
  }
</style>