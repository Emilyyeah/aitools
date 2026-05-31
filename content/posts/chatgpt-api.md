+++
title = "开发者：ChatGPT API 怎么接"
date = 2026-05-31
draft = false
description = "API中转方案。一行代码切换，国内直连，按量计费。"
+++

## API 中转是什么

你在国内的服务器无法直连 `api.openai.com`。中转平台在国内部署一个兼容 OpenAI 接口的端点，帮你转发请求。

## 怎么用

代码里改一行：

```
# 原来
client = OpenAI(api_key="sk-xxx")

# 改成
client = OpenAI(
    api_key="your-key",
    base_url="https://your-relay.com/v1"  # 中转平台地址
)
```

其他代码不变。

## 怎么选中转平台

- 看 SLA 保障（99.9%+ 优先）
- 看支持的模型范围（GPT-4o、o3 等最新模型）
- 看计费是否透明（按 token，不要有隐藏费用）
- 看有没有免费额度可以测试

## 2026 年现状

中转赛道非常繁荣，多家竞争。主流平台提供 99.99% SLA、400+ 模型、按量计费。价格透明，普遍低于官方直连。

<div class="cross-links">

### 你可能还想看

* [从零开始用上ChatGPT](/aitools/posts/chatgpt-beginner/)
* [Claude 开发者方案](/aitools/posts/claude-dev/)

</div>
