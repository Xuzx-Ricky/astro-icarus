---
title: "API 参考"
description: "Astro Icarus 主题的配置 API 完整参考文档"
pubDatetime: 2025-02-27T13:00:00
modDatetime: 2025-02-27T13:00:00
category: "参考"
tags: ["API", "参考", "配置", "文档"]
toc: true
comment: true
---

# API 参考

本文档提供 Astro Icarus 主题所有配置选项的完整参考。

## SITE 配置

### 基本信息

| 字段 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| title | string | 是 | - | 网站标题 |
| subtitle | string | 否 | '' | 副标题 |
| description | string | 否 | '' | 网站描述 |
| url | string | 是 | - | 网站 URL |
| lang | string | 否 | 'zh-CN' | 语言代码 |
| favicon | string | 否 | '/favicon.svg' | 网站图标 |
| author | string | 否 | '' | 默认作者 |
| startYear | number | 否 | 2024 | 建站年份 |

### 示例

```typescript
export const SITE = {
  title: '我的博客',
  subtitle: '记录生活点滴',
  description: '这是一个使用 Astro Icarus 主题搭建的个人博客',
  url: 'https://example.com',
  lang: 'zh-CN',
  favicon: '/favicon.svg',
  author: '作者名',
  startYear: 2024,
};
```

## AUTHOR 配置

### 作者信息

| 字段 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| name | string | 是 | - | 作者名称 |
| avatar | string | 否 | '' | 头像路径 |
| bio | string | 否 | '' | 个人简介 |
| location | string | 否 | '' | 所在地 |
| email | string | 否 | '' | 邮箱地址 |
| github | string | 否 | '' | GitHub 链接 |
| twitter | string | 否 | '' | Twitter 链接 |
| weibo | string | 否 | '' | 微博链接 |

### 示例

```typescript
export const AUTHOR = {
  name: '作者名',
  avatar: '/images/avatar.jpg',
  bio: '一个热爱技术、热爱生活的开发者',
  location: '中国',
  email: 'email@example.com',
  github: 'https://github.com/username',
  twitter: '',
  weibo: '',
};
```

## NAV_LINKS 配置

### 导航链接

| 字段 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| href | string | 是 | - | 链接地址 |
| label | string | 是 | - | 显示文本 |
| icon | string | 否 | '' | Font Awesome 图标类 |

### 示例

```typescript
export const NAV_LINKS = [
  { href: '/', label: '首页', icon: 'fa-home' },
  { href: '/archives', label: '归档', icon: 'fa-archive' },
  { href: '/about', label: '关于', icon: 'fa-user' },
];
```

## COMMENT_CONFIG 配置

### 评论系统

| 字段 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| enabled | boolean | 否 | true | 是否启用 |
| provider | string | 是 | - | 评论提供商 |

### Giscus 配置

| 字段 | 类型 | 必填 | 说明 |
|------|------|------|------|
| repo | string | 是 | GitHub 仓库 |
| repoId | string | 是 | 仓库 ID |
| category | string | 是 | 讨论分类 |
| categoryId | string | 是 | 分类 ID |
| mapping | string | 否 | 页面映射方式 |
| reactionsEnabled | boolean | 否 | 是否启用表情 |
| emitMetadata | boolean | 否 | 是否发送元数据 |
| inputPosition | string | 否 | 输入框位置 |
| lang | string | 否 | 界面语言 |

### 示例

```typescript
export const COMMENT_CONFIG = {
  enabled: true,
  provider: 'giscus',
  giscus: {
    repo: 'username/repo',
    repoId: 'R_kgDxxx',
    category: 'Announcements',
    categoryId: 'DIC_kwDxxx',
    mapping: 'pathname',
    reactionsEnabled: true,
    emitMetadata: false,
    inputPosition: 'top',
    lang: 'zh-CN',
  },
};
```

## SEARCH_CONFIG 配置

### 搜索配置

| 字段 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| enabled | boolean | 否 | true | 是否启用 |
| provider | string | 否 | 'fuse' | 搜索提供商 |

### Fuse.js 配置

| 字段 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| keys | array | 否 | ['title', 'description'] | 搜索字段 |
| threshold | number | 否 | 0.3 | 匹配阈值 |

### 示例

```typescript
export const SEARCH_CONFIG = {
  enabled: true,
  provider: 'fuse',
  fuse: {
    keys: ['title', 'description', 'content', 'tags'],
    threshold: 0.3,
  },
};
```

## 文章 Frontmatter

### 基本字段

| 字段 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| title | string | 是 | - | 文章标题 |
| description | string | 是 | - | 文章描述 |
| pubDatetime | date | 是 | - | 发布时间 |
| modDatetime | date | 否 | - | 修改时间 |
| category | string | 是 | - | 分类 |
| tags | array | 否 | [] | 标签列表 |

### 高级字段

| 字段 | 类型 | 默认值 | 说明 |
|------|------|--------|------|
| thumbnail | string | - | 封面图 |
| toc | boolean | true | 显示目录 |
| comment | boolean | true | 开启评论 |
| sticky | boolean | false | 置顶 |
| hidden | boolean | false | 隐藏 |
| layout | string | 'three-column' | 布局 |
| showShare | boolean | true | 显示分享 |
| showDonation | boolean | false | 显示打赏 |
| showSidebar | boolean | true | 显示侧边栏 |

## 工具函数

### formatDate

格式化日期。

```typescript
function formatDate(date: Date | string): string
```

**示例**

```typescript
import { formatDate } from '../utils/helpers';

formatDate('2025-02-27');
// 返回: "2025年2月27日"
```

### calculateReadingTime

计算阅读时间。

```typescript
function calculateReadingTime(content: string): number
```

**示例**

```typescript
import { calculateReadingTime } from '../utils/helpers';

const minutes = calculateReadingTime(articleBody);
// 返回: 5 (分钟)
```

### getWordCount

获取字数统计。

```typescript
function getWordCount(content: string): number
```

**示例**

```typescript
import { getWordCount } from '../utils/helpers';

const count = getWordCount(articleBody);
// 返回: 1500 (字)
```

## CSS 变量

### 颜色变量

| 变量名 | 说明 |
|--------|------|
| --primary | 主色调 |
| --text | 主要文字颜色 |
| --text-strong | 强调文字颜色 |
| --text-light | 次要文字颜色 |
| --bg | 页面背景色 |
| --card-bg | 卡片背景色 |
| --border | 边框颜色 |

### 尺寸变量

| 变量名 | 默认值 | 说明 |
|--------|--------|------|
| --radius | 4px | 圆角大小 |
| --radius-lg | 8px | 大圆角 |

## 下一步

- 学习[最佳实践](/blog/15-best-practices)
- 了解[贡献指南](/blog/16-contributing)
- 查看[更新日志](/blog/17-changelog)
