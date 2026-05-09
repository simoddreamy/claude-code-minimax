# Claude Code MiniMax 中文版

> 让 Claude Code 使用 MiniMax API 工作

![Preview](preview.png)

## 功能特性

- 🚀 **完整 Claude Code 功能** - 终端交互、文件系统操作、Git 集成
- 🔄 **MiniMax API 支持** - 使用 MiniMax 的 `https://api.minimaxi.com/anthropic` 端点
- 💰 **成本优化** - 利用 MiniMax Token Plan 使用 Claude Code
- ⚡ **快速上手** - 设置环境变量即可运行

## 快速开始

### 前置要求

- Bun 1.3.5 或更高版本
- Node.js 24 或更高版本
- MiniMax API Key

### 安装

```bash
git clone https://github.com/simoddreamy/claude-code-minimax.git
cd claude-code-minimax
bun install
```

### 配置

设置环境变量：

```bash
export ANTHROPIC_BASE_URL="https://api.minimaxi.com/anthropic"
export ANTHROPIC_API_KEY="你的MiniMax_API密钥"
export ANTHROPIC_MODEL="MiniMax-M2.7"
export CLAUDE_NO_LOGIN=1
```

### 运行

```bash
bun run dev
```

首次运行时会提示选择颜色主题，完成后即可正常对话。

## MiniMax MCP 配置（可选）

如需使用 MiniMax MCP 工具（网络搜索、图片理解），可在 `.claude.json` 中配置：

```bash
cp .claude.json.example .claude.json
# 编辑 .claude.json，将 YOUR_MINIMAX_API_KEY 替换为你的密钥
```

## MiniMax 模型

| 模型 | 上下文窗口 | 最大输出 |
|------|-----------|----------|
| MiniMax-M2.7 | 200,000 | 8,192 |
| MiniMax-M2.5 | 200,000 | 8,192 |
| MiniMax-M2.1 | 200,000 | 8,192 |

## 环境变量

| 变量 | 说明 | 必需 |
|------|------|------|
| `ANTHROPIC_BASE_URL` | MiniMax API 端点: `https://api.minimaxi.com/anthropic` | 是 |
| `ANTHROPIC_API_KEY` | 你的 MiniMax API 密钥 | 是 |
| `ANTHROPIC_MODEL` | 使用的模型 (如 `MiniMax-M2.7`) | 否（默认最佳可用）|
| `CLAUDE_NO_LOGIN` | 设置为 `1` 跳过 OAuth 登录 | 是 |

## 已知问题

### Q: 运行时报 "Not logged in"？
A: 确保设置 `CLAUDE_NO_LOGIN=1` 环境变量。

### Q: 进程挂起不退出？
A: 使用交互模式运行（不带 `-p` 参数）：
```bash
bun run dev  # 不带 -p
```

## 项目结构

```
├── src/                    # 源代码
│   ├── bootstrap/          # 应用启动
│   ├── bridge/            # 桥接通信
│   ├── cli/               # CLI 处理器
│   ├── services/          # API 和分析服务
│   └── ...
├── shims/                 # 兼容性垫片
├── vendor/                # 第三方依赖
└── skills/                # Claude Code 技能
```

## 贡献

欢迎提交 Issue 和 Pull Request！

## 许可证

详见 [LICENSE.md](LICENSE.md)

## 致谢

- 原始 [Claude Code](https://github.com/anthropics/claude-code) by Anthropic
- [pengchengneo/Claude-Code](https://github.com/pengchengneo/Claude-Code) - 恢复的源码树
