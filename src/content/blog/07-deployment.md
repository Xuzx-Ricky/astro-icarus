---
title: "部署指南"
description: "详细介绍如何将 Astro Icarus 博客部署到各种平台，包括 Cloudflare Pages、Vercel、Netlify 等"
pubDatetime: 2025-02-27T06:00:00
modDatetime: 2025-02-27T06:00:00
category: "教程"
tags: ["部署", "Cloudflare", "Vercel", "Netlify"]
toc: true
comment: true
---

# 部署指南

完成博客开发后，下一步就是将其部署到线上，让全世界都能访问。本指南将详细介绍如何将 Astro Icarus 博客部署到各种主流平台。

## 部署前准备

### 构建项目

在部署之前，需要先构建项目：

```bash
pnpm build
```

构建完成后，会在 `dist` 目录下生成静态文件。

### 检查构建结果

1. 确保构建没有错误
2. 检查 `dist` 目录下的文件
3. 预览构建结果：`pnpm preview`

## Cloudflare Pages 部署

Cloudflare Pages 是一个免费的静态网站托管服务，提供全球 CDN 加速。

### 方法一：Git 集成（推荐）

**步骤 1：创建 GitHub 仓库**

```bash
# 初始化 Git 仓库
git init

# 添加所有文件
git add .

# 提交
git commit -m "Initial commit"

# 添加远程仓库
git remote add origin https://github.com/yourname/my-blog.git

# 推送
git push -u origin main
```

**步骤 2：连接 Cloudflare Pages**

1. 登录 [Cloudflare Dashboard](https://dash.cloudflare.com)
2. 点击左侧菜单的 "Pages"
3. 点击 "创建项目"
4. 选择 "连接到 Git"
5. 授权 Cloudflare 访问你的 GitHub 仓库
6. 选择你的博客仓库

**步骤 3：配置构建设置**

| 设置项 | 值 |
|--------|-----|
| Framework preset | `Astro` |
| Build command | `pnpm build` |
| Build output directory | `dist` |

**步骤 4：添加环境变量（可选）**

如果你的构建需要环境变量，可以在 "Environment variables" 中添加。

**步骤 5：部署**

点击 "保存并部署"，等待几分钟后，你的博客就会部署完成。

### 方法二：直接上传

1. 运行 `pnpm build` 构建项目
2. 登录 Cloudflare Dashboard
3. 进入 Pages → 创建项目
4. 选择 "直接上传"
5. 上传 `dist` 文件夹

### 绑定自定义域名

1. 进入项目的 "自定义域" 设置
2. 点击 "设置自定义域"
3. 输入你的域名
4. 按照提示配置 DNS 记录
5. 等待 DNS 生效（通常几分钟到几小时）

## Vercel 部署

Vercel 是另一个流行的静态网站托管平台，特别适合前端项目。

### Git 集成部署

**步骤 1：导入项目**

1. 登录 [Vercel](https://vercel.com)
2. 点击 "Add New Project"
3. 导入你的 GitHub 仓库

**步骤 2：配置构建设置**

Vercel 会自动检测 Astro 项目，使用默认设置即可。

**步骤 3：部署**

点击 "Deploy"，等待部署完成。

### 使用 Vercel CLI

```bash
# 安装 Vercel CLI
npm i -g vercel

# 登录
vercel login

# 部署
vercel --prod
```

## Netlify 部署

Netlify 是功能强大的静态网站托管平台，提供丰富的功能。

### Git 集成部署

**步骤 1：导入项目**

1. 登录 [Netlify](https://netlify.com)
2. 点击 "Add new site" → "Import an existing project"
3. 选择 GitHub
4. 选择你的仓库

**步骤 2：配置构建设置**

| 设置项 | 值 |
|--------|-----|
| Build command | `pnpm build` |
| Publish directory | `dist` |

**步骤 3：部署**

点击 "Deploy site"，等待部署完成。

### 使用 Netlify CLI

```bash
# 安装 Netlify CLI
npm i -g netlify-cli

# 登录
netlify login

# 部署
netlify deploy --prod --dir=dist
```

### Netlify Drop

最简单的部署方式：

1. 运行 `pnpm build`
2. 访问 [Netlify Drop](https://app.netlify.com/drop)
3. 将 `dist` 文件夹拖拽到页面

## GitHub Pages 部署

GitHub Pages 是 GitHub 提供的免费静态网站托管服务。

### 使用 GitHub Actions

**步骤 1：创建工作流文件**

创建 `.github/workflows/deploy.yml`：

```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches: [main]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      
      - name: Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: 20
          
      - name: Install pnpm
        uses: pnpm/action-setup@v2
        with:
          version: 9
          
      - name: Install dependencies
        run: pnpm install
        
      - name: Build
        run: pnpm build
        
      - name: Deploy
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./dist
```

**步骤 2：启用 GitHub Pages**

1. 进入仓库的 Settings → Pages
2. Source 选择 "Deploy from a branch"
3. Branch 选择 "gh-pages"

## 阿里云 OSS 部署

阿里云 OSS 是国内常用的静态资源存储服务。

### 使用 OSS 控制台

1. 创建 OSS Bucket
2. 开启静态网站托管
3. 上传 `dist` 文件夹内容

### 使用 OSS 工具

```bash
# 安装 ossutil
wget http://gosspublic.alicdn.com/ossutil/1.7.14/ossutil64
chmod 755 ossutil64

# 配置
./ossutil64 config

# 上传
./ossutil64 cp -r dist/ oss://your-bucket-name/
```

### 使用 GitHub Actions

```yaml
name: Deploy to Aliyun OSS

on:
  push:
    branches: [main]

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      
      - name: Build
        run: |
          pnpm install
          pnpm build
          
      - name: Deploy to OSS
        uses: manyuanrong/setup-ossutil@v2.0
        with:
          endpoint: oss-cn-hangzhou.aliyuncs.com
          access-key-id: ${{ secrets.OSS_ACCESS_KEY_ID }}
          access-key-secret: ${{ secrets.OSS_ACCESS_KEY_SECRET }}
          
      - run: ossutil cp -rf dist/ oss://your-bucket-name/
```

## 腾讯云 COS 部署

腾讯云 COS 是另一个国内常用的对象存储服务。

### 使用 COS 控制台

1. 创建 COS Bucket
2. 开启静态网站
3. 上传 `dist` 文件夹内容

### 使用 COS CLI

```bash
# 安装 coscmd
pip install coscmd

# 配置
coscmd config -a <AccessKeyId> -s <AccessKeySecret> \
  -b <BucketName> -r <Region>

# 上传
coscmd upload -r dist/ /
```

## 自动部署

### GitHub Actions 自动部署

创建 `.github/workflows/deploy.yml`：

```yaml
name: Deploy

on:
  push:
    branches: [main]

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      
      - name: Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: 20
          
      - name: Setup pnpm
        uses: pnpm/action-setup@v2
        with:
          version: 9
          
      - name: Install dependencies
        run: pnpm install
        
      - name: Build
        run: pnpm build
        
      # 部署到 Cloudflare Pages
      - name: Deploy to Cloudflare Pages
        uses: cloudflare/pages-action@v1
        with:
          apiToken: ${{ secrets.CLOUDFLARE_API_TOKEN }}
          accountId: ${{ secrets.CLOUDFLARE_ACCOUNT_ID }}
          projectName: my-blog
          directory: dist
```

## 部署最佳实践

### 环境变量管理

使用环境变量管理不同环境的配置：

```bash
# .env.production
PUBLIC_ANALYTICS_ID=G-XXXXXXXXXX
```

### 构建优化

1. **压缩资源** - 启用 gzip/brotli
2. **图片优化** - 使用 WebP 格式
3. **代码分割** - 按需加载
4. **缓存策略** - 设置合理的缓存头

### 性能监控

1. 使用 Google Analytics 监控流量
2. 使用 Google Search Console 监控搜索表现
3. 使用 Lighthouse 定期测试性能

## 常见问题

### 构建失败

1. 检查依赖是否安装完整
2. 检查 Node.js 版本
3. 检查配置文件语法

### 部署后样式丢失

1. 检查 base URL 配置
2. 检查资源路径
3. 检查 CSS 文件是否正确生成

### 404 错误

1. 检查路由配置
2. 检查文件是否正确上传
3. 检查服务器重写规则

## 下一步

- 探索[高级功能](/blog/08-advanced-features)
- 学习[性能优化](/blog/09-performance)
- 了解[安全加固](/blog/10-security)
