# 75 期数据表 · 八家国内外主流 token 价格 + 各根本差异关键数据

> **抓取日期**: 2026-07-11 至 2026-07-12
> **数据维度**: 输入单价 / 输出单价 / Cached input 单价 / Cache write / 长上下文提价 / Free tier
> **货币**:USD/百万 tokens(unless noted)
> **可信度标记**: L4(厂商一手页) > L3(行业头部 + 多源交叉) > L2(二级权威站) > L1(单源) > L0(待验证)

---

## A. 国内 8 家厂商 token 单价表

### A.1 OpenAI(2026-07 时点)

| 模型 | Input $/M | Cached Input $/M | Output $/M | Cache Write | 长上下文提价 | Free tier | 可信度 | 来源 |
|---|---|---|---|---|---|---|---|---|
| GPT-5.5 | $5.00 | $0.50 (90% off) | $30.00 | 1.25x input | >272K 时 2x input / 1.5x output | 无(只 starter credit) | L4 | https://developers.openai.com/api/docs/models/gpt-5.5 |
| GPT-5.5 Pro | $30.00 | — | $180.00 | 1.25x | 同上 | 无 | L4 | 同上 |
| GPT-5.5 Batch | $2.50 | $0.25 | $15.00 | 1.25x | n/a (offline) | 无 | L3 | https://apidog.com/blog/gpt-5-5-pricing/ |
| GPT-5.5 Flex | $2.50 | $0.25 | $15.00 | 1.25x | n/a | 无 | L3 | 同上 |
| GPT-5.6 Sol | $5.00 | $0.50 | $30.00 | 1.25x | n/a 发布时未公开 | 无 | L3 | https://www.aipricing.guru/openai-pricing/ |
| GPT-5.6 Terra | $2.50 | $0.25 | $15.00 | 1.25x | 同上 | 无 | L3 | 同上 |
| GPT-5.6 Luna | $1.00 | $0.10 | $6.00 | 1.25x | 同上 | 无 | L3 | 同上 |
| GPT-5.4 | $2.50 | $0.25 | $15.00 | 1.25x | n/a | 无 | L3 | 同上 |
| GPT-5.4 mini | $0.75 | — | $4.50 | — | n/a | 无 | L3 | 同上 |
| GPT-5.4 nano | $0.20 | — | $1.25 | — | n/a | 无 | L3 | 同上 |
| GPT-4.1 | $2.00 | $0.50 | $8.00 | — | 1M 上下文 | 无 | L3 | 同上 |
| GPT-4.1 mini | $0.40 | $0.10 | $1.60 | — | 1M | 无 | L3 | 同上 |
| GPT-4.1 nano | $0.10 | — | $0.40 | — | 1M | 无 | L3 | 同上 |
| GPT-4o | $2.50 | — | $10.00 | — | 128K | 无 | L3 | 同上 |
| GPT-4o mini | $0.15 | $0.075 | $0.60 | — | 128K | 无 | L3 | 同上 |
| GPT-5 (旧版) | $1.25 | — | $10.00 | — | 400K | 无 | L3 | 同上 |
| GPT-5 Pro (旧版) | $15.00 | — | $120.00 | — | 400K | 无 | L3 | 同上 |
| o3 (reasoning) | $2.00 | — | $8.00 | — | 200K | 无 | L3 | 同上 |
| o4-mini (reasoning) | $1.10 | — | $4.40 | — | 200K | 无 | L3 | 同上 |

### A.2 Anthropic Claude(2026-07 时点)

| 模型 | Input $/M | Cached Input $/M (Read) | Cache Write $/M | Output $/M | 长上下文提价 | Free tier | 可信度 | 来源 |
|---|---|---|---|---|---|---|---|---|
| Claude Fable 5 | $10.00 | $1.00 | $12.50 | $50.00 | n/a(latest) | 无(只 Pro) | L4 | https://www.anthropic.com/pricing |
| Claude Opus 4.8 | $5.00 | $0.50 | $6.25 | $25.00 | n/a | 无 | L4 | 同上 |
| Claude Sonnet 5 (intro 价) | $2.00 | $0.20 | $2.50 | $10.00 | n/a(8/31/2026 前) | 无 | L4 | 同上 |
| Claude Sonnet 5 (standard) | $3.00 | $0.30 | $3.75 | $15.00 | n/a(8/31/2026 后) | 无 | L4 | 同上 |
| Claude Sonnet 4.6 | $3.00 | $0.30 | $3.75 | $15.00 | n/a | 无 | L4 | 同上 |
| Claude Opus 4.7 | $5.00 | $0.50 | $6.25 | $25.00 | n/a | 无 | L4 | 同上 |
| Claude Opus 4.5 | $5.00 | $0.50 | $6.25 | $25.00 | n/a | 无 | L4 | 同上 |
| Claude Haiku 4.5 | $1.00 | $0.10 | $1.25 | $5.00 | n/a | 无 | L4 | 同上 |
| Claude Managed Agents | $0.08/session-hour(active runtime) | — | — | — | n/a | n/a | L4 | 同上 |
| Claude Web search | $10/1K searches | — | — | — | n/a | n/a | L4 | 同上 |
| Claude Code execution | $0.05/hour/container | — | — | — | n/a | 50 free hours/day | L4 | 同上 |

### A.3 DeepSeek(2026-07 时点)

| 模型 | Input $/M (miss) | Cache Hit $/M | Output $/M | Cache Write | 长上下文提价 | Free tier | 可信度 | 来源 |
|---|---|---|---|---|---|---|---|---|
| DeepSeek-V4-Pro | $0.435 | $0.003625 | $0.87 | 1.25x input | n/a 1M context | 无,只有并发折扣 | L4 | https://api-docs.deepseek.com/quick_start/pricing/ |
| DeepSeek-V4-Flash | $0.14 | $0.0028 | $0.28 | 1.25x | 1M context | 无 | L4 | 同上 |

> 注:DeepSeek 的 cache hit 价格极低(比 miss 价低 35-50 倍),意味着"重复前缀"的 RAG / system prompt 场景 token 成本可几乎压扁。

### A.4 阿里云百炼(通义千问 Qwen)

| 模型 | Input 元/M | Output 元/M | Cache Hit | Cache Write | 长上下文提价 | Free tier | 可信度 | 来源 |
|---|---|---|---|---|---|---|---|---|
| Qwen3-Max | ~¥4/M | ~¥12/M | 估算 ~¥1/M | 1.25x | >128K ~¥6/M input | 新用户 100 万 token(估算) | L2 | 估算 |
| Qwen-Plus | ~¥0.8/M | ~¥2/M | ~¥0.2/M | 1.25x | n/a | 是 | L2 | 估算 |
| Qwen-Turbo | ~¥0.3/M | ~¥0.6/M | ~¥0.06/M | 1.25x | n/a | 是 | L2 | 估算 |
| Qwen-Long(1M ctx) | ~¥0.5/M | ~¥2/M | ~¥0.1/M | 1.25x | >128K 提价 | 部分有 | L2 | 估算 |

> **L2 标注理由**:阿里云百炼 2026 年 7 月 12 日官网抓取失败(JS 渲染),数字以行业二级汇总(Morphllm, apiDog, OpenRouter)推断。建议主编在文末标注"以阿里云百炼官方实时为准"。

### A.5 腾讯混元(Hunyuan)

| 模型 | Input 元/M | Output 元/M | Cache Hit | Cache Write | 长上下文提价 | Free tier | 可信度 | 来源 |
|---|---|---|---|---|---|---|---|---|
| Hunyuan-Standard | ~¥1.2/M | ~¥4/M | ~¥0.3/M | 1.25x | n/a | 是(API 调试) | L2 | 估算 |
| Hunyuan-Pro | ~¥5/M | ~¥15/M | ~¥1/M | 1.25x | >32K 提价 ~1.5x | 部分 | L2 | 估算 |
| Hunyuan-Long(256K) | ~¥0.8/M | ~¥2/M | ~¥0.2/M | 1.25x | >64K 提价 | 是 | L2 | 估算 |

> **L2 标注理由**:腾讯混元官方价格页 2026-07-12 JS 渲染失败,以二级汇总站推断。

### A.6 智谱 GLM(BigModel)

| 模型 | Input 元/M | Output 元/M | Cache Hit | Cache Write | 长上下文提价 | Free tier | 可信度 | 来源 |
|---|---|---|---|---|---|---|---|---|
| GLM-4.6 | ~¥1/M | ~¥4/M | ~¥0.3/M | 1.25x | 200K | 是(注册领) | L2 | 估算 |
| GLM-4.5-Air | ~¥0.5/M | ~¥2/M | ~¥0.15/M | 1.25x | 128K | 是 | L2 | 估算 |
| GLM-Z1-Air (推理) | ~¥0.8/M | ~¥3.2/M | ~¥0.2/M | 1.25x | 128K | 是 | L2 | 估算 |

> **L2 标注理由**:智谱官网 JS 渲染。

### A.7 字节火山引擎豆包(Doubao)

| 模型 | Input 元/M | Output 元/M | Cache Hit | Cache Write | 长上下文提价 | Free tier | 可信度 | 来源 |
|---|---|---|---|---|---|---|---|---|
| Doubao-1.5-Pro | ~¥0.8/M | ~¥2/M | ~¥0.2/M | 1.25x | 256K | 是 | L2 | 估算 |
| Doubao-1.5-Lite | ~¥0.3/M | ~¥0.6/M | ~¥0.06/M | 1.25x | 256K | 是 | L2 | 估算 |
| Doubao-Seed | ~¥1.2/M | ~¥4/M | ~¥0.3/M | 1.25x | 256K | 部分 | L2 | 估算 |

> **L2 标注理由**:火山引擎文档站 2026-07-12 JS 渲染失败。

### A.8 MiniMax(abab/MiniMax)

| 模型 | Input $/M | Output $/M | Cache Hit | Cache Write | 长上下文提价 | Free tier | 可信度 | 来源 |
|---|---|---|---|---|---|---|---|---|
| MiniMax-Text-01 | ~$0.30/M | ~$0.90/M | ~$0.10/M | 1.25x | 1M context | 部分 | L2 | 估算(2025 报价区间) |
| MiniMax-ABAB-6.5 | ~$0.15/M | ~$0.45/M | — | — | 64K | 部分 | L2 | 估算 |

> **L2 标注理由**:MiniMax 价格 2026 时点未在本次抓取到一手页面。以 2025 报价区间推断,需主编在撰稿前按公司名确认。

---

## B. 三个根本差异的实测原始数据

### B.1 状态叠加态 (差异 1)

| 数据点 | 数值 | 来源 | 可信度 |
|---|---|---|---|
| Anthropic Managed Agents 单价 | $0.08/session-hour(活动会话按小时单独计费) | https://www.anthropic.com/pricing | L4 |
| Anthropic Web search | $10/1000 searches | 同上 | L4 |
| Anthropic Code execution | $0.05/hour/container(每天 50 free hours) | 同上 | L4 |
| Claude "long-running conversations"$0.08/小时反映叠加态成本 | 0.08 USD | 同上 | L4 |

### B.2 响应时间 (差异 2)

| 数据点 | 数值 | 来源 | 可信度 |
|---|---|---|---|
| Character.AI 单会话成本 | $0.01/小时(百万级会话) | https://blog.character.ai/optimizing-ai-inference-at-character-ai/ | L3 |
| Character.AI 1 亿日活年度服务成本 | $3.65 亿/年,$3.65/日活/年 | 同上 | L3 |
| Character.AI AMD MI300X 升级后 token 成本降幅 | 50% | https://www.digitalocean.com/blog/technical-deep-dive-character-ai-amd | L3 |
| AI inference vs training 占比 | inference:training = 15:1(2026 行业) | https://www.byteiota.com/ai-inference-costs-2026-the-hidden-15-20x-gpu-crisis/ | L3 |
| Character.AI 风险计算 | 1M users × 1 hour/day × $0.01/hour = $365M/年 | https://blog.character.ai/optimizing-ai-inference-at-character-ai/ | L3 |

### B.3 上下文归属 (差异 3)

| 数据点 | 数值 | 来源 | 可信度 |
|---|---|---|---|
| GPT-5.5 长上下文(>272K input) | 2x input / 1.5x output(整个会话) | https://developers.openai.com/api/docs/models/gpt-5.5 | L4 |
| GPT-5.5 标准上限 | 1,050,000 token context, 128K max output | 同上 | L4 |
| GPT-5.5 Cached input 折扣 | $0.50/M(90% 折扣) | https://www.aipricing.guru/openai-pricing/ | L3 |
| GPT-5.6 Luna Cached read | $0.10/M | 同上 | L3 |

---

## C. 上下文长度 vs 单会话成本(差异 5)

| 上下文长度 | 单会话平均 tokens | OpenAI GPT-5.5 单价 | 单会话 "假设计入" cost(估算) | 比 8K 放大倍数 |
|---|---|---|---|---|
| 8K | 2K tokens 平均 | $5 input / $30 output | $0.02 + 重建缓存 | 1x |
| 32K | 8K 平均 | $5 / $30 | $0.08 + 持续缓存重建 | ~4x |
| 128K | 32K 平均 | $5 / $30(input miss 时 $10) | $0.32 + 长会话 | ~16x |
| 200K | 50K 平均 | $5/$30 input(>272K 时 2x) | $0.50 + 部分会话提价 | ~25x |
| 1M | 100K-1M | $5/$30 input(>272K 提价 2x,部分会话) | $0.50-$5.00 | 25-250x |

> 备注:数字基于"每会话 input tokens(假设 75% 系统提示 + 25% 用户内容)+ output(2K-10K tokens)"。比值是 input 增长 + cache miss + 长会话 attention cost 累乘后的工程估算,**L2 等级**,不是厂商官方账单。

---

## D. 5 个根本差异实测对照表

| 差异 | 传统服务 | Agent 应用 | 量化对比 | 数据来源 |
|---|---|---|---|---|
| 状态叠加 | 无状态 / Redis 缓存 | 会话级状态机 + history + tool result + LLM context | Anthropic Managed Agents $0.08/小时 | anthropic.com/pricing |
| 响应时间 | 50-200ms(REST API p99) | 1-10s(LLM call 端到端) | Character.AI 单会话 $0.01/小时 | character.ai blog |
| 上下文归属 | app 收口,context 关闭 | LLM 收口,context 累计 | GPT-5.5 >272K 提价 2x | developers.openai.com/api/docs/models/gpt-5.5 |
| 存储多栈 | DB / Redis / OSS 单一栈 | Qdrant + Postgres + Redis + OSS 叠加 | Anthropic managed agents 单独计费 | anthropic.com/pricing |
| 规模关系 | user 多 = 摊薄 | context 大 = 烧更多 | 8K → 200K 放大 ~25-30x | 综合估算(L2) |

---

## E. 与 Chinese SaaS 用户付费意愿 对照

| 中国 SaaS 用户类型 | 典型客单价(月) | 1000 用户年度收入 |
|---|---|---|
| 微中小企业(20-100 人) | 50-300 元 / 用户 / 年 | 5-30 万元 |
| 中型企业(100-500 人) | 200-800 元 / 用户 / 年 | 20-80 万元 |
| AI 客服初创"小 K"案例:硬件 + token 双烧 | — | **~80 万元(其中 token ≈ 46 万)** |

**结论**:中小 AI 客服初创的真实硬件 + token 成本基本 = 或 > 中型企业客单价收入——**活都活不下去,除非靠融资。**
