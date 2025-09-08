---
layout: default
title: Windows工具
permalink: /windows-tools/
---

# Windows工具

这里提供各种实用的Windows工具和软件，帮助您提高工作效率和电脑使用体验。

## 所有工具

<div class="tool-grid">
  {% assign sorted_tools = site.windows_tools | sort: 'date' | reverse %}
  {% if sorted_tools.size > 0 %}
    {% for tool in sorted_tools %}
      <div class="tool-card">
        {% if tool.screenshot %}
          <div class="tool-image">
            <img src="{{ site.baseurl }}/{{ tool.screenshot }}" alt="{{ tool.title }}" loading="lazy">
          </div>
        {% else %}
          <div class="tool-image placeholder">
            <div class="placeholder-icon">🔧</div>
          </div>
        {% endif %}
        <div class="tool-info">
          <h3><a href="{{ tool.url }}">{{ tool.title }}</a></h3>
          <div class="tool-meta">
            <span class="tool-date">{{ tool.date | date: "%Y年%m月%d日" }}</span>
          </div>
          <div class="tool-excerpt">
            {{ tool.content | strip_html | truncate: 100 }}
          </div>
          <a href="{{ tool.url }}" class="read-more">查看详情 →</a>
        </div>
      </div>
    {% endfor %}
  {% else %}
    <p class="no-content">暂无工具内容，请在 _windows_tools 目录下添加工具介绍文章。</p>
  {% endif %}
</div>

<style>
  .tool-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
    gap: 20px;
    margin-top: 30px;
  }
  
  .tool-card {
    background-color: #ffffff;
    border: 1px solid #eaeaea;
    border-radius: 12px;
    overflow: hidden;
    transition: transform 0.3s ease, box-shadow 0.3s ease;
    display: flex;
    flex-direction: column;
    height: 100%;
  }
  
  .tool-card:hover {
    transform: translateY(-5px);
    box-shadow: 0 10px 20px rgba(0,0,0,0.1);
  }
  
  .tool-image {
    height: 180px;
    overflow: hidden;
    background-color: #f5f5f5;
  }
  
  .tool-image img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    transition: transform 0.3s ease;
  }
  
  .tool-card:hover .tool-image img {
    transform: scale(1.05);
  }
  
  .tool-image.placeholder {
    display: flex;
    align-items: center;
    justify-content: center;
  }
  
  .placeholder-icon {
    font-size: 48px;
  }
  
  .tool-info {
    padding: 15px;
    flex: 1;
    display: flex;
    flex-direction: column;
  }
  
  .tool-info h3 {
    margin-top: 0;
    margin-bottom: 10px;
    font-size: 1.2rem;
  }
  
  .tool-info h3 a {
    color: #333;
    text-decoration: none;
  }
  
  .tool-info h3 a:hover {
    color: #007bff;
  }
  
  .tool-meta {
    color: #666;
    font-size: 0.85em;
    margin-bottom: 10px;
  }
  
  .tool-excerpt {
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
    .tool-grid {
      grid-template-columns: 1fr;
      gap: 15px;
    }
    
    .tool-image {
      height: 160px;
    }
  }
</style>