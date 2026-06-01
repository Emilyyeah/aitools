+++
title = "开发者 API 接入指南"
date = 2026-05-31
draft = false
description = "一行代码接入ChatGPT/Claude/Gemini API。OpenRouter、Ofox.ai等中转平台对比，附代码示例。"
+++

## 你是哪种开发者

- 想做 AI 应用，需要调用 ChatGPT/Claude API → 看**方案一**
- 已经在用 OpenAI 官方 API，但国内连不上 → 看**方案二**
- 想用 Claude Code 命令行编程 → 看**方案三**

---

## 方案一：国内 API 中转平台

**原理**：平台在国内部署兼容 OpenAI 接口的端点。你改一行 `base_url`，其余代码不变。

### 主流中转平台

**OpenRouter**

- 覆盖模型最多（400+），ChatGPT + Claude + Gemini + 开源模型全有
- 统一 API 格式，切换模型不用改代码
- 按量计费，价格透明
- 适合：需要接入多个模型的开发者

**Ofox.ai**

- 专为国内开发者优化，中文文档完善
- 延迟低，国内节点响应快
- 价格有竞争力
- 适合：国内开发者快速上手

**openairouter.net**

- 收录 77+ 个中转服务商的导航站
- 可以按价格、模型、标签筛选
- 适合：想对比价格后再选的开发者

### 代码示例

```python
from openai import OpenAI

client = OpenAI(
    api_key="你的中转平台key",
    base_url="https://中转平台地址/v1"
)

response = client.chat.completions.create(
    model="gpt-4o",
    messages=[{"role": "user", "content": "你好"}]
)
print(response.choices[0].message.content)
```

切换到 Claude：

```python
response = client.chat.completions.create(
    model="claude-opus-4-5-20251101",
    messages=[{"role": "user", "content": "Hello"}]
)
```

### 费用参考

| 模型 | 官方价格（/1M token） | 中转约 |
|:---|:---|:---|
| GPT-4o | $2.5 / $10 | 上浮 10-30% |
| GPT-4o mini | $0.15 / $0.6 | 上浮 10-30% |
| Claude Opus 4.5 | $15 / $75 | 上浮 10-30% |
| Gemini Flash | 免费 | 免费 |

注册通常送 ¥5-10 体验金，够测试几次。

---

## 方案二：官方 API + 自建代理

如果你已经有境外服务器，可以用 HTTP 代理：

```python
import httpx

client = OpenAI(
    api_key="sk-xxx",
    http_client=httpx.Client(proxy="http://你的代理地址:端口")
)
```

**适合**：已有基础设施、对隐私要求高的开发者。

---

## 方案三：Claude Code

在终端里跟 Claude 结对编程。

```bash
npm install -g @anthropic-ai/claude-code
# 配置中转平台 API Key
export ANTHROPIC_API_KEY="你的中转平台key"
export ANTHROPIC_BASE_URL="https://中转平台地址"
claude
```

👉 详细配置见 [Claude 开发者指南](/aitools/posts/claude-dev/)

---

## 选型建议

| | OpenRouter | Ofox.ai | 自建代理 |
|:---|:---|:---|:---|
| 模型数量 | 🥇 400+ | 主流模型 | 看官方 |
| 延迟 | 200-500ms | 🥇 更低 | 取决于代理 |
| 门槛 | 低 | 低 | 中 |
| 成本 | 官方+10-30% | 官方+10-30% | 官方+代理成本 |
| 适合 | 多模型接入 | 国内快速上手 | 有基础设施的 |

**建议**：先注册 OpenRouter 或 Ofox.ai，用免费体验金测试，满意了再正式接入。

<div class="cross-links">

### 你可能还想看

* [Claude 开发者指南](/aitools/posts/claude-dev/)
* [GPT Image 2 API 接入](/aitools/posts/gpt-image2-api/)

</div>
