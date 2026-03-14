---
title: "常见问题 FAQ"
description: "Astro Icarus 主题常见问题解答"
pubDatetime: 2025-02-27T17:00:00
modDatetime: 2025-02-27T17:00:00
category: "参考"
tags: ["FAQ", "问题", "解答", "帮助"]
toc: true
comment: true
---

# 常见问题 FAQ

本文档收集了 Astro Icarus 主题的常见问题及其解答。

## 安装问题

### Q: 安装依赖时出错怎么办？

**A:** 尝试以下步骤：

```bash
# 清除缓存
rm -rf node_modules pnpm-lock.yaml

# 重新安装
pnpm install
```

### Q: 需要哪个 Node.js 版本？

**A:** 需要 Node.js 18 或更高版本。

```bash
# 检查版本
node -v

# 升级版本
nvm install 20
nvm use 20
```

## 构建问题

### Q: 构建失败怎么办？

**A:** 检查以下几点：

1. 依赖是否安装完整
2. Node.js 版本是否符合要求
3. 配置文件语法是否正确

### Q: 构建成功但页面空白？

**A:** 检查 `base` 配置是否正确：

```javascript
// astro.config.mjs
export default defineConfig({
  base: '/',  // 确保正确
});
```

## 文章问题

### Q: 文章不显示怎么办？

**A:** 检查以下几点：

1. 文件是否在 `src/content/blog/` 目录
2. `hidden` 是否为 `true`
3. `draft` 是否为 `true`
4. frontmatter 格式是否正确

### Q: 如何置顶文章？

**A:** 在 frontmatter 中设置：

```markdown
---
sticky: true
---
```

### Q: 如何隐藏文章？

**A:** 在 frontmatter 中设置：

```markdown
---
hidden: true
---
```

## 样式问题

### Q: 暗色模式不生效？

**A:** 检查 CSS 变量定义：

```css
[data-theme="dark"] {
  --bg: #0d1117;
  --card-bg: #161b22;
}
```

### Q: 自定义样式不生效？

**A:** 检查选择器是否正确，或尝试增加特异性：

```css
/* 增加特异性 */
body .my-component {
  color: red;
}
```

## 评论问题

### Q: 评论不显示？

**A:** 检查以下几点：

1. 评论配置是否正确
2. 评论服务是否可用
3. 网络连接是否正常

### Q: 如何禁用评论？

**A:** 在 frontmatter 中设置：

```markdown
---
comment: false
---
```

## 部署问题

### Q: 部署到 Cloudflare Pages？

**A:** 参考[部署指南](/blog/07-deployment)。

### Q: 如何绑定自定义域名？

**A:** 在 Cloudflare Pages 设置中添加自定义域名。

### Q: 404 错误怎么办？

**A:** 配置重定向规则：

```
/* /index.html 200
```

## 性能问题

### Q: 页面加载慢？

**A:** 尝试以下优化：

1. 压缩图片
2. 启用缓存
3. 使用 CDN

### Q: 如何提高 Lighthouse 评分？

**A:** 参考[性能优化指南](/blog/09-performance)。

## 功能问题

### Q: 如何添加新页面？

**A:** 使用脚本创建：

```bash
pnpm new:page about --title="关于"
```

### Q: 如何修改导航链接？

**A:** 在 `src/config.ts` 中修改：

```typescript
export const NAV_LINKS = [
  { href: '/', label: '首页', icon: 'fa-home' },
];
```

### Q: 如何添加自定义组件？

**A:** 参考[插件开发指南](/blog/11-plugin-development)。

## 升级问题

### Q: 如何升级主题？

**A:** 参考[版本升级指南](/blog/13-upgrade)。

### Q: 升级后出现问题？

**A:** 检查更新日志中的破坏性变更，并相应修改配置。

## 其他问题

### Q: 如何获取帮助？

**A:** 可以通过以下方式获取帮助：

1. 查看文档
2. 搜索 Issues
3. 提交 Issue
4. 发送邮件

### Q: 如何贡献代码？

**A:** 参考[贡献指南](/blog/16-contributing)。

### Q: 主题使用什么许可证？

**A:** MIT 许可证。

## 没有找到答案？

如果以上没有解答你的问题，可以：

1. [提交 Issue](https://github.com/Xuzx-Ricky/astro-icarus/issues)
2. 发送邮件到 your-email@example.com
