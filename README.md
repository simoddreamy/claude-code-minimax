# Claude Code MiniMax

> **中文文档**: [README_CN.md](README_CN.md)

![Preview](preview.png)

A MiniMax-adapted fork of Anthropic's Claude Code, enabling the use of MiniMax's Anthropic-compatible API with all Claude Code features.

## Features

- 🚀 **Full Claude Code functionality** - Terminal interaction, filesystem operations, git integration
- 🔄 **MiniMax API support** - Uses MiniMax's `https://api.minimaxi.com/anthropic` endpoint
- 💰 **Cost-effective** - Leverage MiniMax's token plan for Claude Code usage
- ⚡ **Easy setup** - Just set environment variables and run

## Quick Start

### Prerequisites

- Bun 1.3.5 or newer
- Node.js 24 or newer
- MiniMax API key

### Installation

```bash
git clone https://github.com/simoddreamy/claude-code-minimax.git
cd claude-code-minimax
bun install
```

### Configuration

Set your MiniMax API credentials:

```bash
export ANTHROPIC_BASE_URL=https://api.minimaxi.com/anthropic
export ANTHROPIC_API_KEY=your_minimax_api_key
export ANTHROPIC_MODEL=MiniMax-M2.7  # or MiniMax-M2.5, MiniMax-M2.1
```

### Run

```bash
bun run dev
```

Or inline:

```bash
ANTHROPIC_BASE_URL=https://api.minimaxi.com/anthropic \
ANTHROPIC_API_KEY=your_api_key \
ANTHROPIC_MODEL=MiniMax-M2.7 \
bun run dev
```

## Environment Variables

| Variable | Description | Required |
|----------|-------------|----------|
| `ANTHROPIC_BASE_URL` | MiniMax API endpoint: `https://api.minimaxi.com/anthropic` | Yes |
| `ANTHROPIC_API_KEY` | Your MiniMax API key | Yes |
| `ANTHROPIC_MODEL` | Model to use (e.g., `MiniMax-M2.7`) | No (defaults to best available) |

## MiniMax Models

| Model | Context Window | Max Output |
|-------|---------------|------------|
| MiniMax-M2.7 | 200,000 | 8,192 |
| MiniMax-M2.5 | 200,000 | 8,192 |
| MiniMax-M2.1 | 200,000 | 8,192 |

## Project Structure

```
├── src/                    # Source code
│   ├── bootstrap/          # Application bootstrap
│   ├── bridge/            # Bridge communication
│   ├── cli/               # CLI handlers
│   ├── services/          # API and analytics services
│   └── ...
├── shims/                 # Compatibility shims
├── vendor/                # Third-party dependencies
└── skills/                # Claude Code skills
```

## Credits

- Original [Claude Code](https://github.com/anthropics/claude-code) by Anthropic
- [pengchengneo/Claude-Code](https://github.com/pengchengneo/Claude-Code) - Restored source tree
- MiniMax API support via third-party API compatibility layer

## License

See [LICENSE.md](LICENSE.md) for details.
