# 我的 Markdown 网站

这是一个使用 Jekyll 和 GitHub Pages 搭建的个人网站。

## 网站功能

- **栏目分类**：可以根据不同的主题将文章分类到不同的栏目中
- **标签系统**：为文章添加标签，方便内容检索
- **首页展示**：首页自动展示各个栏目的最新内容
- **响应式设计**：适配不同屏幕尺寸的设备

## 如何添加新文章

1. 在 `_posts` 目录下创建一个新的 Markdown 文件
2. 文件名格式必须为 `YYYY-MM-DD-文章标题.md`
3. 在文件顶部添加 Front Matter，例如：
   
   ```yaml
   ---
   layout: post
   title: "文章标题"
   date: 2023-10-27 10:00:00 +0800
   categories:
   - 栏目名称
   tags:
   - 标签1
   - 标签2
   ---
   ```

4. 在 Front Matter 下方添加文章内容（使用 Markdown 格式）

## 如何创建新栏目

不需要单独创建栏目，只需要在文章的 Front Matter 中添加 `categories` 字段，Jekyll 会自动创建对应的栏目页面。

## 如何部署网站

这个网站使用 GitHub Actions 自动部署。当您将代码推送到 GitHub 仓库的 main 分支时，GitHub Actions 会自动构建和部署网站。

## 本地预览

如果您想在本地预览网站，可以按照以下步骤操作：

1. 安装 Ruby 和 Jekyll
2. 克隆仓库到本地
3. 在仓库根目录下运行以下命令：
   
   ```bash
   bundle install
   bundle exec jekyll serve
   ```

4. 在浏览器中访问 `http://localhost:4000` 查看网站

## 自定义设置

您可以通过修改 `_config.yml` 文件来自定义网站的设置，例如网站标题、描述、永久链接格式等。