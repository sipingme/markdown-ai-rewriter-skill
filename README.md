# Markdown AI Rewriter Skill

AI-powered Markdown content rewriter for Claw Hub.

## Features

- 🆓 **Free Tier**: 10 free rewrites per day using shared API key
- 🔑 **Bring Your Own Key**: Unlimited usage with your own OpenAI/Anthropic key
- 🎨 **Multiple Styles**: Casual, formal, technical, creative
- 🏗️ **Structure Preservation**: Keeps headings, code blocks, tables intact
- 🤖 **Multi-Provider**: OpenAI and Anthropic support

## Installation

```bash
npm install -g markdown-ai-rewriter
```

## Quick Start

### Option 1: Zero Configuration (Shared Key)

Use immediately without any setup:

```bash
markdown-ai-rewrite rewrite \
  --input article.md \
  --output rewritten.md \
  --provider openai \
  --style casual
```

Daily limit: 10 rewrites

### Option 2: Your Own Key (Unlimited)

Configure your API key for unlimited usage:

```bash
export OPENAI_API_KEY='sk-your-key-here'
```

## Usage with AI

Simply tell the AI:
- "Rewrite this article in a casual style"
- "Make this more formal"
- "Rewrite but keep the structure"

## Documentation

See [SKILL.md](./SKILL.md) for complete documentation.

## License

MIT
