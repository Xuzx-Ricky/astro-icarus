---
title: "智能日历组件使用指南"
description: "深入了解 Astro Icarus 主题的智能日历组件，包括农历、节气、倒计时等功能"
pubDatetime: 2025-02-27T19:00:00
modDatetime: 2025-02-27T19:00:00
category: "组件"
tags: ["日历", "农历", "节气", "组件"]
toc: true
comment: true
---

# 智能日历组件使用指南

智能日历组件是 Astro Icarus 主题的特色功能，集成了日历、农历、节气、节假日和倒计时等多种功能。

## 功能概述

智能日历组件包含以下功能：

1. **公历显示** - 显示当前日期、星期、月份
2. **农历显示** - 显示农历日期
3. **节气显示** - 显示二十四节气
4. **节假日显示** - 显示传统节日和法定假日
5. **倒计时功能** - 显示倒计时事件

## 基本配置

### 启用智能日历

在 `src/config.ts` 中配置：

```typescript
export const SMART_CALENDAR_CONFIG = {
  enabled: true,
  showLunar: true,
  showSolarTerms: true,
  showHolidays: true,
  events: [
    { date: '01-01', name: '元旦', type: 'holiday' },
    { date: '02-14', name: '情人节', type: 'festival' },
    { date: '05-01', name: '劳动节', type: 'holiday' },
    { date: '10-01', name: '国庆节', type: 'holiday' },
    { date: '12-25', name: '圣诞节', type: 'festival' },
  ],
  countdowns: [
    {
      id: 'newyear',
      title: '新年倒计时',
      targetDate: '2026-01-01T00:00:00',
      icon: 'fa-glass-cheers',
    },
  ],
};
```

### 配置项说明

| 字段 | 类型 | 默认值 | 说明 |
|------|------|--------|------|
| enabled | boolean | true | 是否启用 |
| showLunar | boolean | true | 显示农历 |
| showSolarTerms | boolean | true | 显示节气 |
| showHolidays | boolean | true | 显示节假日 |
| events | array | [] | 自定义事件 |
| countdowns | array | [] | 倒计时事件 |

## 农历功能

### 农历显示

智能日历会自动计算并显示农历日期：

- 农历月份（正月、二月等）
- 农历日期（初一、初二等）

### 农历算法

组件使用简化的农历算法，可以准确显示大部分日期的农历。

## 节气功能

### 二十四节气

组件会显示当天的节气：

- 立春、雨水、惊蛰、春分
- 清明、谷雨、立夏、小满
- 芒种、夏至、小暑、大暑
- 立秋、处暑、白露、秋分
- 寒露、霜降、立冬、小雪
- 大雪、冬至、小寒、大寒

### 节气算法

节气日期基于天文算法计算，可以准确显示每个节气的日期。

## 节假日功能

### 内置节假日

组件内置了以下节假日：

| 日期 | 节日 |
|------|------|
| 01-01 | 元旦 |
| 02-14 | 情人节 |
| 05-01 | 劳动节 |
| 06-01 | 儿童节 |
| 10-01 | 国庆节 |
| 12-25 | 圣诞节 |

### 自定义节假日

你可以添加自己的节假日：

```typescript
events: [
  { date: '03-08', name: '妇女节', type: 'festival' },
  { date: '09-10', name: '教师节', type: 'festival' },
  { date: '11-11', name: '双十一', type: 'festival' },
]
```

## 倒计时功能

### 添加倒计时

```typescript
countdowns: [
  {
    id: 'birthday',
    title: '生日倒计时',
    targetDate: '2025-06-15T00:00:00',
    icon: 'fa-birthday-cake',
  },
]
```

### 自动新年倒计时

组件会自动计算下一个新年的日期，无需手动设置。

### 倒计时显示

倒计时会显示：
- 天
- 时
- 分
- 秒

## 自定义样式

### 修改日历大小

```css
.smart-calendar-widget {
  font-size: 0.9rem;
}
```

### 修改今日高亮

```css
.day-cell.today {
  background: var(--primary);
  color: #fff;
}
```

### 修改节气样式

```css
.solar-term {
  background: linear-gradient(135deg, rgba(50, 115, 220, 0.15), rgba(50, 115, 220, 0.05));
  color: var(--primary);
}
```

## 故障排查

### 农历不显示

检查 `showLunar` 是否为 `true`。

### 节气不显示

检查 `showSolarTerms` 是否为 `true`。

### 倒计时不显示

检查 `countdowns` 是否配置正确。

## 最佳实践

### 选择合适的显示内容

| 博客类型 | 推荐显示 |
|---------|---------|
| 个人博客 | 全部 |
| 技术博客 | 公历 + 倒计时 |
| 文化博客 | 全部 |

### 合理设置倒计时

- 不要设置过多的倒计时
- 选择有意义的日期
- 定期更新倒计时

## 下一步

- 了解[一言组件](/blog/19-hitokoto-guide)
- 探索[其他组件](/blog/21-components-overview)
- 学习[组件开发](/blog/11-plugin-development)
