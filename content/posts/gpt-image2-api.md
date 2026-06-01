+++
title = "GPT Image 2 API 接入"
date = 2026-05-30
draft = false
description = "通过API批量生成GPT Image 2图片。中转平台接入方式、价格、代码示例。"
+++

## 适合谁

- 需要**批量生图**（几十到几千张）
- 想把生图能力**集成到自己产品里**
- 有基本编程能力（会调 API 就行）

---

## 接入方式

GPT Image 2 兼容 OpenAI 的图像 API 接口。通过国内中转平台，把 `base_url` 换掉即可。

### 代码示例

```python
from openai import OpenAI

client = OpenAI(
    api_key="你的中转平台key",
    base_url="https://中转平台地址/v1"
)

response = client.images.generate(
    model="gpt-image-2",
    prompt="一只橘猫在窗台上晒太阳，温暖的自然光，4K画质",
    n=1,
    size="1024x1024"
)

print(response.data[0].url)
```

**支持的分辨率**：1024x1024、1792x1024（横版）、1024x1792（竖版）

### Node.js 版本

```javascript
import OpenAI from 'openai';

const client = new OpenAI({
  apiKey: '你的中转平台key',
  baseURL: 'https://中转平台地址/v1',
});

const response = await client.images.generate({
  model: 'gpt-image-2',
  prompt: '一只橘猫在窗台上晒太阳',
  n: 1,
  size: '1024x1024',
});

console.log(response.data[0].url);
```

---

## 费用参考

| 分辨率 | 中转价格（约） |
|:---|:---|
| 1024×1024 | ¥0.3-0.5/张 |
| 1792×1024 | ¥0.4-0.7/张 |
| 1024×1792 | ¥0.4-0.7/张 |

比 ChatGPT Plus 的 $20/月（¥140）灵活：用得多付得多，用得少付得少。批量生成 100 张也就几十块钱。

---

## 怎么找中转平台

搜索「GPT Image 2 API」「OpenAI 图像 API 中转」。注意：

- 确认平台写的是 GPT Image 2（不是旧版 DALL-E）
- 看平台文档确认支持的图像模型列表
- 先充 ¥5-10 试几张，验证效果和稳定性

---

## API vs 聚合平台网页

| | API 中转 | 聚合平台网页 |
|:---|:---|:---|
| 使用方式 | 写代码调用 | 打开网页输入 |
| 批量能力 | ✅ 自动化批量 | ❌ 手动一张张生成 |
| 集成能力 | ✅ 嵌入自己的产品 | ❌ |
| 门槛 | 需要编程 | 零门槛 |
| 价格 | ¥0.3-0.7/张 | 通常按月订阅 |

<div class="cross-links">

### 你可能还想看

* [GPT Image 2 免费试用](/aitools/posts/gpt-image2-free/)
* [开发者 API 接入指南（ChatGPT）](/aitools/posts/chatgpt-api/)
* [ChatGPT Plus 官方使用](/aitools/posts/gpt-image2-official/)

</div>
