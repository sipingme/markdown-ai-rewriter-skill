---
name: markdown-ai-rewriter
description: AI-powered Markdown content rewriter that preserves document structure
version: 0.1.0
author: Ping Si <sipingme@gmail.com>
user-invocable: true
requires:
  - node: ">=18.0.0"
  - npm: ">=8.0.0"
  - env:
      - OPENAI_API_KEY: "OpenAI API Key (可选，也可使用共享 Key)"
      - ANTHROPIC_API_KEY: "Anthropic API Key (可选)"
tags:
  - markdown
  - ai
  - rewriter
  - content
repository: https://github.com/sipingme/markdown-ai-rewriter
---

# Markdown AI Rewriter Skill

AI 驱动的 Markdown 内容重写工具 - 保持文档结构，智能改写内容。

## ⚡ 快速开始

### 安装

```bash
npm install -g markdown-ai-rewriter
```

### 零配置使用（共享 Key）

**无需配置 API Key，开箱即用！**

每天免费 10 次重写额度，适合快速体验和低频使用。

```bash
# 直接使用
markdown-ai-rewrite rewrite \
  --input article.md \
  --output article-rewritten.md \
  --provider openai \
  --style casual
```

### 配置自己的 Key（无限使用）

如果需要高频使用或超出每日限额，可配置自己的 API Key：

```bash
# 添加到 ~/.zshrc 或 ~/.bashrc
export OPENAI_API_KEY='sk-your-key-here'

# 或使用 Anthropic
export ANTHROPIC_API_KEY='sk-ant-your-key-here'
```

**获取 API Key**：
- OpenAI: https://platform.openai.com/api-keys
- Anthropic: https://console.anthropic.com/

---

## 🎯 何时使用此 Skill

当用户需要以下操作时，应触发此 Skill：

- ✅ 重写 Markdown 文章内容
- ✅ 改变文章写作风格（正式/轻松/技术/创意）
- ✅ 保持文章结构但改写表达
- ✅ 避免直接复制原文（洗稿）
- ✅ 将新闻风格转为博客风格

**触发关键词**：
- "重写这篇文章"
- "用轻松的风格改写"
- "把这个改成正式风格"
- "洗稿"
- "改写但保持结构"

---

## 📋 前置要求

### 1. 系统要求
- Node.js >= 18.0.0
- npm 或 pnpm 包管理器

### 2. API Key（可选）

**方案 A：使用共享 Key（推荐新手）**
- 无需配置
- 每天 10 次免费额度
- 适合快速体验

**方案 B：使用自己的 Key（推荐高频用户）**
- 需要注册 OpenAI 或 Anthropic 账号
- 无限制使用
- 成本自己控制

### 3. 安装 Skill

```bash
npm install -g markdown-ai-rewriter
```

---

## 🚀 标准操作流程 (SOP)

### 操作 1：使用共享 Key 重写（零配置）

**场景**：快速体验，无需配置

**步骤**：

1. 准备 Markdown 文件
2. 执行重写命令：

```bash
markdown-ai-rewrite rewrite \
  --input article.md \
  --output article-rewritten.md \
  --provider openai \
  --style casual \
  --verbose
```

**输出示例**：
```
ℹ️  Using shared API key (9 uses remaining today)
🚀 Starting rewrite with openai...
📄 Total blocks: 15
✍️  Rewritable blocks: 8
✅ [1/8] Rewritten paragraph
✅ [2/8] Rewritten paragraph
...
✅ Rewrite complete!
📊 Stats:
   - Total blocks: 15
   - Rewritten blocks: 8
   - Output: article-rewritten.md
```

**限额提示**：
```
❌ Error: Daily quota exceeded (10/10). 
Please configure your own API key:
export OPENAI_API_KEY='sk-...' or export ANTHROPIC_API_KEY='sk-ant-...'
```

---

### 操作 2：配置自己的 Key（无限使用）

**场景**：高频使用或超出每日限额

**步骤**：

1. 获取 API Key（选择一个）：
   - OpenAI: https://platform.openai.com/api-keys
   - Anthropic: https://console.anthropic.com/

2. 配置环境变量：

```bash
# 添加到 ~/.zshrc 或 ~/.bashrc
export OPENAI_API_KEY='sk-your-key-here'

# 重新加载配置
source ~/.zshrc
```

3. 使用（无限制）：

```bash
markdown-ai-rewrite rewrite \
  --input article.md \
  --output article-rewritten.md \
  --provider openai \
  --style formal
```

---

### 操作 3：不同写作风格

**可用风格**：

- **casual**（轻松）：口语化、亲切、像和朋友聊天
- **formal**（正式）：专业、严谨、适合商务场合
- **technical**（技术）：精确、专业术语、适合技术文档
- **creative**（创意）：生动、富有表现力、吸引眼球

**示例**：

```bash
# 轻松风格
markdown-ai-rewrite rewrite -i news.md -o blog.md -p openai -s casual

# 正式风格
markdown-ai-rewrite rewrite -i draft.md -o formal.md -p openai -s formal

# 技术风格
markdown-ai-rewrite rewrite -i doc.md -o tech.md -p openai -s technical
```

---

### 操作 4：自定义重写提示

**场景**：需要特定的重写要求

```bash
markdown-ai-rewrite rewrite \
  --input article.md \
  --output output.md \
  --provider openai \
  --style custom \
  --prompt "重写为面向小学生的科普文章，使用简单易懂的语言"
```

---

## 🔧 高级用法

### 编程 API

```javascript
const { MarkdownRewriter } = require('markdown-ai-rewriter');

const rewriter = new MarkdownRewriter({
  provider: 'openai',
  useSharedKey: true,  // 使用共享 Key
  dailyLimit: 10,      // 每日限额
  verbose: true,
  options: {
    style: 'casual',
    temperature: 0.7,
  },
});

const result = await rewriter.rewrite(markdown);
console.log(result.rewritten);
```

### 与其他工具配合

```bash
# 完整工作流：抓取 → 重写 → 发布
convert-url --url "https://news.com/article" --output article.md
markdown-ai-rewrite rewrite -i article.md -o rewritten.md -p openai -s casual
wechat-pub publish create --file rewritten.md --theme sports
```

---

## 📊 输入输出规范

### 输入格式

任何标准 Markdown 文件：

```markdown
# 标题

这是一段文字。

## 二级标题

- 列表项 1
- 列表项 2

> 引用内容

\`\`\`javascript
// 代码块会被保留
console.log('Hello');
\`\`\`
```

### 输出格式

**保留的元素**（不重写）：
- ❌ 标题（# ## ###）
- ❌ 代码块（```）
- ❌ 图片（![](...)）
- ❌ 表格
- ❌ 水平线（---）

**重写的元素**：
- ✅ 段落文本
- ✅ 引用内容（> ...）
- ✅ 列表项内容

---

## ⚠️ 常见问题和解决方案

### 问题 1：超出每日限额

**症状**：提示 "Daily quota exceeded (10/10)"

**解决**：配置自己的 API Key

```bash
export OPENAI_API_KEY='sk-your-key-here'
```

### 问题 2：API Key 无效

**症状**：提示 "API key required" 或 "Unauthorized"

**解决**：
1. 检查 Key 是否正确
2. 确认环境变量已设置：`echo $OPENAI_API_KEY`
3. 重新加载配置：`source ~/.zshrc`

### 问题 3：重写质量不满意

**解决**：
1. 尝试不同的风格（casual/formal/technical/creative）
2. 使用自定义 prompt
3. 调整 temperature（0.3-1.0）

---

## 💰 成本说明

### 使用共享 Key
- **完全免费**
- 每天 10 次限额
- 适合低频使用

### 使用自己的 Key

**OpenAI GPT-4o-mini**：
- 1000 字文章：~$0.01-0.02
- 月成本（每天 5 篇）：~$1.5-3

**Anthropic Claude 3.5 Sonnet**：
- 1000 字文章：~$0.05-0.10
- 月成本（每天 5 篇）：~$7.5-15

---

## 🎓 示例对话

**用户**：帮我重写这篇新闻文章，用轻松的风格

**AI**：好的，我来帮你重写。正在处理...

[执行命令]

**AI**：✅ 重写完成！
- 使用共享 API Key（剩余 9/10 次）
- 总共 15 个段落，重写了 8 个
- 输出文件：article-rewritten.md
- 风格：轻松口语化

你可以查看重写后的文件了！

---

## 📝 维护说明

- **版本**: 0.1.0
- **最后更新**: 2026-03-23
- **维护者**: Ping Si <sipingme@gmail.com>
- **许可证**: MIT

---

## 🔗 相关项目

- [news-to-markdown](https://github.com/sipingme/news-to-markdown) - 抓取新闻文章
- [wechat-md-publisher](https://github.com/sipingme/wechat-md-publisher) - 发布到微信公众号
