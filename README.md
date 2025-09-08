# 老铁软件下载平台

一个专注于提供Windows工具和安卓APP下载的静态网站，使用Jekyll构建，支持GitHub Pages自动部署。

## 网站结构

- **首页**：网站的主要入口，提供快速导航
- **Windows工具**：展示各种Windows软件和工具
- **安卓APP**：展示各种安卓应用程序
- **关于我们**：介绍网站的使命和团队信息
- **打赏作者**：支持网站运营的方式

## 如何添加新内容

### 添加Windows工具

1. 在`_windows_tools`目录下创建一个新的Markdown文件（扩展名为.md）
2. 文件开头添加以下YAML前置元数据：
   ```yaml
   ---
   layout: windows_tool
   title: 工具名称
   permalink: /windows-tools/工具-slug/
   date: 发布日期（格式：YYYY-MM-DD）
   author: 作者名称
   screenshot: /assets/images/工具截图.png
   system_requirements: 系统要求
   download_link: 下载链接
   features:
     - 功能1
     - 功能2
     - 功能3
   ---
   ```
3. 在前置元数据后添加工具的详细介绍内容

### 添加安卓APP

1. 在`_android_apps`目录下创建一个新的Markdown文件（扩展名为.md）
2. 文件开头添加以下YAML前置元数据：
   ```yaml
   ---
   layout: android_app
   title: 应用名称
   permalink: /android-apps/应用-slug/
   date: 发布日期（格式：YYYY-MM-DD）
   author: 作者名称
   icon: /assets/images/应用图标.png
   version: 应用版本
   size: 应用大小
   developer: 开发者名称
   screenshots:
     - /assets/images/应用截图1.png
     - /assets/images/应用截图2.png
   system_requirements: 系统要求
   download_link: 下载链接
   features:
     - 功能1
     - 功能2
     - 功能3
   ---
   ```
3. 在前置元数据后添加应用的详细介绍内容

## 图片资源

- 所有图片资源请放在`assets/images`目录下
- 建议使用PNG或JPG格式的图片
- 图标建议尺寸：1024x1024像素
- 截图建议尺寸：根据实际情况调整，保持清晰

## 部署方式

1. 将代码推送到GitHub仓库
2. 在GitHub仓库的设置中启用GitHub Pages
3. 选择合适的分支（通常是main或master）作为发布源
4. 等待GitHub Actions自动构建和部署

## 本地开发（可选）

如果需要在本地预览网站效果，可以安装Jekyll并运行本地服务器：

```bash
# 安装Jekyll（需要先安装Ruby）
gem install bundler jekyll

# 安装依赖
bundle install

# 启动本地服务器
bundle exec jekyll serve
```

然后在浏览器中访问 http://localhost:4000 查看网站。