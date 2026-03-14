---
title: "右键菜单组件使用指南"
description: "深入了解 Astro Icarus 主题的右键菜单组件，包括导航、复制、搜索等功能"
pubDatetime: 2025-02-27T23:00:00
modDatetime: 2025-02-27T23:00:00
category: "组件"
tags: ["右键菜单", "菜单", "组件", "交互"]
toc: true
comment: true
---

# 右键菜单组件使用指南

右键菜单组件是 Astro Icarus 主题的交互功能，提供自定义的右键菜单，替代浏览器默认菜单。

## 功能概述

右键菜单组件提供以下功能：

1. **导航操作** - 前进、后退、刷新、回到顶部
2. **复制粘贴** - 复制选中文本、粘贴文本
3. **链接操作** - 复制链接、新窗口打开
4. **图片操作** - 复制图片、下载图片
5. **搜索功能** - 搜索选中文本
6. **主题切换** - 切换暗色/亮色模式
7. **阅读模式** - 进入阅读模式

## 基本配置

### 启用右键菜单

在 `src/config.ts` 中配置：

```typescript
export const RIGHT_MENU_CONFIG = {
  enabled: true,
  items: {
    navigation: true,
    copyPaste: true,
    search: true,
    themeToggle: true,
    readMode: true,
    imageActions: true,
    linkActions: true,
  },
  searchEngines: [
    { name: '百度', url: 'https://www.baidu.com/s?wd=', icon: 'fa-search' },
    { name: '必应', url: 'https://cn.bing.com/search?q=', icon: 'fa-search' },
    { name: 'Google', url: 'https://www.google.com/search?q=', icon: 'fa-google' },
  ],
};
```

### 配置项说明

| 字段 | 类型 | 默认值 | 说明 |
|------|------|--------|------|
| enabled | boolean | true | 是否启用 |
| items | object | - | 菜单项配置 |
| searchEngines | array | - | 搜索引擎 |

## 功能详解

### 导航操作

- **后退** - 返回上一页
- **前进** - 前进到下一页
- **刷新** - 刷新当前页面
- **回到顶部** - 滚动到页面顶部

### 复制粘贴

- **复制选中文本** - 复制当前选中的文本
- **粘贴文本** - 粘贴剪贴板内容到输入框

### 链接操作

- **复制链接** - 复制链接地址
- **新窗口打开** - 在新窗口打开链接

### 图片操作

- **复制图片** - 复制图片到剪贴板
- **下载图片** - 下载图片到本地

### 搜索功能

- **搜索选中文本** - 使用配置的搜索引擎搜索选中文本

### 主题切换

- **切换主题** - 切换暗色/亮色模式

### 阅读模式

- **阅读模式** - 隐藏侧边栏和导航栏，专注阅读

## 使用技巧

### 快捷键

右键菜单没有快捷键，使用鼠标右键触发。

### 菜单定位

菜单会自动调整位置，确保不会超出视口。

## 故障排查

### 右键菜单不显示

检查 `enabled` 是否为 `true`。

### 功能不工作

1. 检查浏览器是否支持相关 API
2. 检查权限设置

## 最佳实践

### 选择合适的搜索引擎

| 用户群体 | 推荐搜索引擎 |
|---------|-------------|
| 国内用户 | 百度、必应 |
| 国际用户 | Google、Bing |

## 下一步

- 了解[组件概览](/blog/21-components-overview)
- 学习[组件开发](/blog/11-plugin-development)
- 查看[故障排查](/blog/12-troubleshooting)
