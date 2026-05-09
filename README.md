# Claude Code MiniMax

> **中文文档**: [README_CN.md](README_CN.md)

![Preview](preview.png)

A MiniMax-adapted fork of Anthropic's Claude Code, enabling the use of MiniMax's Anthropic-compatible API with all Claude Code features.

## Features

- 🚀 **Full Claude Code functionality** - Terminal interaction, filesystem operations, git integration
- 🔄 **MiniMax API support** - Uses MiniMax's `https://api.minimaxi.com/anthropic` endpoint
- 💰 **Cost-effective** - Leverage MiniMax's token plan for Claude Code usage
- ⚡ **Easy setup** - Just set environment variables and run
- ✅ **Automatic provider detection** - MiniMax is automatically detected, no login required

## Quick Start

### Prerequisites

- Bun 1.3.5 or newer (or Node.js 24+)
- MiniMax API key

### Installation

```bash
git clone https://github.com/simoddreamy/claude-code-minimax.git
cd claude-code-minimax
bun install
```

### Configuration

Set your MiniMax API credentials as environment variables:

```bash
export ANTHROPIC_BASE_URL="https://api.minimaxi.com/anthropic"
export ANTHROPIC_API_KEY="your_minimax_api_key"
export ANTHROPIC_MODEL="MiniMax-M2.7"  # or MiniMax-M2.5, MiniMax-M2.1
export CLAUDE_NO_LOGIN=1  # Skip Anthropic login (required for MiniMax)
```

### Run

#### Interactive Mode

```bash
bun run dev
```

#### Non-Interactive / Script Mode

For use in scripts or CI/CD pipelines, use the `-p` flag:

```bash
bun run dev -- -p "Your prompt here" < /dev/null
```

Or inline all environment variables:

```bash
ANTHROPIC_BASE_URL="https://api.minimaxi.com/anthropic" \
ANTHROPIC_API_KEY="your_api_key" \
ANTHROPIC_MODEL="MiniMax-M2.7" \
CLAUDE_NO_LOGIN=1 \
bun run dev -- -p "say hello" < /dev/null
```

## Environment Variables

| Variable | Description | Required |
|----------|-------------|----------|
| `ANTHROPIC_BASE_URL` | MiniMax API endpoint: `https://api.minimaxi.com/anthropic` | Yes |
| `ANTHROPIC_API_KEY` | Your MiniMax API key | Yes |
| `ANTHROPIC_MODEL` | Model to use (e.g., `MiniMax-M2.7`) | No (defaults to best available) |
| `CLAUDE_NO_LOGIN` | Set to `1` to skip Anthropic login prompt | Yes (for MiniMax) |

## MiniMax Models

| Model | Context Window | Max Output |
|-------|---------------|------------|
| MiniMax-M2.7 | 200,000 | 8,192 |
| MiniMax-M2.5 | 200,000 | 8,192 |
| MiniMax-M2.1 | 200,000 | 8,192 |

## Troubleshooting

### Login Prompt Appears

If you're prompted to login to Anthropic, make sure you've set:
- `ANTHROPIC_BASE_URL` to MiniMax endpoint
- `CLAUDE_NO_LOGIN=1`

### "API Error" or Connection Issues

1. Verify your MiniMax API key is correct
2. Check that `ANTHROPIC_BASE_URL` is set to `https://api.minimaxi.com/anthropic` (not the older `api.minimax.chat`)
3. Ensure your MiniMax account has API access enabled

### Interactive Mode Hangs

For non-interactive usage, always use the `-p` flag with stdin redirected:

```bash
claude -p "prompt" < /dev/null
```

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
