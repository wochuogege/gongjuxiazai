---
layout: default
title: 搜索结果
permalink: /search/
---

# 搜索结果

<div class="search-container">
  <div class="search-form-wrapper">
    <form action="{{ site.baseurl }}/search/" method="get" id="search-form">
      <input type="text" id="search-input" placeholder="搜索工具或应用..." value="{{ page.search_term }}" autocomplete="off">
      <button type="submit" id="search-button">
        <svg width="16" height="16" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
          <path d="M11 19C15.4183 19 19 15.4183 19 11C19 6.58172 15.4183 3 11 3C6.58172 3 3 6.58172 3 11C3 15.4183 6.58172 19 11 19Z" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
          <path d="M21 21L16.65 16.65" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
        </svg>
      </button>
    </form>
  </div>
  
  <div id="search-results" class="search-results">
    <p class="search-instructions">请在上方搜索框输入关键词进行搜索</p>
  </div>
</div>

<script>
  // 搜索功能实现
  document.addEventListener('DOMContentLoaded', function() {
    const searchForm = document.getElementById('search-form');
    const searchInput = document.getElementById('search-input');
    const searchResults = document.getElementById('search-results');
    
    // 搜索索引数据 - 优化版本，确保能正确索引所有内容
    const searchIndex = [
      {% for tool in site.windows_tools %}
        {
          title: '{{ tool.title }}',
          url: '{{ site.baseurl }}{{ tool.url }}',
          content: '{{ tool.content | strip_html | strip_newlines | escape }}',
          rawContent: '{{ tool.content | escape }}',
          type: 'Windows工具',
          date: '{{ tool.date | date: "%Y年%m月%d日" }}',
          excerpt: '{{ tool.content | strip_html | truncate: 150 | escape }}'
        },
      {% endfor %}
      {% for app in site.android_apps %}
        {
          title: '{{ app.title }}',
          url: '{{ site.baseurl }}{{ app.url }}',
          content: '{{ app.content | strip_html | strip_newlines | escape }}',
          rawContent: '{{ app.content | escape }}',
          type: '安卓APP',
          date: '{{ app.date | date: "%Y年%m月%d日" }}',
          excerpt: '{{ app.content | strip_html | truncate: 150 | escape }}'
        }
        {% unless forloop.last %},{% endunless %}
      {% endfor %}
    ];
    
    // 获取URL中的搜索参数
    function getSearchParams() {
      const params = new URLSearchParams(window.location.search);
      return params.get('q') || '';
    }
    
    // 执行搜索 - 增强版，确保能匹配更多内容
    function performSearch(query) {
      if (!query.trim()) {
        searchResults.innerHTML = '<p class="search-instructions">请在上方搜索框输入关键词进行搜索</p>';
        return;
      }
      
      query = query.toLowerCase();
      // 增强的搜索逻辑，确保能匹配标题、内容、原始内容和摘要中的关键词
      const results = searchIndex.filter(item => {
        // 检查标题
        const titleMatch = item.title.toLowerCase().includes(query);
        
        // 检查处理过的内容
        const contentMatch = item.content.toLowerCase().includes(query);
        
        // 检查原始内容（未经过多处理）
        const rawContentMatch = item.rawContent.toLowerCase().includes(query);
        
        // 检查摘要
        const excerptMatch = item.excerpt.toLowerCase().includes(query);
        
        // 任何一项匹配就返回结果
        return titleMatch || contentMatch || rawContentMatch || excerptMatch;
      });
      
      if (results.length === 0) {
        searchResults.innerHTML = '<p class="no-results">未找到匹配的结果，请尝试其他关键词。</p>';
      } else {
        let html = `<p class="results-count">找到 ${results.length} 条结果</p><div class="results-list">`;
        results.forEach(item => {
          html += `
            <div class="search-result-item">
              <div class="result-meta">
                <span class="result-type">${item.type}</span>
                <span class="result-date">${item.date}</span>
              </div>
              <h3><a href="${item.url}">${item.title}</a></h3>
              <p class="result-excerpt">${item.excerpt}</p>
            </div>
          `;
        });
        html += '</div>';
        searchResults.innerHTML = html;
      }
    }
    
    // 初始加载时执行搜索
    const initialQuery = getSearchParams();
    if (initialQuery) {
      searchInput.value = initialQuery;
      performSearch(initialQuery);
    }
    
    // 表单提交时执行搜索
    searchForm.addEventListener('submit', function(e) {
      e.preventDefault();
      const query = searchInput.value.trim();
      if (query) {
        // 更新URL但不刷新页面
        const url = new URL(window.location);
        url.searchParams.set('q', query);
        window.history.pushState({}, '', url);
        performSearch(query);
      }
    });
    
    // 监听URL变化（用于浏览器前进/后退按钮）
    window.addEventListener('popstate', function() {
      const query = getSearchParams();
      searchInput.value = query;
      performSearch(query);
    });
  });
</script>

<style>
  .search-container {
    max-width: 800px;
    margin: 0 auto;
    padding: 20px;
  }
  
  .search-form-wrapper {
    margin-bottom: 30px;
    text-align: center;
  }
  
  #search-form {
    display: flex;
    align-items: center;
    max-width: 500px;
    margin: 0 auto;
    position: relative;
  }
  
  #search-input {
    width: 100%;
    padding: 12px 40px 12px 20px;
    border: 2px solid #ddd;
    border-radius: 25px;
    font-size: 16px;
    outline: none;
    transition: border-color 0.3s ease;
  }
  
  #search-input:focus {
    border-color: #007bff;
  }
  
  #search-button {
    position: absolute;
    right: 10px;
    background: none;
    border: none;
    cursor: pointer;
    color: #666;
    padding: 5px;
    font-size: 18px;
  }
  
  #search-button:hover {
    color: #007bff;
  }
  
  .search-instructions,
  .no-results {
    text-align: center;
    color: #666;
    font-size: 16px;
    padding: 40px 0;
  }
  
  .results-count {
    font-size: 14px;
    color: #666;
    margin-bottom: 20px;
  }
  
  .results-list {
    display: flex;
    flex-direction: column;
    gap: 15px;
  }
  
  .search-result-item {
    background-color: #fff;
    border: 1px solid #eaeaea;
    border-radius: 8px;
    padding: 20px;
    transition: box-shadow 0.3s ease;
  }
  
  .search-result-item:hover {
    box-shadow: 0 4px 12px rgba(0,0,0,0.1);
  }
  
  .result-meta {
    display: flex;
    gap: 15px;
    margin-bottom: 10px;
    font-size: 12px;
  }
  
  .result-type {
    background-color: #007bff;
    color: white;
    padding: 2px 8px;
    border-radius: 4px;
  }
  
  .result-date {
    color: #999;
  }
  
  .search-result-item h3 {
    margin: 10px 0;
    font-size: 18px;
  }
  
  .search-result-item h3 a {
    color: #333;
    text-decoration: none;
    transition: color 0.3s ease;
  }
  
  .search-result-item h3 a:hover {
    color: #007bff;
  }
  
  .result-excerpt {
    color: #666;
    line-height: 1.6;
    margin: 10px 0 0;
    font-size: 14px;
  }
  
  @media (max-width: 768px) {
    .search-container {
      padding: 15px;
    }
    
    #search-form {
      max-width: 100%;
    }
    
    .search-result-item {
      padding: 15px;
    }
  }
</style>