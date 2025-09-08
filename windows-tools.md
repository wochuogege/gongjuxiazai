---
layout: default
title: Windows工具
permalink: /windows-tools/
---

# Windows工具

这里提供各种实用的Windows工具和软件，帮助您提高工作效率和电脑使用体验。

## 所有工具

<div class="tool-list">
  {% assign sorted_tools = site.windows_tools | sort: 'date' | reverse %}
  {% if sorted_tools.size > 0 %}
    {% for tool in sorted_tools %}
      <div class="tool-item">
        <h3><a href="{{ tool.url }}">{{ tool.title }}</a></h3>
        <div class="tool-meta">
          <span class="tool-date">{{ tool.date | date: "%Y年%m月%d日" }}</span>
        </div>
        <div class="tool-excerpt">
          {{ tool.content | strip_html | truncate: 150 }}
        </div>
        <a href="{{ tool.url }}" class="read-more">查看详情 →</a>
      </div>
    {% endfor %}
  {% else %}
    <p class="no-content">暂无工具内容，请在 _windows_tools 目录下添加工具介绍文章。</p>
  {% endif %}
</div>

<style>
  .tool-list {
    margin-top: 30px;
  }
  
  .tool-item {
    background-color: #f9f9f9;
    border-radius: 8px;
    padding: 20px;
    margin-bottom: 20px;
    transition: transform 0.3s ease, box-shadow 0.3s ease;
  }
  
  .tool-item:hover {
    transform: translateY(-3px);
    box-shadow: 0 5px 15px rgba(0,0,0,0.1);
  }
  
  .tool-item h3 {
    margin-top: 0;
  }
  
  .tool-meta {
    color: #666;
    font-size: 0.9em;
    margin-bottom: 10px;
  }
  
  .tool-excerpt {
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