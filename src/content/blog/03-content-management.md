---
title: "内容管理完全指南"
description: "学习如何高效管理你的博客内容，包括文章创建、编辑、分类、标签等完整操作指南"
pubDatetime: 2025-02-27T02:00:00
modDatetime: 2025-02-27T02:00:00
category: "教程"
tags: ["内容管理", "文章", "Markdown", "写作"]
toc: true
comment: true
---

# 内容管理完全指南

内容管理是博客运营的核心环节。Astro Icarus 主题提供了强大的内容管理功能，让你可以轻松地创建、编辑、组织和管理博客文章。本指南将详细介绍所有与内容管理相关的功能和最佳实践。

## 文章系统概述

### 文章存储结构

Astro Icarus 使用 Astro 的内容集合（Content Collections）功能来管理文章。所有文章都存储在 `src/content/blog/` 目录下，采用 Markdown 格式。

```
src/content/blog/
├── 2025-02-27-getting-started.md
├── 2025-02-27-theme-configuration.md
├── 2025-02-27-content-management.md
└── ...
```

### 文章命名规范

为了保持文章的有序管理，建议采用以下命名格式：

```
YYYY-MM-DD-article-slug.md
```

- **YYYY-MM-DD**: 文章发布日期
- **article-slug**: 文章的 URL 标识符，使用小写字母和连字符

例如：`2025-02-27-getting-started.md`

## 文章 Frontmatter

每篇文章的头部都需要包含 frontmatter 配置，用于定义文章的各种属性。

### 完整 Frontmatter 示例

```markdown
---
title: "文章标题"
description: "文章描述，用于 SEO 和列表展示"
pubDatetime: 2025-02-27T00:00:00
modDatetime: 2025-02-27T00:00:00
category: "分类名称"
tags: ["标签1", "标签2", "标签3"]
thumbnail: "/images/article-cover.jpg"
toc: true
comment: true
sticky: false
hidden: false
layout: "three-column"
showShare: true
showDonation: false
showSidebar: true
---
```

### Frontmatter 字段详解

#### 必填字段

**title** (string) - 文章标题
- 显示在文章页面和列表中
- 建议控制在 60 个字符以内
- 示例：`title: "如何搭建个人博客"`

**description** (string) - 文章描述
- 用于 SEO 和文章列表展示
- 建议控制在 160 个字符以内
- 示例：`description: "本文将详细介绍如何使用 Astro 搭建个人博客"`

**pubDatetime** (date) - 发布时间
- ISO 8601 格式
- 示例：`pubDatetime: 2025-02-27T00:00:00`

**category** (string) - 分类
- 文章所属的分类
- 示例：`category: "技术教程"`

#### 可选字段

**modDatetime** (date) - 修改时间
- 文章最后修改的时间
- 示例：`modDatetime: 2025-02-27T12:00:00`

**tags** (array) - 标签列表
- 文章的标签，用于内容组织和搜索
- 示例：`tags: ["Astro", "博客", "教程"]`

**thumbnail** (string) - 封面图
- 文章封面图片的路径
- 示例：`thumbnail: "/images/article-cover.jpg"`

**toc** (boolean) - 是否显示目录
- 默认值：`true`
- 控制是否在文章页面显示目录

**comment** (boolean) - 是否开启评论
- 默认值：`true`
- 控制是否显示评论区域

**sticky** (boolean) - 是否置顶
- 默认值：`false`
- 置顶文章会显示在列表最前面

**hidden** (boolean) - 是否隐藏
- 默认值：`false`
- 隐藏的文章不会显示在列表中，但可以通过 URL 访问

**layout** (string) - 布局类型
- 默认值：`"three-column"`
- 可选值：`"three-column"` | `"two-column"`
- 控制文章页面的布局

**showShare** (boolean) - 是否显示分享
- 默认值：`true`
- 控制是否显示分享按钮

**showDonation** (boolean) - 是否显示打赏
- 默认值：`false`
- 控制是否显示打赏区域

**showSidebar** (boolean) - 是否显示侧边栏
- 默认值：`true`
- 控制是否显示左侧边栏

## 创建文章

### 方法一：使用命令行脚本

我们提供了便捷的命令行脚本来创建文章：

```bash
pnpm new:post
```

运行后会提示你输入以下信息：
1. 文章标题
2. 文章描述（可选）
3. 分类（可选）
4. 标签（用逗号分隔，可选）

脚本会自动生成带有正确 frontmatter 的 Markdown 文件。

### 方法二：手动创建

你也可以直接在 `src/content/blog/` 目录下创建 Markdown 文件：

```markdown
---
title: "我的新文章"
description: "这是我的新文章描述"
pubDatetime: 2025-02-27T00:00:00
category: "随笔"
tags: ["生活", "思考"]
---

# 我的新文章

在这里开始撰写你的文章内容...

## 二级标题

正文内容

### 三级标题

更多内容
```

### 方法三：使用后端管理界面

如果你使用了我们提供的后端管理工具，可以通过图形界面创建文章：

1. 打开管理界面
2. 点击"新建文章"按钮
3. 填写文章信息
4. 在编辑器中撰写内容
5. 点击保存

## Markdown 语法

Astro Icarus 支持标准 Markdown 语法，以及扩展功能。

### 基础语法

**标题**
```markdown
# 一级标题
## 二级标题
### 三级标题
#### 四级标题
```

**段落和换行**
```markdown
这是一个段落。

这是另一个段落，中间需要空一行。
```

**强调**
```markdown
*斜体文本*
**粗体文本**
***粗斜体文本***
~~删除线文本~~
```

**列表**
```markdown
- 无序列表项 1
- 无序列表项 2
  - 嵌套列表项
  - 嵌套列表项

1. 有序列表项 1
2. 有序列表项 2
   1. 嵌套列表项
   2. 嵌套列表项
```

**链接和图片**
```markdown
[链接文本](https://example.com)
![图片描述](https://example.com/image.jpg)
```

**引用**
```markdown
> 这是一段引用文本。
> 可以有多行。
```

**代码**
```markdown
行内代码：`const x = 1`

代码块：
```javascript
function hello() {
  console.log('Hello, World!');
}
```
```

**表格**
```markdown
| 表头 1 | 表头 2 | 表头 3 |
|--------|--------|--------|
| 单元格 | 单元格 | 单元格 |
| 单元格 | 单元格 | 单元格 |
```

**分割线**
```markdown
---
```

### 扩展语法

**任务列表**
```markdown
- [x] 已完成任务
- [ ] 未完成任务
```

**脚注**
```markdown
这是一个带有脚注的句子[^1]。

[^1]: 这是脚注的内容。
```

**数学公式**
```markdown
行内公式：$E = mc^2$

块级公式：
$$
\sum_{i=1}^{n} x_i = x_1 + x_2 + \cdots + x_n
$$
```

## 分类和标签

### 分类管理

分类用于对文章进行大类的划分。每篇文章只能属于一个分类。

**创建分类**

分类不需要预先创建，直接在文章 frontmatter 中指定即可：

```markdown
---
category: "技术教程"
---
```

**分类页面**

主题会自动生成分类页面，访问 `/categories/分类名称/` 即可查看该分类下的所有文章。

### 标签管理

标签用于对文章进行更细粒度的标记。每篇文章可以有多个标签。

**添加标签**

在文章 frontmatter 中添加标签：

```markdown
---
tags: ["Astro", "博客", "教程", "前端"]
---
```

**标签页面**

访问 `/tags/标签名称/` 可以查看该标签下的所有文章。

## 文章置顶

### 设置置顶

在文章 frontmatter 中设置 `sticky: true`：

```markdown
---
title: "重要公告"
sticky: true
---
```

### 置顶效果

置顶文章会：
1. 显示在文章列表的最前面
2. 在首页显示"置顶"标识
3. 在文章页面显示"置顶"徽章

## 文章隐藏

### 设置隐藏

在文章 frontmatter 中设置 `hidden: true`：

```markdown
---
title: "草稿文章"
hidden: true
---
```

### 隐藏效果

隐藏文章会：
1. 不在文章列表中显示
2. 不在分类和标签页面中显示
3. 但可以通过直接访问 URL 查看

这适合用于发布尚未完成的文章，或者不想在列表中显示的文章。

## 文章布局

### 三栏布局

默认布局，左侧显示个人资料和目录，中间是文章内容，右侧是侧边栏。

```markdown
---
layout: "three-column"
---
```

### 两栏布局

隐藏右侧边栏，扩大文章内容区域。

```markdown
---
layout: "two-column"
---
```

## 最佳实践

### 文章写作建议

1. **标题要吸引人** - 好的标题能提高点击率
2. **描述要准确** - 描述会显示在搜索结果和社交媒体上
3. **使用合适的标签** - 标签有助于内容组织和搜索
4. **添加封面图** - 封面图能让文章在列表中更醒目
5. **保持更新** - 定期更新旧文章，保持内容新鲜

### SEO 优化

1. **使用关键词** - 在标题、描述和正文中合理使用关键词
2. **添加封面图** - 设置 `og:image` 提高社交媒体分享效果
3. **使用目录** - 启用 `toc: true` 提高用户体验
4. **优化 URL** - 使用简洁、有意义的 slug

### 内容组织

1. **合理分类** - 分类数量不宜过多，3-10 个为宜
2. **标签规范** - 建立标签规范，避免重复标签
3. **定期归档** - 定期整理旧文章，保持内容整洁

## 常见问题

### 文章不显示怎么办

1. 检查 `hidden` 是否为 `true`
2. 检查 `draft` 是否为 `true`
3. 检查 frontmatter 格式是否正确
4. 重新构建项目

### 如何修改文章 URL

修改文件名中的 slug 部分即可：

```
2025-02-27-old-slug.md → 2025-02-27-new-slug.md
```

### 如何删除文章

直接删除对应的 Markdown 文件，然后重新构建项目。

### 如何批量修改文章

可以使用文本编辑器的批量替换功能，或者编写脚本进行处理。

## 下一步

- 学习如何[自定义主题样式](/blog/04-customization)
- 配置[评论系统](/blog/05-comments)
- 了解[SEO 优化技巧](/blog/06-seo)
