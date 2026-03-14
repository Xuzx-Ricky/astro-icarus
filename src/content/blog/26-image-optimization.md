---
title: "图片优化指南"
description: "深入了解 Astro Icarus 主题的图片优化功能，包括自动压缩、WebP转换、懒加载等"
pubDatetime: 2025-02-28T01:00:00
modDatetime: 2025-02-28T01:00:00
category: "教程"
tags: ["图片", "优化", "WebP", "懒加载"]
toc: true
comment: true
---

# 图片优化指南

图片优化是提高网站性能的重要手段。Astro Icarus 主题提供了全面的图片优化功能。

## 功能概述

图片优化功能包括：

1. **自动压缩** - 构建时自动压缩图片
2. **格式转换** - 自动转换为 WebP 格式
3. **懒加载** - 延迟加载屏幕外图片
4. **响应式图片** - 根据设备提供不同尺寸

## 基本配置

### 图片配置

在 `astro.config.mjs` 中配置：

```javascript
export default defineConfig({
  image: {
    service: {
      entrypoint: 'astro/assets/services/sharp',
      config: {
        webp: {
          quality: 80,
          effort: 6,
        },
        jpeg: {
          quality: 80,
          progressive: true,
        },
      },
    },
  },
});
```

### 懒加载配置

在 `src/config.ts` 中配置：

```typescript
export const LAZY_LOAD_CONFIG = {
  enabled: true,
  placeholder: '/images/placeholder.svg',
  threshold: 0.1,
  rootMargin: '50px',
  allowClickBeforeLoad: true,
};
```

## 使用 OptimizedImage 组件

### 基本用法

```astro
---
import OptimizedImage from '../components/OptimizedImage.astro';
---

<OptimizedImage
  src="/images/photo.jpg"
  alt="图片描述"
  width={800}
  height={600}
  loading="lazy"
/>
```

### Props 说明

| 属性 | 类型 | 默认值 | 说明 |
|------|------|--------|------|
| src | string | - | 图片路径 |
| alt | string | - | 替代文本 |
| width | number | 800 | 宽度 |
| height | number | 600 | 高度 |
| loading | string | 'lazy' | 加载方式 |
| format | string | 'webp' | 输出格式 |
| quality | number | 80 | 图片质量 |

## 图片格式

### 推荐格式

| 格式 | 适用场景 | 压缩率 |
|------|---------|--------|
| WebP | 通用 | 高 |
| AVIF | 新一代 | 最高 |
| JPEG | 照片 | 中 |
| PNG | 透明 | 低 |
| SVG | 图标 | - |

### 格式选择

- **照片** - 使用 WebP 或 JPEG
- **截图** - 使用 WebP 或 PNG
- **图标** - 使用 SVG
- **动画** - 使用 WebP 或 GIF

## 图片尺寸

### 推荐尺寸

| 用途 | 尺寸 |
|------|------|
| 封面图 | 1200x630 |
| 文章配图 | 800x450 |
| 头像 | 200x200 |
| 缩略图 | 400x225 |

### 响应式图片

```astro
<Image 
  src={myImage}
  alt="描述"
  widths={[400, 800, 1200]}
  sizes="(max-width: 800px) 100vw, 800px"
/>
```

## 图片压缩

### 压缩工具

| 工具 | 类型 | 特点 |
|------|------|------|
| Sharp | Node.js | 快速 |
| ImageMagick | 命令行 | 功能丰富 |
| TinyPNG | 在线 | 简单 |
| Squoosh | 在线 | 可视化 |

### 压缩命令

```bash
# 使用 Sharp
pnpm optimize

# 使用 ImageMagick
convert input.jpg -quality 80 output.jpg
```

## 懒加载

### 原生懒加载

```html
<img src="image.jpg" loading="lazy" alt="描述" />
```

### Intersection Observer

```javascript
const observer = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      const img = entry.target;
      img.src = img.dataset.src;
      observer.unobserve(img);
    }
  });
});

document.querySelectorAll('img[data-src]').forEach(img => {
  observer.observe(img);
});
```

## 最佳实践

### 图片优化清单

- [ ] 使用合适的格式
- [ ] 压缩图片大小
- [ ] 使用懒加载
- [ ] 提供响应式图片
- [ ] 添加 alt 文本

### 性能建议

1. 图片大小控制在 200KB 以内
2. 使用 CDN 加速
3. 启用 HTTP/2
4. 设置合理的缓存策略

## 故障排查

### 图片不显示

1. 检查图片路径
2. 检查文件是否存在
3. 检查权限设置

### 图片加载慢

1. 压缩图片
2. 使用 CDN
3. 启用懒加载

## 下一步

- 了解[性能优化](/blog/09-performance)
- 学习[组件开发](/blog/11-plugin-development)
- 查看[故障排查](/blog/12-troubleshooting)
