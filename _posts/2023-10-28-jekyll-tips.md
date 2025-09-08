---
layout: post
title: "Jekyll 使用技巧分享"
date: 2023-10-28 14:30:00 +0800
categories:
- 技术
tags:
- Jekyll
- GitHub Pages
- 静态网站
---
# Jekyll 使用技巧分享

在使用 Jekyll 搭建网站的过程中，我积累了一些实用的技巧，现在分享给大家。

## 快速开始

要创建一个新的 Jekyll 网站，您可以使用以下命令：

```bash
jekyll new my-site
cd my-site
bundle exec jekyll serve
```

这样您就可以在本地访问 `http://localhost:4000` 查看您的网站了。

## 自定义布局

Jekyll 的一个强大特性是可以自定义布局。您可以在 `_layouts` 目录下创建不同的布局文件，然后在文章的 Front Matter 中指定使用哪个布局。

## 自动化部署

使用 GitHub Actions 可以实现网站的自动构建和部署。您只需要在 `.github/workflows` 目录下创建一个工作流文件，配置构建和部署步骤即可。

## 更多资源

- [Jekyll 官方文档](https://jekyllrb.com/docs/)
- [GitHub Pages 文档](https://docs.github.com/en/pages)

希望这些技巧对您有所帮助！