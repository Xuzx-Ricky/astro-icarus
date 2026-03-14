---
title: "性能优化指南"
description: "学习如何优化 Astro Icarus 博客的性能，提高加载速度和用户体验"
pubDatetime: 2025-02-27T08:00:00
modDatetime: 2025-02-27T08:00:00
category: "教程"
tags: ["性能", "优化", "速度", "Lighthouse"]
toc: true
comment: true
---

# 性能优化指南

网站性能直接影响用户体验和搜索排名。本指南将帮助你优化 Astro Icarus 博客的性能，获得更好的 Lighthouse 评分。

## 性能指标

### Core Web Vitals

Google 提出的三个核心性能指标：

| 指标 | 描述 | 良好标准 |
|------|------|---------|
| LCP | 最大内容绘制 | ≤ 2.5s |
| FID | 首次输入延迟 | ≤ 100ms |
| CLS | 累积布局偏移 | ≤ 0.1 |

### 其他重要指标

| 指标 | 描述 | 良好标准 |
|------|------|---------|
| FCP | 首次内容绘制 | ≤ 1.8s |
| TTFB | 首字节时间 | ≤ 600ms |
| TTI | 可交互时间 | ≤ 3.8s |

## 图片优化

### 使用 WebP 格式

WebP 格式比 JPEG 和 PNG 更小，质量更好。

**配置**

```javascript
// astro.config.mjs
export default defineConfig({
  image: {
    service: {
      entrypoint: 'astro/assets/services/sharp',
      config: {
        webp: {
          quality: 80,
        },
      },
    },
  },
});
```

### 响应式图片

根据设备屏幕大小提供不同尺寸的图片。

```astro
---
import { Image } from 'astro:assets';
import myImage from '../images/my-image.jpg';
---

<Image 
  src={myImage} 
  alt="描述" 
  widths={[400, 800, 1200]}
  sizes="(max-width: 800px) 100vw, 800px"
/>
```

### 懒加载

延迟加载屏幕外的图片。

```html
<img src="image.jpg" loading="lazy" alt="描述" />
```

### 图片压缩

使用工具压缩图片：

```bash
# 安装 imagemin
npm install -g imagemin-cli

# 压缩图片
imagemin images/* --out-dir=dist/images
```

## 代码优化

### JavaScript 优化

**代码分割**

```javascript
// 动态导入
const module = await import('./module.js');
```

**延迟加载非关键脚本**

```html
<script src="analytics.js" defer></script>
```

**使用 async**

```html
<script src="script.js" async></script>
```

### CSS 优化

**关键 CSS 内联**

将关键 CSS 直接内联到 HTML 中。

**延迟加载非关键 CSS**

```html
<link rel="preload" href="styles.css" as="style" onload="this.onload=null;this.rel='stylesheet'">
```

**移除未使用的 CSS**

使用 PurgeCSS 移除未使用的 CSS：

```javascript
// astro.config.mjs
import purgecss from 'astro-purgecss';

export default defineConfig({
  integrations: [purgecss()],
});
```

## 字体优化

### 使用 font-display

```css
@font-face {
  font-family: 'MyFont';
  src: url('myfont.woff2') format('woff2');
  font-display: swap;
}
```

### 预加载关键字体

```html
<link rel="preload" href="font.woff2" as="font" type="font/woff2" crossorigin>
```

### 使用系统字体栈

```css
body {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
}
```

## 缓存优化

### HTTP 缓存头

配置服务器返回正确的缓存头：

```
Cache-Control: public, max-age=31536000, immutable
```

### 服务工作者缓存

使用 Service Worker 缓存资源：

```javascript
// sw.js
self.addEventListener('fetch', (event) => {
  event.respondWith(
    caches.match(event.request).then((response) => {
      return response || fetch(event.request);
    })
  );
});
```

## CDN 优化

### 使用 CDN

将静态资源部署到 CDN，加速全球访问。

**推荐 CDN**

| CDN | 特点 |
|-----|------|
| Cloudflare | 免费，全球节点 |
| jsDelivr | 开源项目免费 |
| unpkg | npm 包 CDN |

### 预连接 CDN

```html
<link rel="preconnect" href="https://cdn.jsdelivr.net">
<link rel="dns-prefetch" href="https://cdn.jsdelivr.net">
```

## 构建优化

### 压缩资源

**HTML 压缩**

```javascript
// astro.config.mjs
export default defineConfig({
  compressHTML: true,
});
```

**CSS/JS 压缩**

Astro 会自动压缩 CSS 和 JS。

###  Tree Shaking

移除未使用的代码。

```javascript
// 只导入需要的函数
import { format } from 'date-fns';
```

## 性能测试

### Lighthouse

使用 Chrome DevTools 中的 Lighthouse 进行性能测试。

**测试步骤**

1. 打开 Chrome DevTools
2. 切换到 Lighthouse 标签
3. 选择测试类别
4. 点击 "Generate report"

### WebPageTest

[WebPageTest](https://www.webpagetest.org) 提供详细的性能分析报告。

### GTmetrix

[GTmetrix](https://gtmetrix.com) 提供性能评分和优化建议。

## 性能监控

### 真实用户监控 (RUM)

使用 Web Vitals 库监控真实用户数据：

```javascript
import { getCLS, getFID, getFCP, getLCP, getTTFB } from 'web-vitals';

getCLS(console.log);
getFID(console.log);
getFCP(console.log);
getLCP(console.log);
getTTFB(console.log);
```

### 性能预算

设定性能预算，防止性能退化：

```javascript
// .github/workflows/performance.yml
name: Performance Budget

on: [push]

jobs:
  lighthouse:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Run Lighthouse
        uses: treosh/lighthouse-ci-action@v10
        with:
          budgetPath: ./budget.json
```

## 优化清单

### 图片

- [ ] 使用 WebP/AVIF 格式
- [ ] 压缩图片
- [ ] 使用响应式图片
- [ ] 懒加载图片
- [ ] 使用适当的图片尺寸

### CSS

- [ ] 内联关键 CSS
- [ ] 延迟加载非关键 CSS
- [ ] 移除未使用的 CSS
- [ ] 使用 CSS 变量

### JavaScript

- [ ] 代码分割
- [ ] 延迟加载非关键脚本
- [ ] 使用 Tree Shaking
- [ ] 压缩 JS

### 字体

- [ ] 使用 font-display: swap
- [ ] 预加载关键字体
- [ ] 使用系统字体栈

### 缓存

- [ ] 配置 HTTP 缓存头
- [ ] 使用 Service Worker
- [ ] 版本化静态资源

### CDN

- [ ] 使用 CDN
- [ ] 预连接 CDN 域名
- [ ] 启用 HTTP/2

## 常见问题

### 图片加载慢

1. 使用 WebP 格式
2. 压缩图片
3. 使用 CDN
4. 启用懒加载

### CSS 阻塞渲染

1. 内联关键 CSS
2. 延迟加载非关键 CSS
3. 使用 media 属性

### JavaScript 执行慢

1. 代码分割
2. 延迟加载
3. 使用 Web Workers

## 下一步

- 了解[安全加固](/blog/10-security)
- 探索[插件开发](/blog/11-plugin-development)
- 学习[故障排查](/blog/12-troubleshooting)
