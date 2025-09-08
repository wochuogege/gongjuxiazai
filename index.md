---
layout: default
title: 首页
---

# 欢迎访问我们的网站

这里是一个专注于提供Windows工具和安卓APP下载的平台，我们致力于为用户提供优质、安全、实用的软件资源。

## 快速导航

- [Windows工具](/windows-tools/) - 各种实用的Windows软件和工具
- [安卓APP](/android-apps/) - 精选的安卓应用程序
- [关于我们](/about-us/) - 了解我们的团队和使命
- [打赏作者](/donate/) - 支持我们继续提供优质内容

---

## 最新Windows工具

<div class="latest-tools">
  {% assign latest_windows_tools = site.windows_tools | sort: 'date' | reverse | limit: 3 %}
  {% if latest_windows_tools.size > 0 %}
    {% for tool in latest_windows_tools %}
    <div class="tool-item">
      <h3><a href="{{ site.baseurl }}{{ tool.url }}">{{ tool.title }}</a></h3>
      <div class="tool-meta">
        <span class="tool-date">发布日期：{{ tool.date | date: "%Y-%m-%d" }}</span>
        {% if tool.version %}<span class="tool-version">版本：{{ tool.version }}</span>{% endif %}
      </div>
      {% if tool.screenshot %}<div class="tool-screenshot"><img src="{{ site.baseurl }}/{{ tool.screenshot }}" alt="{{ tool.title }} 截图" loading="lazy"></div>{% endif %}
      <div class="tool-excerpt">{{ tool.excerpt | strip_html | truncate: 150 }}</div>
      <a href="{{ site.baseurl }}{{ tool.url }}" class="tool-more">查看详情</a>
    </div>
    {% endfor %}
  {% else %}
    <p>暂无Windows工具内容，敬请期待！</p>
  {% endif %}
  <div class="view-all"><a href="{{ site.baseurl }}/windows-tools/">查看全部Windows工具 &raquo;</a></div>
</div>

---

## 最新安卓APP

<div class="latest-apps">
  {% assign latest_android_apps = site.android_apps | sort: 'date' | reverse | limit: 3 %}
  {% if latest_android_apps.size > 0 %}
    {% for app in latest_android_apps %}
    <div class="app-item">
      <h3><a href="{{ site.baseurl }}{{ app.url }}">{{ app.title }}</a></h3>
      <div class="app-meta">
        <span class="app-date">发布日期：{{ app.date | date: "%Y-%m-%d" }}</span>
        {% if app.version %}<span class="app-version">版本：{{ app.version }}</span>{% endif %}
      </div>
      {% if app.icon %}<div class="app-icon"><img src="{{ site.baseurl }}/{{ app.icon }}" alt="{{ app.title }} 图标" loading="lazy"></div>{% endif %}
      <div class="app-excerpt">{{ app.excerpt | strip_html | truncate: 150 }}</div>
      <a href="{{ site.baseurl }}{{ app.url }}" class="app-more">查看详情</a>
    </div>
    {% endfor %}
  {% else %}
    <p>暂无安卓APP内容，敬请期待！</p>
  {% endif %}
  <div class="view-all"><a href="{{ site.baseurl }}/android-apps/">查看全部安卓APP &raquo;</a></div>
</div>

<style>
  .latest-tools, .latest-apps {
    margin-bottom: 30px;
  }
  
  .tool-item, .app-item {
    border: 1px solid #eaeaea;
    border-radius: 8px;
    padding: 20px;
    margin-bottom: 20px;
    background-color: #fff;
    transition: transform 0.3s ease, box-shadow 0.3s ease;
  }
  
  .tool-item:hover, .app-item:hover {
    transform: translateY(-5px);
    box-shadow: 0 5px 15px rgba(0,0,0,0.1);
  }
  
  .tool-item h3, .app-item h3 {
    margin-top: 0;
    margin-bottom: 10px;
    font-size: 1.5rem;
  }
  
  .tool-item h3 a, .app-item h3 a {
    color: #333;
    text-decoration: none;
  }
  
  .tool-item h3 a:hover, .app-item h3 a:hover {
    color: #007bff;
  }
  
  .tool-meta, .app-meta {
    display: flex;
    gap: 20px;
    margin-bottom: 15px;
    color: #666;
    font-size: 0.9rem;
  }
  
  .tool-screenshot, .app-icon {
    margin-bottom: 15px;
  }
  
  .tool-screenshot img {
    max-width: 100%;
    height: auto;
    border-radius: 4px;
  }
  
  .app-icon img {
    max-width: 80px;
    height: auto;
    border-radius: 16px;
  }
  
  .tool-excerpt, .app-excerpt {
    color: #555;
    margin-bottom: 15px;
    line-height: 1.6;
  }
  
  .tool-more, .app-more {
    display: inline-block;
    background-color: #007bff;
    color: white;
    padding: 8px 16px;
    border-radius: 4px;
    text-decoration: none;
    transition: background-color 0.3s ease;
  }
  
  .tool-more:hover, .app-more:hover {
    background-color: #0056b3;
  }
  
  .view-all {
    text-align: center;
    margin-top: 20px;
  }
  
  .view-all a {
    color: #007bff;
    text-decoration: none;
    font-weight: bold;
  }
  
  .view-all a:hover {
    text-decoration: underline;
  }
  
  @media (max-width: 768px) {
    .tool-meta, .app-meta {
      flex-direction: column;
      gap: 5px;
    }
    
    .tool-item, .app-item {
      padding: 15px;
    }
  }
</style>