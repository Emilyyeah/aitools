+++
title = "开发者 API 接入指南"
date = 2026-05-31
draft = false
description = "一行代码接入ChatGPT/Claude/Gemini API。国内中转平台对比、接入方式、费用参考。"
+++

## 你是哪种开发者

- 想做 AI 应用，需要调用 ChatGPT/Claude API → 看**方案一**
- 已经在用 OpenAI 官方 API，但国内连不上 → 看**方案二**
- 想用 Claude Code 命令行编程 → 看**方案三**

---

## 方案一：国内 API 中转平台

**原理**：平台在国内部署了一个兼容 OpenAI 接口格式的端点。你只需要把代码里的 `base_url` 从 `api.openai.com` 改成中转平台的地址。

**接入步骤**：

1. 注册一个 API 中转平台（搜索「API 中转」「OpenAI API 国内」）
2. 获取 API Key
3. 在你的代码里改一行：

```python
# 原来
client = OpenAI(api_key="sk-xxx")

# 改成
client = OpenAI(
    api_key="你的中转平台key",
    base_url="https://中转平台地址/v1"
)
```

4. 其余代码完全不变。所有 `chat.completions.create()` 调用自动走国内节点。

**2026 年 API 中转市场**：

赛道非常繁荣，多家平台竞争。主流包括：OpenRouter、诗云 API、4ksAPI、CatRouter 等，以及各大云厂商（七牛云、阿里云等）的 AI 代理服务。

**选平台的标准**：
- 支持的模型数量和更新速度（新模型出来多久能接入）
- API 延迟（国内节点通常在 200-500ms）
- 价格（通常比官方略高 10-30%，包含中转成本）
- SLA 保障（99.9%+ 可用性的优先）
- 是否支持流式输出（streaming）

**费用参考**：

| 模型 | 官方价格（/1M token） | 中转价格（/1M token） |
|:---|:---|:---|
| GPT-4o | 输入 $2.5 / 输出 $10 | 约上浮 10-30% |
| GPT-4o mini | 输入 $0.15 / 输出 $0.6 | 约上浮 10-30% |
| Claude Opus 4.5 | 输入 $15 / 输出 $75 | 约上浮 10-30% |
| Gemini Flash | 免费 | 免费 |

注册通常送 ¥5-10 体验金，够你测试几千次调用。

---

## 方案二：官方 API + 代理

如果你已经在用 OpenAI/Anthropic 官方 API，只是网络不通，可以：

1. 在服务器端设置 HTTP 代理（指向你的境外服务器或代理服务）
2. 在代码里配置 `http_client` 使用代理

```python
import httpx

client = OpenAI(
    api_key="sk-xxx",
    http_client=httpx.Client(proxy="http://你的代理地址:端口")
)
```

**前提**：你需要有一台境外服务器或稳定代理。适合已有基础设施的开发者。

---

## 方案三：Claude Code（开发者特供）

Anthropic 推出的命令行 AI 编程工具，在终端里直接跟 Claude 结对编程。

**安装**：

```bash
npm install -g @anthropic-ai/claude-code
```

**国内使用**：
- 需要通过 API 中转平台获取 Claude API Key
- 设置环境变量 `ANTHROPIC_BASE_URL` 指向中转地址
- 或直接使用国内的替代工具/聚合平台

👉 更多细节见 [Claude 开发者指南](/aitools/posts/claude-dev/)

---

## 方式选型

| | 中转平台 | 官方+代理 | Claude Code |
|:---|:---|:---|:---|
| 门槛 | 低 | 中（需自建代理） | 低 |
| 延迟 | 200-500ms | 取决于代理 | 取决于中转 |
| 成本 | 官方价+10-30% | 官方价+代理成本 | 中转平台价格 |
| 隐私 | 平台能看到请求 | 自己掌控 | 平台能看到请求 |
| 适合 | 大多数开发者 | 有基础设施的 | 写代码的 |

**建议**：先注册一个中转平台用免费体验金测试，满意了再正式接入。不急着付费。

<div class="cross-links">

### 你可能还想看

* [Claude 开发者指南](/aitools/posts/claude-dev/)
* [GPT Image 2 API 接入](/aitools/posts/gpt-image2-api/)

</div>
