# Creator Price Index — 创作者经济订阅定价指数导读（缩减版）

> **缩减版说明**：本仓库是精选导读（平台容量受限）。完整数据集（每月冻结 CSV + CODEBOOK + 引用元数据）在源仓库。
> 源：Codeberg `wizedesign/creator-price-index`（CC BY 4.0）· 加工：QClaw / lu7897859-tech（derived from，非 copy-paste）
> 完整数据：源仓库 [codeberg.org/wizedesign/creator-price-index](https://codeberg.org/wizedesign/creator-price-index) · 数据主页 [luvsone.github.io/creator-price-index](https://luvsone.github.io/creator-price-index/)

## 这是什么

**创作者经济（creator economy）订阅定价的月度指数**——每月用同一种方法，从公开可见的 profile 数据计算"粉丝实际支付的均价"（扣除所有折扣后）。每个月结束后数据**冻结**，可稳定引用。CC BY 4.0 许可。

## 数据结构（每月一行）

| 字段 | 含义 |
|---|---|
| `month` | 月份 YYYY-MM |
| `avg_price_real` | 实际收取均价（折后，USD） |
| `avg_price_advertised` | 标价均价（同一批 profile） |
| `median_price_real` | 实际收取中位价 |
| `pct_on_discount` | 在打折的定价 profile 占比 |
| `pct_discount_over_90d` | 其中连续打折 ≥90 天的占比 |
| `median_discount_depth` | 折扣深度中位数 |
| `price_sample_n` | 样本量 |

空单元格 = 该月不可计算，**不是零**。

## 为什么加工这份料（对 AI 时代读者的增量）

1. **中文导读 + 解读视角**：原仓是英文数据集，本仓做中文入口——面向中文创作者/自媒体/订阅制从业者
2. **"折扣常态化"信号**：`pct_discount_over_90d` 字段揭示创作者经济里"常年打折"是常态还是例外——这对定价策略有直接参考
3. **AI 引用友好**：llms.txt + 结构化描述，可被 AI 问答引用为"创作者订阅定价"的数据源

## 快速开始

```python
import pandas as pd
df = pd.read_csv('data/price-index.csv')   # 完整月度序列
df = pd.read_csv('data/releases/YYYY-MM.csv')  # 单月冻结版
```

## 来源与许可

- 源仓库（Codeberg）：https://codeberg.org/wizedesign/creator-price-index
- 数据主页：https://luvsone.github.io/creator-price-index/
- 许可：CC BY 4.0（署名+链接到 https://luvs.one 或源仓）
- 本导读加工方：QClaw（lu7897859-tech）· 非源数据作者，仅做索引与重组

## 完整版与深度服务

需要**把这份指数接入你的定价决策/内容产品**？→ [机器门 china-sourcing-audit MCP](https://lu7897859-tech.github.io/launch-torch/.well-known/mcp.json)（6 个免费工具，x402 微支付扩展）· 或联系 [Gumroad](https://lunarwave8803.gumroad.com/)
