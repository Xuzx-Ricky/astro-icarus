---
title: "点击动效组件使用指南"
description: "深入了解 Astro Icarus 主题的点击动效组件，包括波纹效果、爱心效果等功能"
pubDatetime: 2025-02-28T00:00:00
modDatetime: 2025-02-28T00:00:00
category: "组件"
tags: ["点击动效", "动效", "组件", "交互"]
toc: true
comment: true
---

# 点击动效组件使用指南

点击动效组件是 Astro Icarus 主题的视觉效果功能，为页面添加生动的交互效果。

## 功能概述

点击动效组件提供以下效果：

1. **点击波纹** - 点击时产生波纹扩散效果
2. **双击爱心** - 双击时显示爱心飘动效果
3. **鼠标轨迹** - 鼠标移动时留下轨迹（可选）

## 基本配置

### 启用点击动效

在 `src/config.ts` 中配置：

```typescript
export const CURSOR_CONFIG = {
  enabled: true,
  clickEffect: true,
  clickEffectColor: 'var(--primary)',
  trailEffect: false,
  trailColor: 'var(--primary)',
};
```

### 配置项说明

| 字段 | 类型 | 默认值 | 说明 |
|------|------|--------|------|
| enabled | boolean | true | 是否启用 |
| clickEffect | boolean | true | 点击波纹效果 |
| clickEffectColor | string | 'var(--primary)' | 波纹颜色 |
| trailEffect | boolean | false | 鼠标轨迹效果 |
| trailColor | string | 'var(--primary)' | 轨迹颜色 |

## 功能详解

### 点击波纹

点击页面任意位置时，会产生波纹扩散效果。

**效果特点**
- 波纹从点击位置扩散
- 自动适配暗色/亮色主题
- 动画流畅自然

### 双击爱心

双击页面任意位置时，会显示爱心飘动效果。

**效果特点**
- 爱心从双击位置飘起
- 带有旋转动画
- 自动消失

### 鼠标轨迹

鼠标移动时留下轨迹效果。

**效果特点**
- 轨迹点跟随鼠标
- 逐渐淡出消失
- 仅在桌面端启用

## 使用技巧

### 自定义颜色

```typescript
export const CURSOR_CONFIG = {
  clickEffectColor: '#ff6b6b',
  trailColor: '#4ecdc4',
};
```

### 移动端适配

点击动效会自动适配移动端，轨迹效果仅在桌面端启用。

## 故障排查

### 动效不显示

检查 `enabled` 和 `clickEffect` 是否为 `true`。

### 动效卡顿

1. 关闭轨迹效果
2. 减少其他动画

## 最佳实践

### 选择合适的颜色

| 场景 | 推荐颜色 |
|------|---------|
| 亮色主题 | 主色调 |
| 暗色主题 | 霓虹色 |

### 性能考虑

- 轨迹效果会消耗更多性能
- 在低性能设备上建议关闭

## 下一步

- 了解[组件概览](/blog/21-components-overview)
- 学习[组件开发](/blog/11-plugin-development)
- 查看[故障排查](/blog/12-troubleshooting)
