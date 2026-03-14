---
title: "组件概览"
description: "Astro Icarus 主题所有组件的完整介绍和使用说明"
pubDatetime: 2025-02-27T20:00:00
modDatetime: 2025-02-27T20:00:00
category: "组件"
tags: ["组件", "概览", "介绍", "使用"]
toc: true
comment: true
---

# 组件概览

Astro Icarus 主题包含丰富的组件，本指南将介绍所有组件的功能和使用方法。

## 布局组件

### BaseLayout

基础布局组件，所有页面都使用此布局。

**功能**
- HTML 结构
- 全局样式
- SEO 元素
- 脚本加载

**使用**

```astro
---
import BaseLayout from '../layouts/BaseLayout.astro';
---

<BaseLayout title="页面标题">
  <slot />
</BaseLayout>
```

## 导航组件

### Navbar

顶部导航栏组件。

**功能**
- Logo 和网站标题
- 导航链接
- 搜索按钮
- 主题切换

**配置**

```typescript
export const NAV_LINKS = [
  { href: '/', label: '首页', icon: 'fa-home' },
  { href: '/about', label: '关于', icon: 'fa-user' },
];
```

### Footer

页脚组件。

**功能**
- 版权信息
- 备案信息
- 统计信息
- 社交链接

## 文章组件

### ArticleCard

文章卡片组件，用于文章列表。

**功能**
- 封面图
- 标题和描述
- 元信息（日期、分类、阅读时间）
- 标签

**Props**

| 属性 | 类型 | 说明 |
|------|------|------|
| post | CollectionEntry | 文章数据 |

### TOC

文章目录组件。

**功能**
- 自动生成目录
- 滚动高亮
- 点击跳转

**Props**

| 属性 | 类型 | 说明 |
|------|------|------|
| headings | Heading[] | 标题列表 |

## 侧边栏组件

### ProfileWidget

个人资料组件。

**功能**
- 头像
- 名称和简介
- 社交链接
- 统计信息

### Hitokoto

一言组件。

**功能**
- 随机语录
- 多提供商支持
- 自动缓存

**配置**

```typescript
export const HITOKOTO_CONFIG = {
  enabled: true,
  providers: ['classic', 'wandering_earth'],
};
```

### SmartCalendar

智能日历组件。

**功能**
- 公历显示
- 农历显示
- 节气显示
- 倒计时

**配置**

```typescript
export const SMART_CALENDAR_CONFIG = {
  enabled: true,
  showLunar: true,
  showSolarTerms: true,
};
```

### RecentPosts

最近文章组件。

**功能**
- 显示最近文章列表
- 可配置数量

### Categories

分类组件。

**功能**
- 显示所有分类
- 显示文章数量

### Tags

标签组件。

**功能**
- 显示所有标签
- 标签云效果

### Archives

归档组件。

**功能**
- 按月归档
- 显示文章数量

### FriendLinks

友情链接组件。

**功能**
- 显示友链列表
- 卡片式布局

## 功能组件

### Comments

评论组件。

**支持系统**
- Giscus
- Gitalk
- Valine
- Waline
- Twikoo
- Utterances
- Disqus
- 畅言云评

**配置**

```typescript
export const COMMENT_CONFIG = {
  provider: 'giscus',
  giscus: {
    repo: 'username/repo',
    repoId: 'xxx',
  },
};
```

### Search

搜索组件。

**功能**
- 全文搜索
- 实时结果
- 键盘快捷键

### Share

分享组件。

**功能**
- 多平台分享
- 复制链接

### Donation

打赏组件。

**功能**
- 支付宝
- 微信支付
- PayPal

### Copyright

版权组件。

**功能**
- 版权声明
- 许可协议
- 转载说明

## 交互组件

### RightMenu

右键菜单组件。

**功能**
- 导航操作
- 复制粘贴
- 搜索文本
- 主题切换

### ClickEffect

点击动效组件。

**功能**
- 点击波纹
- 双击爱心

### AIAssistant

AI 助手组件。

**功能**
- 文章摘要
- 翻译功能
- 相关推荐

## 工具组件

### OptimizedImage

优化图片组件。

**功能**
- 自动压缩
- WebP 转换
- 懒加载

**Props**

| 属性 | 类型 | 说明 |
|------|------|------|
| src | string | 图片路径 |
| alt | string | 替代文本 |
| width | number | 宽度 |
| height | number | 高度 |

## 自定义组件

### 创建自定义组件

```astro
---
// MyComponent.astro
interface Props {
  title: string;
}

const { title } = Astro.props;
---

<div class="my-component">
  <h2>{title}</h2>
  <slot />
</div>

<style>
  .my-component {
    padding: 1rem;
    background: var(--card-bg);
    border-radius: var(--radius);
  }
</style>
```

### 使用自定义组件

```astro
---
import MyComponent from '../components/MyComponent.astro';
---

<MyComponent title="我的组件">
  <p>组件内容</p>
</MyComponent>
```

## 组件配置

### 启用/禁用组件

在 `src/config.ts` 中配置：

```typescript
export const SIDEBAR_WIDGETS_CONFIG = {
  widgets: {
    profile: { enabled: true },
    hitokoto: { enabled: true },
    smartCalendar: { enabled: true },
  },
};
```

### 自定义组件顺序

```typescript
export const SIDEBAR_WIDGETS_CONFIG = {
  left: ['profile', 'hitokoto', 'smartCalendar'],
  right: ['recentPosts', 'categories', 'tags'],
};
```

## 下一步

- 了解[一言组件](/blog/19-hitokoto-guide)
- 了解[智能日历组件](/blog/20-smart-calendar-guide)
- 学习[组件开发](/blog/11-plugin-development)
