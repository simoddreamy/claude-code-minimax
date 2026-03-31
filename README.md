
# Restored Claude Code Source, Third-Party API Support

> **中文文档**: [README_CN.md](README_CN.md)

![Preview](preview.png)

This repository is a restored Claude Code source tree reconstructed primarily from source maps and missing-module backfilling.

It is not the original upstream repository state. Some files were unrecoverable from source maps and have been replaced with compatibility shims or degraded implementations so the project can install and run again.

## Third-Party LLM API Support

This fork has been **modified to bypass Claude's preflight checks**, enabling the use of third-party large language model APIs that are compatible with the Anthropic API format.

You can use any Anthropic-compatible API endpoint by setting the following environment variables:

```bash
ANTHROPIC_BASE_URL=https://api.minimaxi.com/anthropic \
ANTHROPIC_API_KEY=YOUR_API_KEY \
ANTHROPIC_MODEL=MiniMax-M2.7 \
bun run dev
```

| Variable | Description |
|---|---|
| `ANTHROPIC_BASE_URL` | Base URL of the third-party Anthropic-compatible API |
| `ANTHROPIC_API_KEY` | Your API key for the third-party service |
| `ANTHROPIC_MODEL` | Model name to use (e.g. `MiniMax-M2.7`) |

> **Note**: The preflight authentication check that normally requires a valid Anthropic account has been removed. Any API key accepted by your chosen endpoint will work.

## Current status

- The source tree is restorable and runnable in a local development workflow.
- `bun install` succeeds.
- `bun run version` succeeds.
- `bun run dev` now routes through the restored CLI bootstrap instead of the temporary `dev-entry` shim.
- `bun run dev --help` shows the full command tree from the restored CLI.
- A number of modules still contain restoration-time fallbacks, so behavior may differ from the original Claude Code implementation.

## Restored so far

Recent restoration work has recovered several pieces beyond the initial source-map import:

- the default Bun scripts now start the real CLI bootstrap path
- bundled skill content for `claude-api` and `verify` has been rewritten from placeholder files into usable reference docs
- compatibility layers for Chrome MCP and Computer Use MCP now expose realistic tool catalogs and structured degraded-mode responses instead of empty stubs
- several explicit placeholder resources have been replaced with working fallback prompts for planning and permission-classifier flows

Remaining gaps are mostly private/native integrations where the original implementation was not recoverable from source maps, so those areas still rely on shims or reduced behavior.

## Why this exists

Source maps do not contain a full original repository:

- type-only files are often missing
- build-time generated files may be absent
- private package wrappers and native bindings may not be recoverable
- dynamic imports and resource files are frequently incomplete

This repository fills those gaps enough to produce a usable, runnable restored workspace.

## Run

Requirements:

- Bun 1.3.5 or newer
- Node.js 24 or newer

Install dependencies:

```bash
bun install
```

Run with a third-party API (recommended):

```bash
ANTHROPIC_BASE_URL=https://api.minimaxi.com/anthropic \
ANTHROPIC_API_KEY=YOUR_API_KEY \
ANTHROPIC_MODEL=MiniMax-M2.7 \
bun run dev
```

Or run the restored CLI directly:

```bash
bun run dev
```

Print the restored version:

```bash
bun run version
```
