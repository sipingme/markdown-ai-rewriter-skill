# Markdown AI Rewriter Skill

AI 驱动的 Markdown 内容重写工具，专为 Claw Hub 设计。

## 功能特性

- 🎨 **多种风格**：轻松、正式、技术、创意四种写作风格
- 🏗️ **保留结构**：保持标题、代码块、表格等结构完整
- 🤖 **多提供商**：支持 OpenAI 和 Anthropic
- 🔄 **Claw Hub 集成**：自动使用你配置的 API Key
- ⚡ **自动触发**：AI 自动识别何时使用此 Skill

## 前置要求

**必需**：OpenAI 或 Anthropic API Key

在 Claw Hub 中配置一次，所有 Skill 共享：

```bash
export OPENAI_API_KEY='sk-your-key-here'
# 或
export ANTHROPIC_API_KEY='sk-ant-your-key-here'
```

获取 API Key：
- OpenAI: https://platform.openai.com/api-keys
- Anthropic: https://console.anthropic.com/

## 安装

```bash
npm install -g markdown-ai-rewriter
```

## 快速开始

直接告诉 AI 你的需求：

```
用户："帮我重写这篇文章，用轻松的风格"
AI：自动触发 Skill → 执行重写 → 返回结果
```

## 使用方式

直接对 AI 说：
- "用轻松的风格重写这篇文章"
- "改成正式风格"
- "重写但保持结构不变"

## 完整文档

查看 [SKILL.md](./SKILL.md) 了解完整文档。

## 许可证

MIT
