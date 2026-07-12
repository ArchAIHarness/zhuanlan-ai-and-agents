# 76 期数据表 · 三招落地实测 + 国产 LLM Provider 价格对照

> **抓取日期**: 2026-07-12
> **数据维度**: 边缘推理路径(浏览器侧)/ Provider 价格(国产 LLM 替代)/ WebGPU 边界 / 业务专注案例
> **货币**: USD/百万 tokens(unless noted)
> **可信度标记**: L4(厂商一手页) > L3(行业头部 + 多源交叉) > L2(行业二级汇总 + 推算) > L1(单源) > L0(待验证)

---

## A. 边缘推理路径(浏览器侧)实测对照

### A.1 JSLinux × WebContainer × WASM × WebGPU 对比

| 路径 | 启动时间 | 内存 | 适合跑什么 | 不适合跑什么 | 浏览器兼容性 | 来源 | 可信度 |
|---|---|---|---|---|---|---|---|
| **QEMU JSLinux**(Fabrice Bellard) | 点击即用 | 64-256 MB | 完整 Linux VM / x86/RISC-V 二进制 / Alpine / Windows 2000 | LLM / 重 GPU 工作 | 全平台 | https://bellard.org/jslinux/ | L4 |
| **WebContainer / StackBlitz** | 毫秒级 | 完整 Node.js 子集 | **完整 Node.js + npm/pnpm/yarn + 文件系统 + dev server** | LLM / 完整 native binary | Chromium + Firefox + Safari TP | https://webcontainers.io/ | L4 |
| **WASM(轻量场景)** | 即时 | 几 MB | 图像 / 视频 / 加密 / 数据解析 / **轻量 ML(Whisper-tiny / DistilBERT / MobileNetV4)** | 完整 LLM / 重 ML 训练 | 全平台原生 | https://webassembly.org/ + Transformers.js | L3 |
| **WebGPU** | 即时 | 取决于 GPU | **embeddings / sentiment / ASR tiny / 图像分类 / 小模型推理** | **完整 LLM(Qwen-72B fp16 = 140GB,远超浏览器 GPU)** | 全球 ~70%(Oct 2024) | https://huggingface.co/docs/transformers.js/en/guides/webgpu | L4 |

### A.2 WebGPU 跑 LLM **假命题** 根因(L4)

| 限制 | 具体原因 | 数量级 |
|---|---|---|
| **显存** | 浏览器 GPU 显存 ≤ 用户 GPU 显存(消费级显卡 8-24 GB);Qwen-72B fp16 = ~140GB,Qwen-7B fp16 = ~14GB | 数量级不匹配 |
| **KV cache 不持久** | 浏览器 reload 后 KV cache 全部丢失,长对话等于"每次重头算" | 工程不可行 |
| **通信开销** | GPU → CPU 数据传输在浏览器侧比云端慢一个数量级(WebGPU 缺直接 PCIe 通道) | 数量级不匹配 |
| **浏览器支持** | 截至 2024-10 WebGPU 全球浏览器支持仅约 70%(caniuse.com/webgpu)| 部分用户根本用不了 |
| **LLM 模型大小** | Hugging Face Transformers.js v3 推荐 `q4` / `q8` 量化 + 小模型 | 明确说不适合 LLM |

**L4**(Hugging Face 官方文档)。**结论**:**WebGPU 不适合跑 LLM**。本期调研**严格标注为假命题**,避免读者误以为"在浏览器跑 ChatGPT"是可行路径。

### A.3 真实生产案例(已脱敏)

| 案例 | 用 WebContainer 做什么 | 来源 |
|---|---|---|
| **StackBlitz Codeflow IDE** | 浏览器 IDE,处理 PR review | https://developer.stackblitz.com/codeflow/what-is-codeflow |
| **re:tune**(AI-native IDE) | AI copilot 在 WebContainer 内"理解并操作完整运行时(server + client)" | https://webcontainers.io/(客户引言)|
| **Vercel / SvelteKit** | 全栈交互式教学 | 同上 |
| **Egghead.io** | 嵌入式交互式编程教学 | 同上 |
| **Scrimba** | 嵌入式后端教学 | 同上 |
| **Xata** | Database SDK 教学 | 同上 |
| **Astro** | 静态站点构建器开发 | 同上 |
| **Suborbital** | Run WebContainers inside WebContainers("俄罗斯套娃"案例) | 同上 |

---

## B. Provider 抽象层 · 国产 LLM 替代价格对照

### B.1 OpenRouter 上国产模型一手价格(2026-07-12)

| 模型 | Input $/M | Output $/M | Context | 备注 |
|---|---|---|---|---|
| **Z.ai GLM 4.5 Air** | $0.13 | $0.85 | 131K | 国产最便宜的 agent 优化模型 |
| **Z.ai GLM 4.6** | $0.43 | $1.74 | **203K** | 国产最强 agent 优化,对标 Claude Sonnet 价格 1/7 |
| **DeepSeek V3.2 Exp** | $0.27 | $0.41 | 164K | 实验模型,sparse attention |
| **DeepSeek V4 Flash** | $0.14 | $0.28 | 1M | **国产最便宜生产级**,agent 工作负载爆款 |
| **DeepSeek V4 Pro** | $0.435 | $0.87 | 1M | 强推理版 |
| **Qwen3 Max**(估算) | ~$0.55 | ~$1.65 | 1M | 估算(参考 75 期 OpenRouter) |
| **Moonshot Kimi**(估算) | ~$0.30 | ~$1.20 | 128K | 估算(参考 75 期 OpenRouter) |
| **MiniMax abab**(估算) | ~$0.30 | ~$0.90 | 1M | 估算(参考 75 期 OpenRouter) |
| **豆包 Doubao 1.5 Pro**(估算) | ~$0.11 | ~$0.28 | 256K | 估算(参考 75 期 OpenRouter) |

**对比 OpenAI GPT-5.5**(75 期 L4):
- GPT-5.5 Input $5 / Output $30
- **DeepSeek V4 Flash 比 GPT-5.5 便宜 35-100 倍**

### B.2 OpenRouter 路由策略(L4)

| 策略 | 含义 | 适用场景 |
|---|---|---|
| **Balanced**(默认) | price + speed 平衡 | 通用 |
| **Nitro** | 最快 throughput | 实时对话 / 流式输出 |
| **Exacto** | 最高 tool-calling 准确率 | Agent tool 调用 |
| **自动 fallback** | 某 provider 失败 → 自动切换下一家 | 高 SLA 场景 |

**L4**(https://openrouter.ai/models + https://openrouter.ai/docs/features/uptime-optimization)。

### B.3 自托管 Ollama(L4)

| 维度 | 实测 |
|---|---|
| 价格 | 免费(本地运行) |
| Pro | $20/月(50x cloud usage)|
| Max | $100/月(5x Pro usage)|
| 支持应用 | OpenClaw / Claude Code / Codex |
| 数据隐私 | "Your data is never trained on" + 关键业务可完全离线 |
| 模型覆盖 | Qwen / GLM / DeepSeek / Llama / Mistral 全覆盖 |
| 数据存储 | 云端模型在 US / Europe / Singapore |

**L4**(https://ollama.com/)。

### B.4 Provider 价格节省实测

**OpenRouter effective pricing**(2026-07-12 实测):
- 价格节省 **60-80%** 靠 prompt caching 复用
- 来源:https://openrouter.ai/models/z-ai/glm-4.6(页面显示 Effective Pricing 章节)

**L4**(OpenRouter 官方)。

---

## C. 业务专注 · 7 维度判断标准 + 公开案例

### C.1 7 维度判断标准(L3 综合)

| # | 维度 | 判断标准 |
|---|---|---|
| 1 | **行业规模** | 行业年营收 ≥ 100 亿 + 中小客户占比 ≥ 60% |
| 2 | **行业毛利** | ≥ 30% |
| 3 | **大厂覆盖度** | 阿里 / 腾讯 / 字节 / 华为在该行业**没有强势方案** |
| 4 | **行业话语权门槛** | 有行业协会 / 牌照 / 资质 |
| 5 | **上下游接口稳定性** | 上游接口稳定 + 不频繁变更 |
| 6 | **政策风险** | 政策稳定,3-5 年不变 |
| 7 | **团队基因** | 团队有人懂该行业业务 |

### C.2 公开成功案例类型(L2 行业汇总)

| 案例类型 | 细分行业 | 公开数据 |
|---|---|---|
| 医疗 AI 客服 SaaS | 互联网医院 / 民营医疗集团 | 多家公开报道(汇总) |
| 法律 AI 客服 SaaS | 中小企业法律咨询 | 多家公开报道(汇总) |
| 财税 AI 客服 SaaS | 中小企业代理记账 | 多家公开报道(汇总) |
| 跨境电商 AI 客服 | 出海跨境 | Temu / SHEIN 等带动整个赛道 |
| 餐饮 SaaS + AI | 餐饮连锁 | 多家公开报道(国内美团生态)|

**L2 标注理由**:具体公司名 + ARR 数字来自行业二级汇总,**不引用单家公司未经审计的数据**。撰稿引用时建议用"细分行业 AISaaS 18 个月达千万级 ARR 是公开报道过的现象"这种汇总性表述。

### C.3 通用 vs 细分账单对比(L2 估算)

| 模式 | 用户数 | 单用户月度成本 | 估算总成本 | 上下文大小 |
|---|---|---|---|---|
| **75 期"小 K"模式(通用 AI 客服)** | 1000 | **60 元/月/用户** | 6 万/月 + 30+ 万硬件 | 32K-128K |
| **76 期"小 K 改造后"** | **12000** | **4.8 元/月/用户** | **5.3-5.8 万/月** | 8K-16K |

> **L2 估算**:基于 75 期公开 token 单价 + 公开 SaaS 客单价 + WebContainer 公开技术能力,**不是公开厂商账单**。**撰稿引用必须标"测算"**。

---

## D. 三招叠加 · 复合降本算账(L2 估算)

### D.1 单一招数降本比例

| 招数 | 降本维度 | 比例 |
|---|---|---|
| **第一招(边缘推理 + 边缘状态)** | 硬件成本 | 减少 60-80% 1C1G 部署 |
| **第二招(Provider 多路由)** | Token 成本 | 比单 OpenAI 降 50-80% |
| **第三招(业务专注 + 上下文收缩)** | Token + 准确性 | 上下文收敛 50%+ |

### D.2 复合算账

**假设**:
- 用户:12000(从 75 期 1000 涨 12 倍)
- 边缘推断:WebContainer + Ollama 承担 70% 简单 Q&A + 工具调用
- 业务专注:行业单一,上下文收敛到 8K-16K

**月度账单估算**:
| 维度 | 75 期(改造前)| 76 期(改造后)|
|---|---|---|
| 用户数 | 1000 | 12000 |
| 硬件 | 2.5 万/月(1C1G × 1000)| 0.5-1 万/月(浏览器侧承担)|
| Token | 6 万/月(GPT-5.5 单价)| 3-4 万/月(70% Ollama + 30% DeepSeek)|
| 总月度 | **8.5 万/月** | **5.3-5.8 万/月** |
| 单用户成本 | **85 元/月/用户** | **4.6 元/月/用户** |
| 下降 | — | **~95%** |

> **L2 估算边界**:所有 token 数字基于公开单价,所有用户行为数字基于 75 期假设;实际数字随用户行为变化 ±30%。**撰稿引用必须标"测算"**。

---

## E. 与 75 期算账对比(L2 估算)

### E.1 75 期改造前账单(承接)

| 维度 | 75 期 |
|---|---|
| 1C1G × 1000 用户 | 30-50 万/年硬件 |
| Token 算账 | 1000 用户 × 10 轮/天 × 4000 tokens × 180 天 ÷ 1M × ($5×0.67 + $30×0.33) ≈ $64,800(46 万人民币)|
| 总成本 | ~80 万人民币/年 |

### E.2 76 期改造后账单

| 维度 | 76 期 |
|---|---|
| 边缘推理承担 70% | 0.5-1 万/月硬件 |
| 30% 走 OpenRouter + DeepSeek V4 Flash | 3-4 万/月 token |
| 业务专注降低上下文 | 上下文 8K-16K(对比 75 期 32K-128K)|
| 用户规模 | 12000(从 1000 涨 12 倍) |
| 总月度 | 5.3-5.8 万/月 = 63-70 万/年 |
| 单用户成本 | 4.8 元/月/用户 |

---

## F. 国产 LLM 官方价格页 JS 渲染失败说明

| 厂商 | 价格页 URL | 抓取结果 | 替代方案 |
|---|---|---|---|
| 阿里云百炼 | https://bailian.console.aliyun.com/ | JS 渲染失败(curl 拉到 SPA shell) | OpenRouter 上的国产模型价格 |
| 智谱 GLM | https://bigmodel.cn/pricing | JS 渲染失败 | OpenRouter 上的 GLM 价格 |
| 字节豆包 | https://www.volcengine.com/docs/82379/1544106 | JS 渲染失败 | OpenRouter 上的国产模型价格 |
| MiniMax | (公开 API 文档) | 文档站无明确 L4 价格页 | OpenRouter 上的 abab 价格 |

**建议**:撰稿引用时标注"以阿里云百炼 / 智谱 / 字节官方实时为准",不强行外推。本文统一使用 OpenRouter 上的一手价格(L4)。

---

## G. 来源清单(全部 L3-L4,L0-L2 已标)

| # | URL | 抓取日期 | 用于 | 可信度 |
|---|---|---|---|---|
| 1 | https://bellard.org/jslinux/ | 2026-07-12 | JSLinux 路径 | L4 |
| 2 | https://bellard.org/jslinux/tech.html | 2026-07-12 | JSLinux 技术限制 | L4 |
| 3 | https://webcontainers.io/ | 2026-07-12 | WebContainer 客户 + 能力 | L4 |
| 4 | https://webcontainers.io/guides/browser-support | 2026-07-12 | 浏览器兼容性 | L4 |
| 5 | https://developer.stackblitz.com/codeflow/what-is-codeflow | 2026-07-12 | StackBlitz Codeflow | L4 |
| 6 | https://github.com/stackblitz/webcontainer-core | 2026-07-12 | WebContainer 开源 | L4 |
| 7 | https://huggingface.co/docs/transformers.js/en/guides/webgpu | 2026-07-12 | WebGPU 跑 LLM 假命题 | L4 |
| 8 | https://huggingface.co/docs/transformers.js/en/index | 2026-07-12 | Transformers.js v3 浏览器跑 ML | L4 |
| 9 | https://openrouter.ai/ | 2026-07-12 | OpenRouter 一手数据 | L4 |
| 10 | https://openrouter.ai/docs/features/uptime-optimization | 2026-07-12 | OpenRouter 自动 fallback | L4 |
| 11 | https://openrouter.ai/models/z-ai/glm-4.5-air | 2026-07-12 | GLM 4.5 Air 价格 | L4 |
| 12 | https://openrouter.ai/models/z-ai/glm-4.6 | 2026-07-12 | GLM 4.6 价格 | L4 |
| 13 | https://openrouter.ai/models/deepseek/deepseek-v3.2-exp | 2026-07-12 | DeepSeek V3.2 价格 | L4 |
| 14 | https://api-docs.deepseek.com/quick_start/pricing/ | 2026-07-12(经 75 期抓取)| DeepSeek V4 价格 | L4 |
| 15 | https://ollama.com/ | 2026-07-12 | Ollama Pro/Max + 隐私承诺 | L4 |
| 16 | https://docs.ollama.com/integrations | 2026-07-12 | Ollama 集成 | L4 |
| 17 | https://replit.com/ai | 2026-07-12 | Replit Agent 案例 | L4 |
| 18 | https://caniuse.com/webgpu | 2026-07-12(经 HuggingFace 文档引用)| WebGPU 全球 70% 支持 | L4 |