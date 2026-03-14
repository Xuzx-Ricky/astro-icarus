---
title: "贡献指南"
description: "如何为 Astro Icarus 主题做出贡献"
pubDatetime: 2025-02-27T15:00:00
modDatetime: 2025-02-27T15:00:00
category: "参考"
tags: ["贡献", "开源", "GitHub", "协作"]
toc: true
comment: true
---

# 贡献指南

感谢你对 Astro Icarus 主题的兴趣！我们欢迎各种形式的贡献，包括代码、文档、设计等。

## 贡献方式

### 1. 提交 Issue

如果你发现了 bug 或有新功能建议，可以提交 Issue。

**提交前检查**

- [ ] 搜索现有 Issue，避免重复
- [ ] 使用 Issue 模板
- [ ] 提供详细信息

**Issue 类型**

| 类型 | 说明 |
|------|------|
| Bug Report | 报告问题 |
| Feature Request | 功能建议 |
| Documentation | 文档问题 |
| Question | 提问 |

### 2. 提交 Pull Request

如果你有代码贡献，可以提交 Pull Request。

**贡献流程**

1. Fork 仓库
2. 创建分支
3. 提交更改
4. 创建 PR

**PR 规范**

- 使用清晰的标题
- 描述更改内容
- 关联相关 Issue
- 确保测试通过

### 3. 改进文档

文档贡献同样重要：

- 修复文档错误
- 添加使用示例
- 翻译文档

### 4. 分享主题

帮助推广主题：

- 在社交媒体上分享
- 写文章介绍
- 推荐给朋友

## 开发环境

### 克隆仓库

```bash
# Fork 仓库后克隆
git clone https://github.com/your-username/astro-icarus.git
cd astro-icarus
```

### 安装依赖

```bash
pnpm install
```

### 启动开发服务器

```bash
pnpm dev
```

### 构建测试

```bash
pnpm build
```

## 代码规范

### 提交信息规范

使用 Conventional Commits 规范：

```
<type>(<scope>): <subject>

<body>

<footer>
```

**类型**

| 类型 | 说明 |
|------|------|
| feat | 新功能 |
| fix | Bug 修复 |
| docs | 文档 |
| style | 格式 |
| refactor | 重构 |
| perf | 性能优化 |
| test | 测试 |
| chore | 构建/工具 |

**示例**

```
feat(navbar): 添加搜索功能

- 在导航栏添加搜索图标
- 实现搜索弹窗
- 支持键盘快捷键

Closes #123
```

### 代码风格

- 使用 TypeScript
- 遵循 ESLint 规则
- 使用 Prettier 格式化

### 文件命名

| 类型 | 命名规范 |
|------|---------|
| 组件 | PascalCase |
| 工具函数 | camelCase |
| 常量 | UPPER_SNAKE_CASE |

## 测试

### 运行测试

```bash
# 运行所有测试
pnpm test

# 运行特定测试
pnpm test -- Navbar
```

### 测试覆盖率

```bash
pnpm test:coverage
```

### 编写测试

```typescript
import { test, expect } from 'vitest';
import { formatDate } from './helpers';

test('formatDate formats correctly', () => {
  const result = formatDate('2025-02-27');
  expect(result).toBe('2025年2月27日');
});
```

## 文档

### 文档位置

- `README.md` - 项目介绍
- `docs/` - 详细文档
- `src/content/blog/` - 博客文章

### 文档规范

1. 使用 Markdown 格式
2. 提供代码示例
3. 保持更新

## 发布流程

### 版本号规则

使用语义化版本（SemVer）：

```
主版本号.次版本号.修订号
```

| 版本类型 | 说明 |
|---------|------|
| 主版本 | 破坏性变更 |
| 次版本 | 新功能 |
| 修订号 | Bug 修复 |

### 发布步骤

1. 更新版本号
2. 更新 CHANGELOG
3. 创建 Git 标签
4. 发布到 npm
5. 创建 GitHub Release

## 行为准则

### 我们的承诺

- 友好和包容
- 尊重不同观点
- 接受建设性批评
- 关注社区利益

### 不可接受的行为

- 歧视性语言
- 人身攻击
- 骚扰行为
- 泄露他人隐私

## 联系方式

- **GitHub Issues**: [提交 Issue](https://github.com/Xuzx-Ricky/astro-icarus/issues)
- **Email**: your-email@example.com

## 致谢

感谢所有贡献者！

## 许可证

本项目采用 MIT 许可证。
