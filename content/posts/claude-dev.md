+++
title = "Claude Code 安装配置指南"
date = 2026-05-31
draft = false
description = "国内直连 Claude Code。中转平台 API Key 配置、安装步骤、常见问题。"
+++

## Claude Code 是什么

Anthropic 推出的命令行 AI 编程工具——在终端里直接跟 Claude Opus 4.5 结对编程。能读取你的代码文件、执行命令、编辑文件。

---

## 安装

```bash
npm install -g @anthropic-ai/claude-code
```

---

## 国内直连配置

Claude Code 默认连 Anthropic 官方 API，国内需要走中转。两步：

### 1. 获取中转平台 API Key

- [OpenRouter](https://openrouter.ai)（400+模型，支持支付宝）
- [Ofox.ai](https://ofox.ai)（国内优化，中文文档）

注册后在后台生成 API Key。

### 2. 设置环境变量

```bash
# OpenRouter 示例
export ANTHROPIC_API_KEY="sk-or-v1-你的key"
export ANTHROPIC_BASE_URL="https://openrouter.ai/api/v1"

# Ofox.ai 示例
export ANTHROPIC_API_KEY="你的ofox key"
export ANTHROPIC_BASE_URL="https://api.ofox.ai/v1"
```

把这两行加到 `~/.zshrc` 或 `~/.bashrc` 里，以后每次启动终端自动生效。

---

## 启动

```bash
claude
```

第一次运行会有引导设置。之后在任意项目目录下运行，Claude Code 会自动感知项目结构。

---

## 常用场景

```bash
# 代码审查
"审查 src/ 目录的代码质量，列出潜在bug和安全隐患"

# 定位 Bug
"用户反馈登录后页面白屏，帮我定位原因"

# 写测试
"给 src/utils/format.ts 写完整的单元测试"

# 重构
"把这段代码从 class 组件重构为 hooks，保持功能不变"
```

---

## 费用

走中转平台按量计费：

| 模型 | 输入价格（/1M token） | 输出价格 |
|:---|:---|:---|
| Claude Opus 4.5 | ~$15 | ~$75 |
| Claude Sonnet 4 | ~$3 | ~$15 |

日常用 Sonnet 足够了，Opus 只在需要深度推理时用。一个月正常使用，Sonnet 花费约 $5-15。

想先免费体验 Claude？不用装 Claude Code。直接打开 [KULAAI](https://kulaai.cn)，在模型列表里切到 Claude 就能聊。

---

## 替代方案

如果你觉得配置环境麻烦：
- **Cursor**：付费版内置 Claude 模型，开箱即用
- **GitHub Copilot**：已支持选择 Claude 作为底层模型
- **聚合平台网页版**：[KULAAI](https://kulaai.cn) / [RskAi](https://rskai.cn) 直接切换 Claude 聊天
