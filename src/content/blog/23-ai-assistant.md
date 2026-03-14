---
title: "AI 助手组件使用指南"
description: "深入了解 Astro Icarus 主题的 AI 助手组件，包括文章摘要、翻译、推荐等功能"
pubDatetime: 2025-02-27T22:00:00
modDatetime: 2025-02-27T22:00:00
category: "组件"
tags: ["AI", "助手", "摘要", "翻译"]
toc: true
comment: true
---

# AI 助手组件使用指南

AI 助手组件是 Astro Icarus 主题的智能功能，提供文章摘要、翻译、推荐等功能。

## 功能概述

AI 助手组件提供以下功能：

1. **文章摘要** - 自动生成文章摘要
2. **翻译功能** - 翻译页面内容
3. **相关推荐** - 基于当前文章推荐相关内容

## 基本配置

### 启用 AI 助手

在 `src/config.ts` 中配置：

```typescript
export const AI_CONFIG = {
  enabled: true,
  provider: 'openai',
  apiKey: 'your-api-key',
  apiUrl: 'https://api.openai.com/v1',
  model: 'gpt-3.5-turbo',
  features: {
    summary: true,
    translation: true,
    recommendation: true,
    chat: false,
  },
};
```

### 配置项说明

| 字段 | 类型 | 默认值 | 说明 |
|------|------|--------|------|
| enabled | boolean | false | 是否启用 |
| provider | string | 'openai' | AI 提供商 |
| apiKey | string | '' | API 密钥 |
| apiUrl | string | '' | API 地址 |
| model | string | 'gpt-3.5-turbo' | 模型名称 |
| features | object | - | 功能开关 |

## 支持的 AI 提供商

### OpenAI

```typescript
export const AI_CONFIG = {
  provider: 'openai',
  apiKey: 'sk-xxx',
  apiUrl: 'https://api.openai.com/v1',
  model: 'gpt-3.5-turbo',
};
```

### 英伟达 NIM

```typescript
export const AI_CONFIG = {
  provider: 'openai',
  apiKey: 'nvapi-xxx',
  apiUrl: 'https://integrate.api.nvidia.com/v1',
  model: 'meta/llama3-70b-instruct',
};
```

### 其他 OpenAI 兼容 API

```typescript
export const AI_CONFIG = {
  provider: 'openai',
  apiKey: 'your-api-key',
  apiUrl: 'https://your-api-endpoint.com/v1',
  model: 'your-model',
};
```

## 功能详解

### 文章摘要

自动生成文章摘要，帮助读者快速了解文章内容。

**使用方法**

1. 打开 AI 助手
2. 点击"生成摘要"按钮
3. 查看生成的摘要

**配置**

```typescript
export const AI_CONFIG = {
  features: {
    summary: true,
  },
  summary: {
    maxLength: 200,
    autoGenerate: false,
  },
};
```

### 翻译功能

翻译页面内容到不同语言。

**使用方法**

1. 打开 AI 助手
2. 选择目标语言
3. 点击"翻译页面"按钮

**支持语言**

- 中文
- 英文
- 日文
- 韩文
- 法文
- 德文

### 相关推荐

基于当前文章推荐相关内容。

**使用方法**

1. 打开 AI 助手
2. 查看"相关推荐"区域

## 使用技巧

### 快捷键

点击页面右下角的 AI 助手按钮打开对话框。

### 隐私保护

AI 助手不会上传敏感信息，只发送文章内容用于生成摘要。

## 故障排查

### AI 助手不显示

检查 `enabled` 是否为 `true`。

### 摘要生成失败

1. 检查 API 密钥是否正确
2. 检查 API 地址是否可访问
3. 检查网络连接

### 翻译失败

1. 检查 API 密钥
2. 检查目标语言是否支持

## 最佳实践

### 选择合适的模型

| 场景 | 推荐模型 |
|------|---------|
| 摘要生成 | gpt-3.5-turbo |
| 翻译 | gpt-3.5-turbo |
| 高级功能 | gpt-4 |

### 控制成本

1. 限制摘要长度
2. 关闭自动生成功能
3. 选择合适的模型

## 下一步

- 了解[组件概览](/blog/21-components-overview)
- 学习[组件开发](/blog/11-plugin-development)
- 查看[故障排查](/blog/12-troubleshooting)
