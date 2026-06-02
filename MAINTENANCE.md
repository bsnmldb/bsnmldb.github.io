# bsnmldb.github.io 站点维护指南 / Site Maintenance Guide

本文档介绍如何维护和更新基于 [Chirpy](https://github.com/cotes2020/jekyll-theme-chirpy) 主题的个人主页。

This document explains how to maintain and update your personal homepage built with the [Chirpy](https://github.com/cotes2020/jekyll-theme-chirpy) Jekyll theme.

---

## 目录 / Table of Contents

1. [本地开发环境 / Local Development](#1-本地开发环境--local-development)
2. [发布新文章 / Publishing New Posts](#2-发布新文章--publishing-new-posts)
3. [更新个人信息 / Updating Personal Info](#3-更新个人信息--updating-personal-info)
4. [管理分类和标签 / Managing Categories & Tags](#4-管理分类和标签--managing-categories--tags)
5. [在文章中插入图片 / Adding Images to Posts](#5-在文章中插入图片--adding-images-to-posts)
6. [更新简历 / Updating CV](#6-更新简历--updating-cv)
7. [配置评论系统 / Configuring Comments](#7-配置评论系统--configuring-comments)
8. [更换头像和图标 / Changing Avatar & Favicons](#8-更换头像和图标--changing-avatar--favicons)
9. [自定义侧边栏 / Customizing Sidebar](#9-自定义侧边栏--customizing-sidebar)
10. [部署到 GitHub Pages / Deploying to GitHub Pages](#10-部署到-github-pages--deploying-to-github-pages)
11. [常见问题 / FAQ](#11-常见问题--faq)

---

## 1. 本地开发环境 / Local Development

### 安装依赖 / Install Dependencies

```bash
# 安装 Ruby 3.3 (macOS Homebrew)
brew install ruby@3.3

# 将 Ruby@3.3 加入 PATH（加到 ~/.zshrc，只需执行一次）
echo 'export PATH="/opt/homebrew/opt/ruby@3.3/bin:$PATH"' >> ~/.zshrc
source ~/.zshrc

# 验证版本（需要 >= 3.1）
ruby --version

# 安装 Bundler
gem install bundler

# 进入项目目录
cd bsnmldb.github.io

# 初始化 Chirpy 静态资源子模块（首次克隆后需要执行）
git submodule update --init --recursive

# 安装依赖
bundle install

# 添加 Linux 平台支持（用于 GitHub Actions 部署，首次执行一次即可）
bundle lock --add-platform x86_64-linux
```

### 本地预览 / Local Preview

```bash
# 启动本地服务器
bundle exec jekyll serve
# 打开 http://localhost:4000 查看

# 停止服务器：按 Ctrl+C
```

---

## 2. 发布新文章 / Publishing New Posts

### 文件命名规则 / File Naming Convention

文章必须放在 `_posts/` 目录下，文件名格式为：

```
_posts/YYYY-MM-DD-title.md
```

例如：`_posts/2025-01-15-my-new-post.md`

### 使用 jekyll-compose 自动创建 / Using jekyll-compose

```bash
bundle exec jekyll post "My New Post" --timestamp-format "%Y-%m-%d %H:%M:%S %z"
```

这会自动在 `_posts/` 下创建带正确文件名和日期的 Markdown 文件。

### 文章头部 Front Matter 模板 / Post Front Matter Template

```yaml
---
title: 文章标题
author: yiwei            # 必须匹配 _data/authors.yml 中的 key
date: '2025-01-15 10:00:00 +0800'   # 日期时间
categories: [NLP]        # 分类（最多一个，数组格式）
tags: [transformer, attention, notes]  # 标签（可多个）
pin: false               # 是否置顶
math: true               # 是否启用数学公式渲染（KaTeX）
description: >-          # 文章描述（可选，用于 SEO）
  一段简短的文章描述
media_subpath: '/assets/img/posts/2025-01-15-my-new-post'  # 图片路径前缀（可选）
---
```

> **注意 / Note：**
> - `categories` 建议只填一个分类，如 `[NLP]`、`[Mathematics]`、`[Tutorial]`
> - `tags` 可以填多个标签
> - `author` 必须与 `_data/authors.yml` 中定义的 key 一致
> - 如果文章包含 LaTeX 数学公式，必须设置 `math: true`
> - `media_subpath` 设置后，文章中的图片可以直接用文件名引用

### 文章正文 / Post Content

Front Matter 之后直接写 Markdown 正文：

```markdown
---
title: My First Post
author: yiwei
date: '2025-01-15 10:00:00 +0800'
categories: [Tutorial]
tags: [jekyll, blog]
---

这里是正文内容...

## 二级标题

正文段落...

![图片描述](image.png)  <!-- 如果设置了 media_subpath，直接写文件名即可 -->
```

---

## 3. 更新个人信息 / Updating Personal Info

### 修改基本信息 / Edit Basic Info

编辑 `_config.yml` 中的以下字段：

```yaml
title: Yiwei Liu              # 网站标题
tagline: NLP · Reasoning · Information Retrieval  # 副标题
description: >-               # SEO 描述
  Yiwei Liu's personal homepage...
url: "https://bsnmldb.github.io"  # 网站 URL
github:
  username: bsnmldb           # GitHub 用户名
social:
  name: Yiwei Liu             # 版权所有者姓名
  email: ywliu@smail.nju.edu.cn
  links:
    - https://github.com/bsnmldb
```

### 修改"关于"页面 / Edit About Page

编辑 `_tabs/about.md`，这是你的个人介绍页面，支持完整的 Markdown 格式。

### 修改作者信息 / Edit Author Info

编辑 `_data/authors.yml`：

```yaml
yiwei:
  name: Yiwei Liu
  url: https://github.com/bsnmldb/
```

在文章 front matter 中使用 `author: yiwei` 即可关联此作者。

### 修改联系方式 / Edit Contact Links

编辑 `_data/contact.yml`，控制侧边栏底部的联系方式图标：

```yaml
- type: github
  icon: "fab fa-github"

- type: email
  icon: "fas fa-envelope"
  noblank: true

# 取消注释以添加更多：
# - type: linkedin
#   icon: 'fab fa-linkedin'
#   url:  'https://www.linkedin.com/in/yourname'
```

---

## 4. 管理分类和标签 / Managing Categories & Tags

- **分类 (Categories)**：在文章 front matter 的 `categories` 中设置，建议每篇文章最多一个分类
- **标签 (Tags)**：在文章 front matter 的 `tags` 中设置，可以多个

Chirpy 会自动生成分类页面 (`/categories/`) 和标签页面 (`/tags/`)。

侧边栏的分类和标签页面通过 `_tabs/categories.md` 和 `_tabs/tags.md` 控制。

---

## 5. 在文章中插入图片 / Adding Images to Posts

### 方法一：使用 media_subpath（推荐）/ Method 1: Using media_subpath (Recommended)

1. 创建图片目录：
   ```bash
   mkdir -p assets/img/posts/2025-01-15-my-new-post
   ```

2. 将图片放入该目录

3. 在文章 front matter 中设置：
   ```yaml
   media_subpath: '/assets/img/posts/2025-01-15-my-new-post'
   ```

4. 在正文中直接引用文件名：
   ```markdown
   ![图片描述](image.png)
   ```

### 方法二：使用绝对路径 / Method 2: Using Absolute Path

```markdown
![图片描述](/assets/img/posts/2025-01-15-my-new-post/image.png)
```

### 控制图片大小 / Controlling Image Size

```markdown
![图片描述](image.png){: width="500px" }
```

---

## 6. 更新简历 / Updating CV

1. 将新的 PDF 简历替换 `files/CV.pdf`
2. 在 `_tabs/about.md` 中，CV 链接已设置为 `[here](/files/CV.pdf)`

如果需要添加其他文件供下载，放到 `files/` 目录下，然后在页面中链接即可。

---

## 7. 配置评论系统 / Configuring Comments

编辑 `_config.yml` 中的 `comments` 部分。Chirpy 支持以下评论系统：

### Giscus（推荐，基于 GitHub Discussions）

1. 前往 [giscus.app](https://giscus.app/) 配置
2. 将生成的配置填入 `_config.yml`：

```yaml
comments:
  provider: giscus
  giscus:
    repo: bsnmldb/bsnmldb.github.io
    repo_id: <your-repo-id>
    category: Comments
    category_id: <your-category-id>
    mapping: pathname
    reactions_enabled: 1
```

### Utterances（基于 GitHub Issues）

```yaml
comments:
  provider: utterances
  utterances:
    repo: bsnmldb/bsnmldb.github.io
    issue_term: pathname
```

---

## 8. 更换头像和图标 / Changing Avatar & Favicons

### 头像 / Avatar

替换 `assets/img/avatar.png` 即可。建议使用正方形图片，至少 192x192 像素。

`_config.yml` 中的对应配置：
```yaml
avatar: /assets/img/avatar.png
```

### 网站图标 / Favicons

1. 前往 [RealFaviconGenerator](https://realfavicongenerator.net/) 上传你的图标
2. 下载生成的文件包
3. 将生成的文件替换到 `assets/img/favicons/` 目录下（注意是 **favicons** 复数）
4. 当前目录下的文件：
   - `apple-touch-icon.png`
   - `favicon-96x96.png`
   - `favicon.ico`
   - `favicon.svg`
   - `web-app-manifest-192x192.png`
   - `web-app-manifest-512x512.png`
   - `site.webmanifest`

---

## 9. 自定义侧边栏 / Customizing Sidebar

### 侧边栏底部联系方式

编辑 `_data/contact.yml`，添加或移除社交链接。

### 侧边栏页面导航

侧边栏的页面导航由 `_tabs/` 目录控制。每个文件对应一个页面：

| 文件 | 页面 | 图标 |
|------|------|------|
| `_tabs/categories.md` | 分类 | `fas fa-stream` |
| `_tabs/tags.md` | 标签 | `fas fa-tags` |
| `_tabs/archives.md` | 归档 | `fas fa-archive` |
| `_tabs/about.md` | 关于 | `fas fa-info-circle` |

通过修改 `order` 值调整页面在侧边栏的排列顺序（数字越小越靠前）。

### 添加新页面

在 `_tabs/` 下创建新文件：

```markdown
---
layout: page
icon: fas fa-link
order: 5
title: Links
---

这里写页面内容...
```

---

## 10. 部署到 GitHub Pages / Deploying to GitHub Pages

### 自动部署 / Automatic Deployment

推送到 `master` 分支后，GitHub Actions 会自动构建和部署。

```bash
git add .
git commit -m "feat: update site content"
git push origin master
```

> **注意**：本仓库默认分支为 `master`。如果需要改为 `main`，可在 GitHub 仓库 Settings → Default branch 中修改。

### GitHub Actions 配置

部署工作流在 `.github/workflows/pages-deploy.yml`。

**重要**：在 GitHub 仓库的 Settings → Pages 中，将 Source 设置为 **GitHub Actions**（而不是 Deploy from a branch）。

### 手动触发部署

在 GitHub 仓库的 Actions 页面，选择 "Build and Deploy" 工作流，点击 "Run workflow"。

---

## 11. 常见问题 / FAQ

### Q: 本地预览正常，但部署后只显示首页？

确保 `_config.yml` 中的 `url` 设置正确，且 GitHub Pages 的 Source 设置为 **GitHub Actions**。

### Q: 数学公式不渲染？

在文章 front matter 中添加 `math: true`。

### Q: 如何修改主题颜色（亮色/暗色）？

编辑 `_config.yml` 中的 `theme_mode`：
```yaml
theme_mode: light   # 亮色模式
theme_mode: dark    # 暗色模式
theme_mode:         # 空：跟随系统设置
```

### Q: 如何添加中文支持？

`_config.yml` 中已配置：
```yaml
lang: en
languages: ["en", "zh-CN"]
```
`_data/locales/zh-CN.yml` 已存在，Chirpy 会自动支持中英切换。

### Q: 如何让文章置顶？

在文章 front matter 中设置 `pin: true`。

### Q: 如何设置文章摘要？

在 front matter 中用 `description` 字段，或在正文中使用 `<!--more-->` 分隔，分隔线之前的内容会作为摘要。

### Q: 图片链接在部署后失效？

- 确保图片文件名没有中文或特殊字符
- 确保图片已推送到 GitHub
- 使用 `media_subpath` 简化路径管理

---

## 项目结构 / Project Structure

```
bsnmldb.github.io/
├── _config.yml          # 站点配置
├── _data/               # 数据文件
│   ├── authors.yml      # 作者信息
│   ├── contact.yml      # 联系方式（侧边栏）
│   ├── share.yml        # 分享按钮
│   ├── media.yml        # 媒体文件 MIME 类型
│   ├── locales/         # 国际化翻译
│   └── origin/          # CDN 配置
├── _plugins/            # Jekyll 插件
├── _posts/              # 博客文章
├── _tabs/               # 侧边栏页面
│   ├── about.md         # 关于页面
│   ├── archives.md      # 归档
│   ├── categories.md    # 分类
│   └── tags.md          # 标签
├── assets/              # 静态资源
│   └── img/
│       ├── avatar.png   # 侧边栏头像
│       ├── favicon/     # 网站图标（你上传的原始文件）
│       ├── favicons/    # Chirpy 实际读取的图标目录
│       └── posts/       # 文章图片
├── files/               # 下载文件（如 CV.pdf）
├── .github/workflows/   # GitHub Actions
├── Gemfile              # Ruby 依赖
├── index.html           # 首页
└── .gitmodules          # Git 子模块（chirpy-static-assets）
```

---

## 参考资源 / References

- [Chirpy 主题文档](https://github.com/cotes2020/jekyll-theme-chirpy/wiki)
- [Chirpy 入门指南](https://chirpy.cotes.page/posts/getting-started/)
- [Jekyll 官方文档](https://jekyllrb.com/docs/)
- [GitHub Pages 文档](https://docs.github.com/en/pages)
