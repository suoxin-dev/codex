# Codex CLI 中文版 (汉化版)

这是 OpenAI Codex CLI 的中文汉化版本，基于 [openai/codex](https://github.com/openai/codex) fork。

## 汉化内容

| 模块 | 汉化范围 |
|------|---------|
| TUI 斜杠命令 | `/help`、`/model`、`/review` 等 30+ 条命令描述 |
| TUI 欢迎界面 | 欢迎信息、引导流程 |
| TUI 快捷键 | 回车、空格、翻页等键名 |
| TUI 状态栏 | 模式标签、目标状态、队列提示 |
| TUI 更新提示 | 新版本提示、更新操作 |
| TUI 工具提示 | 新功能提示文案 |
| CLI 登录 | 登录/登出、API 密钥相关提示 |
| CLI 启动错误 | 错误信息 |

## 编译安装

### 前提条件

1. 安装 [Rust](https://rustup.rs/)：
   ```bash
   curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
   source ~/.cargo/env
   ```

2. 安装系统依赖（macOS）：
   ```bash
   xcode-select --install
   ```

### 编译步骤

```bash
# 1. 克隆汉化版仓库
git clone https://github.com/suoxin-dev/codex.git
cd codex

# 2. 进入 Rust 项目目录
cd codex-rs

# 3. 编译 release 版本（首次编译需要 10-30 分钟）
cargo build --release -p codex-cli

# 4. 找到编译产物
ls -la target/release/codex
```

### 替换现有安装

```bash
# 备份原文件
cp ~/.npm-global/lib/node_modules/@openai/codex/node_modules/@openai/codex-darwin-x64/vendor/x86_64-apple-darwin/bin/codex \
   ~/.npm-global/lib/node_modules/@openai/codex/node_modules/@openai/codex-darwin-x64/vendor/x86_64-apple-darwin/bin/codex.bak

# 替换为汉化版
cp codex-rs/target/release/codex \
   ~/.npm-global/lib/node_modules/@openai/codex/node_modules/@openai/codex-darwin-x64/vendor/x86_64-apple-darwin/bin/codex

# 验证
codex --version
```

## 注意事项

- 汉化仅修改了用户可见的 UI 文本，不影响程序逻辑
- `npm update` 会覆盖汉化版二进制，需重新替换
- 命令名称（如 /help、/model）保持英文，只汉化了描述文字

## 许可证

与原项目一致：Apache-2.0
