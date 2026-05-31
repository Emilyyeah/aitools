+++
title = "Gemini 国内使用指南"
date = 2026-05-26
draft = false
description = "Google的AI模型。免费额度最大方，原生多模态。不需要付费就能用。"
+++

## 先确认你的情况

<div class="self-check">

### 你想怎么用 Gemini？

* <span class="check">☐</span> 有 Google 账号 + 能连 Google → 看**方案A：官方渠道**
* <span class="check">☐</span> 不想注册 Google 账号 → 看**方案B：聚合平台**
* <span class="check">☐</span> 开发者，需要 API → 看**方案C：API接入**

</div>

---

## Gemini 独特优势

1. **免费额度最大方**：Gemini Flash API 每分钟60次免费，比其他平台都慷慨
2. **多模态原生**：直接处理图片、音频、视频，不需要额外插件
3. **100万token上下文**：一次能塞进整本书
4. **Google 生态集成**：和 Gmail、Docs、Maps 连通

---

## 方案A：官方渠道

**入口**：
- gemini.google.com — 网页版（需要 Google 账号）
- aistudio.google.com — 开发者入口，免费额度更大

**条件**：Google 账号 + 能访问 Google 服务

**优点**：最原生，功能最全
**缺点**：双重门槛

---

## 方案B：聚合平台

和 ChatGPT/Claude 聚合平台同理。大部分聚合平台已支持 Gemini 3.1 Pro 和 Flash。

**注意**：Gemini Flash（轻量版）通常放在免费区——因为 Google 官方就给很大的免费额度，聚合平台转手也不心疼。

**优点**：零门槛，不用 Google 账号
**缺点**：隐私风险

---

## 方案C：API 接入

Google AI Studio 提供免费 API 额度（每分钟60次）。国内通过中转平台调用，仍然免费。

**适合谁**：开发者。

---

## Gemini vs ChatGPT vs Claude

| | Gemini | ChatGPT | Claude |
|:---|:---|:---|:---|
| 免费额度 | 最多 | 有免费版 | 几乎无 |
| 多模态 | 原生 | 强 | 偏文本 |
| 上下文 | 100万token | 128K-1M | 200K |
| 中文 | 好 | 很好 | 好 |
| 国内门槛 | Google账号 | OpenAI账号 | 最高 |

**简单逻辑**：免费 + 多功能 → Gemini；深度推理 + 代码 → Claude；中文 + 综合 → ChatGPT。

<div class="cross-links">

### 你可能还想看

* [NanoBanana 2 教程](/aitools/posts/nanobanana2-guide/) — Gemini 的生图能力
* [ChatGPT 使用指南](/aitools/posts/chatgpt-guide/) — 对比参考

</div>
