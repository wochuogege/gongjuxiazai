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

## 最新内容

<div class="latest-content-container">
  <div class="content-section windows-section">
    <h2>最新Windows工具</h2>
    <div class="content-grid">
      {% assign latest_windows_tools = site.windows_tools | sort: 'date' | reverse | limit: 3 %}
      {% if latest_windows_tools.size > 0 %}
        {% for tool in latest_windows_tools %}
          <div class="content-card">
            {% if tool.screenshot %}
              <div class="content-image">
              <img src="{{ tool.screenshot }}" alt="{{ tool.title }} 截图" loading="lazy">
            </div>
            {% else %}
              <div class="content-image placeholder">
                <div class="placeholder-icon">🖥️</div>
              </div>
            {% endif %}
            <div class="content-info">
              <h3><a href="{{ site.baseurl }}{{ tool.url }}">{{ tool.title }}</a></h3>
              <div class="content-meta">
                <span class="content-date">{{ tool.date | date: "%Y年%m月%d日" }}</span>
                {% if tool.version %}<span class="content-version">版本：{{ tool.version }}</span>{% endif %}
              </div>
              <div class="content-excerpt">
                {{ tool.excerpt | strip_html | truncate: 80 }}
              </div>
              <a href="{{ site.baseurl }}{{ tool.url }}" class="content-more">查看详情 →</a>
            </div>
          </div>
        {% endfor %}
      {% else %}
        <p class="no-content">暂无Windows工具内容，敬请期待！</p>
      {% endif %}
    </div>
    <div class="view-all"><a href="{{ site.baseurl }}/windows-tools/">查看全部Windows工具 &raquo;</a></div>
  </div>

  <div class="content-section android-section">
    <h2>最新安卓APP</h2>
    <div class="content-grid">
      {% assign latest_android_apps = site.android_apps | sort: 'date' | reverse | limit: 3 %}
      {% if latest_android_apps.size > 0 %}
        {% for app in latest_android_apps %}
          <div class="content-card">
            {% if app.icon %}
              <div class="content-image">
              <img src="{{ app.icon }}" alt="{{ app.title }} 图标" loading="lazy">
            </div>
            {% else %}
              <div class="content-image placeholder">
                <div class="placeholder-icon">📱</div>
              </div>
            {% endif %}
            <div class="content-info">
              <h3><a href="{{ site.baseurl }}{{ app.url }}">{{ app.title }}</a></h3>
              <div class="content-meta">
                <span class="content-date">{{ app.date | date: "%Y年%m月%d日" }}</span>
                {% if app.version %}<span class="content-version">版本：{{ app.version }}</span>{% endif %}
              </div>
              <div class="content-excerpt">
                {{ app.excerpt | strip_html | truncate: 80 }}
              </div>
              <a href="{{ site.baseurl }}{{ app.url }}" class="content-more">查看详情 →</a>
            </div>
          </div>
        {% endfor %}
      {% else %}
        <p class="no-content">暂无安卓APP内容，敬请期待！</p>
      {% endif %}
    </div>
    <div class="view-all"><a href="{{ site.baseurl }}/android-apps/">查看全部安卓APP &raquo;</a></div>
  </div>
</div>

<style>
  .latest-content-container {
    display: flex;
    gap: 30px;
    margin-bottom: 40px;
    flex-wrap: wrap;
  }
  
  .content-section {
    flex: 1;
    min-width: 300px;
  }
  
  .content-section h2 {
    font-size: 1.8rem;
    margin-top: 0;
    margin-bottom: 20px;
    padding-bottom: 10px;
    border-bottom: 2px solid #007bff;
  }
  
  .content-grid {
    display: grid;
    grid-template-columns: 1fr;
    gap: 15px;
  }
  
  .content-card {
    background-color: #ffffff;
    border: 1px solid #eaeaea;
    border-radius: 12px;
    overflow: hidden;
    transition: transform 0.3s ease, box-shadow 0.3s ease;
    display: flex;
    flex-direction: column;
  }
  
  .content-card:hover {
    transform: translateY(-5px);
    box-shadow: 0 10px 20px rgba(0,0,0,0.1);
  }
  
  .content-image {
    height: 160px;
    overflow: hidden;
    background-color: #f5f5f5;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  
  .content-image img {
    max-width: 100%;
    max-height: 100%;
    object-fit: contain;
    transition: transform 0.3s ease;
  }
  
  .content-card:hover .content-image img {
    transform: scale(1.05);
  }
  
  .content-image.placeholder {
    display: flex;
    align-items: center;
    justify-content: center;
  }
  
  .placeholder-icon {
    font-size: 56px;
  }
  
  .content-info {
    padding: 15px;
    flex: 1;
    display: flex;
    flex-direction: column;
  }
  
  .content-info h3 {
    margin-top: 0;
    margin-bottom: 10px;
    font-size: 1.2rem;
  }
  
  .content-info h3 a {
    color: #333;
    text-decoration: none;
  }
  
  .content-info h3 a:hover {
    color: #007bff;
  }
  
  .content-meta {
    color: #666;
    font-size: 0.85em;
    margin-bottom: 10px;
    display: flex;
    gap: 15px;
    flex-wrap: wrap;
  }
  
  .content-excerpt {
    color: #555;
    margin-bottom: 15px;
    flex: 1;
    font-size: 0.95em;
    line-height: 1.5;
  }
  
  .content-more {
    color: #007bff;
    text-decoration: none;
    font-weight: 500;
    font-size: 0.9em;
  }
  
  .content-more:hover {
    text-decoration: underline;
  }
  
  .view-all {
    text-align: center;
    margin-top: 20px;
    padding-top: 15px;
    border-top: 1px solid #eaeaea;
  }
  
  .view-all a {
    color: #007bff;
    text-decoration: none;
    font-weight: bold;
  }
  
  .view-all a:hover {
    text-decoration: underline;
  }
  
  .no-content {
    text-align: center;
    padding: 40px 20px;
    color: #666;
    background-color: #f9f9f9;
    border-radius: 12px;
  }
  
  @media (max-width: 768px) {
    .latest-content-container {
      flex-direction: column;
      gap: 20px;
    }
    
    .content-section {
      min-width: auto;
    }
    
    .content-image {
      height: 140px;
    }
    
    .content-info {
      padding: 12px;
    }
  }
</style>