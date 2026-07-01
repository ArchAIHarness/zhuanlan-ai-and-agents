# 29-30 期 · DDD 完整理论与 framework 实战 实施计划

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** 落盘两篇专栏文章——第 29 篇完整讲透 DDD(理论篇,有下一篇预告)+ 第 30 篇以 framework 仓库为案例讲 DDD 融入 AI 开发(实践篇,无预告),全套流程跑完保存到三平台(知乎/CSDN/掘金)草稿就绪。

**Architecture:** 适配本仓库 content-* 5 角色团队协作(content-researcher 调研 → content-writer 撰稿 → content-illustrator 配图 → content-auditor 审核 → content-publisher 发布),按"合并调研 + 两篇独立撰稿"模式跑全链路。两位"作者"是 29 篇和 30 篇。所有阶段产物沉淀到本仓库既有约定位置(`research/`、`illustration-briefs/`、`audit/`、`.zhihu-publish/`、`.csdn-publish/`、`.juejin-publish/`、`assets/<文章名>/`)。

**Tech Stack:** Git + Markdown + 手绘教育插图(baoyu-image-gen via baoyu-cover-image + baoyu-article-illustrator skill)+ Playwright(发布自动化)+ 本仓库既有 content-* 协作纪律(`AGENTS.md`)。

## Global Constraints

- **写作纪律(必守,来源: `AGENTS.md` §5)**：中文/短句/术语首次出现给直觉解释/6-8 节/核心比喻 1 个/去 AI 味清单/开头四步走 + 结尾四步走。
- **品牌串联(必守,来源: `AGENTS.md` §6)**：每篇至少一处内嵌钩子自然引到 ArchAIHarness 主张 + 文末统一出口段(§6.2 模板)+ 不暴露私有 `.opencode/` 编排(§5.7)。
- **维护约定(必守,来源: `AGENTS.md` §七)**：§7.0 完稿五要素全数就位才算完成 + §7.4 发布门禁(发稿前主编必须用 question 工具逐平台确认,任何平台不得合并、不得绕过)+ §7.3 发布链接自动归档。
- **连载节奏(必守,来源: `AGENTS.md` §5.2)**：29 篇(奇=理论篇)**末尾必须写下一篇预告**;30 篇(偶=实践篇)**末尾不写预告**,直接以金句收束。
- **承担审稿约束(必守,29/30 期 spec「撰稿约束」段落)**：
  - **29 篇**:比喻体系用"国家边界"系列(避开 27 篇"作曲家/乐谱");战术层只展开聚合根/实体/值对象,其余概念点到为止;核心 5-6 个术语集中在"什么是 DDD"小节用"翻译成人话"过一遍;标题候选三选(开写前可校准,避开"教科书"调性)。
  - **30 篇**:叙事重心=通用打法抽象(framework 印证),不写新链路(避 28 篇换皮);比喻体系用"DDD 是 AI 的轨道"(避开 27/28"乐谱/赛道");不写"加 SPI 实现"这类功能延展,严格落在 framework 已有的四仓分层 + 双文档体系 + TDD 纪律 + 领域事件规范。
- **每篇禁止重复 27/28 篇用过的核心比喻**(乐谱/作曲家/音符/表情记号/赛道/焊边界 + 放选择)。
- **目录与命名(必守,来源: `AGENTS.md` §4.4)`**:专栏正文 `NN_<标题>.md`;配图 `assets/NN_<标题>/`;渠道包按平台独立存放;插画简报 `illustration-briefs/29-illustration-brief.md` / `30-illustration-brief.md`;调研报告 `research/29-30-research-report.md`;审核报告 `audit/29-audit-report.md` / `audit/30-audit-report.md`;跨期复盘 `audit/29-30-retrospective.md`。

---

## 文件结构(本计划会创建/修改的文件清单)

### 新增文件

| 路径 | 责任人 | 用途 |
|---|---|---|
| `research/29-30-research-report.md` | content-researcher | 29-30 期合并调研 |
| `illustration-briefs/29-illustration-brief.md` | content-master | 29 篇配图简报(主编写,插画专员执行) |
| `illustration-briefs/30-illustration-brief.md` | content-master | 30 篇配图简报(主编写,插画专员执行) |
| `29_DDD完整指南——AI时代工程师的第一道秩序分水岭.md` | content-writer | 29 篇正文 |
| `30_DDD怎么融入AI开发——我从framework仓库里捞出来的四阶段打法.md` | content-writer | 30 篇正文 |
| `assets/29_DDD完整指南——AI时代工程师的第一道秩序分水岭/cover.png` | content-illustrator | 29 篇封面 |
| `assets/29_DDD完整指南——AI时代工程师的第一道秩序分水岭/01-*.png` ~ `06-*.png` | content-illustrator | 29 篇配图(预估 5-6 张) |
| `assets/29_DDD完整指南——AI时代工程师的第一道秩序分水岭/prompts/*.md` | content-illustrator | 29 篇配图 prompts |
| `assets/29_DDD完整指南——AI时代工程师的第一道秩序分水岭/batch.json` | content-illustrator | 29 篇批量生成配置 |
| `assets/30_DDD怎么融入AI开发——我从framework仓库里捞出来的四阶段打法/cover.png` | content-illustrator | 30 篇封面 |
| `assets/30_DDD怎么融入AI开发——我从framework仓库里捞出来的四阶段打法/01-*.png` ~ `05-*.png` | content-illustrator | 30 篇配图(预估 5 张) |
| `assets/30_DDD怎么融入AI开发——我从framework仓库里捞出来的四阶段打法/prompts/*.md` | content-illustrator | 30 篇配图 prompts |
| `assets/30_DDD怎么融入AI开发——我从framework仓库里捞出来的四阶段打法/batch.json` | content-illustrator | 30 篇批量生成配置 |
| `audit/29-audit-report.md` | content-auditor | 29 篇审核报告 |
| `audit/30-audit-report.md` | content-auditor | 30 篇审核报告 |
| `audit/29-30-retrospective.md` | content-auditor | 29-30 期复盘 |
| `.zhihu-publish/<slug>/` × 2 | content-publisher | 知乎渠道包 |
| `.csdn-publish/<slug>/` × 2 | content-publisher | CSDN 渠道包 |
| `.juejin-publish/<slug>/` × 2 | content-publisher | 掘金渠道包 |

### 修改文件

| 路径 | 责任人 | 改动 |
|---|---|---|
| `AGENTS.md` §二 进度表 + §七 维护日志 | content-master | 推进 29/30 状态 + 追加完稿/发布记录 |
| `README.md` 文章目录 + 阅读建议 | content-master | 同步 29/30 条目(完稿与发布后) |

---

## Task 1:29-30 期合并调研(content-researcher)

**Files:**
- Create: `research/29-30-research-report.md`

**承接**:`27-28-research-report.md` 已沉淀 DDD 基本概念 + framework 实战锚点。本任务聚焦"29-30 期新增需求":① 核对 framework 仓库当前最新公开设计(双文档体系、四层架构、TDD 纪律、领域事件规范),确保 30 篇引用的所有事实是最新的;② 收集 DDD 经典参考(Eric Evans《领域驱动设计》、Vaughn Vernon《实现领域驱动设计》/《领域驱动设计精粹》),核实核心概念术语翻译;③ 梳理术语对照表(限界上下文 / 聚合根 / 实体 / 值对象 / 领域事件 / 领域服务 / 仓储 / 统一语言 / 上下文映射),为 29 篇"翻译成人话"提供权威翻译底稿;④ 调研 19 个术语的"日常直觉类比"方案,辅助 29 篇"快速过"段落措辞。

**Step 1.1:列调研清单**
- framework 仓库当前 main 分支最新 commit hash + README/AGENTS.md 当前版本
- framework 仓库的 modules/ 目录结构(domain/application/infrastructure/interfaces 四层布局是否依旧)
- gateway 仓库的 SPI 接口列表(6 个 SPI 当前命名)
- DDD 三个教材的核心术语表(中英对照 + 标准翻译)
- 术语类比候选清单(每个核心术语 2-3 个日常类比方案)

**Step 1.2:产出调研报告**
结构按 `27-28-research-report.md` 模板:
1. 调研目标(本期特定)
2. 调研方法(多源交叉)
3. 关键发现(framework 最新事实 + 术语权威翻译 + 类比候选)
4. 写作锚点(可被 29/30 篇直接引用的具体设计 + URL 引用)
5. 风险与约束(framework 私有编排禁区)

**Interfaces**:
- Consumes:29-30 期 spec(在 `AGENTS.md` §四)
- Produces:`research/29-30-research-report.md` — 由 content-writer 在 Task 3/4 撰稿时消费

**Definition of Done**:
- [ ] 调研报告落盘 `research/29-30-research-report.md`
- [ ] 框架最新事实可被核实(GitHub commit hash 可追溯)
- [ ] 术语翻译对照表完整
- [ ] 类比候选清单为每个核心术语提供 2-3 个方案
- [ ] 主编验收通过(此任务的"读者"是 content-master)

- [ ] **Commit**:
```bash
git add research/29-30-research-report.md
git commit -m "docs(research): 29-30 期合并调研报告(framework 最新事实 + DDD 术语翻译)"
```

---

## Task 2:撰稿要求下发(content-master)

**Files:**
- Create: `illustration-briefs/29-illustration-brief.md`
- Create: `illustration-briefs/30-illustration-brief.md`

**承接**:spec 已落盘到 `AGENTS.md` §四。本任务把 spec 的核心要点翻译成"撰稿员可直接照做"的提示文件:
- 标题候选(开写前可校准,但给出优先推荐)
- 核心比喻(强制)
- 必含术语清单(每个的"翻译成人话"模板已由 Task 1 调研提供)
- 5-6 张配图的内容清单(图编号 + 文字描述 + 比喻对应)
- 出口段(§6.2 模板)
- 撰稿约束(评审视角的硬约束)

**Step 2.1:写 29 篇撰稿简报**
输出 `illustration-briefs/29-illustration-brief.md`,包含:
- 标题最终建议(从 spec 候选三选一里挑一个优先,开写前可校准)
- 7 节结构大纲(每节 50-100 字内容指引)
- 6 张配图占位:
  - 01-**统一语言的桥梁**(开篇用):翻译官 + 术语对照表的视觉化
  - 02-**限界上下文切割图**:一团乱麻 → 几个清晰国家,标注"护照/货币"
  - 03-**上下文映射关系图**:6 种关系(客户-供应商/发布-订阅/共享内核/开放主机/防腐层/合作)的可视化
  - 04-**聚合根的边界**:看门人/门卫的视觉化
  - 05-**四阶段 DDD 落地**:需求→设计→研发→交付的产物链条
  - 06-**AI 时代的 DDD 护栏**:业务边界 = AI 边界(收尾用)
- 金句硬清单(从 spec 6 句金句复制)
- 比喻体系硬约束(国家边界/护照/货币/翻译官/看门人;禁用乐谱/作曲家/音符/表情记号)
- 术语首次出现节奏(集中过一遍,后续不再硬解释)
- 出口段模板

**Step 2.2:写 30 篇撰稿简报**
输出 `illustration-briefs/30-illustration-brief.md`,包含:
- 标题最终建议
- 7-8 节结构大纲
- 5 张配图占位:
  - 01-**DDD 是 AI 的轨道**:轨道 + 出轨 + 翻车的视觉化(开场)
  - 02-**四阶段 AI 动作全景图**:一张图串需求→设计→研发→交付
  - 03-**domain 零 Spring 红线**:framework 的 domain 层 vs 其他三层的视觉化(配研发阶段)
  - 04-**双文档体系**:readme/AGENTS.md 双开 + "人看/AI 看"对应关系(配研发阶段)
  - 05-**边界焊死,选择放开**:framework 硬规范 + gateway 软秩序对照(配收尾)
- 叙事重心硬约束(通用打法抽象,不是新案例)
- framework 必引用的具体设计点(双文档/四层/TDD/事件规范)
- 禁用事项(不做功能延展/不写新链路/不展开 SPI 实现细节)

**Definition of Done**:
- [ ] 两个简报文件落盘
- [ ] 简报内含具体可执行指引(非占位/TBD)
- [ ] 简报与 spec 各项约束一一对齐
- [ ] 主编验收通过

- [ ] **Commit**:
```bash
git add illustration-briefs/29-illustration-brief.md illustration-briefs/30-illustration-brief.md
git commit -m "docs(planning): 29-30 期撰稿简报(配图占位 + 比喻硬约束 + 叙事要求)"
```

---

## Task 3:29 篇正文撰稿(content-writer)

**Files:**
- Create: `29_DDD完整指南——AI时代工程师的第一道秩序分水岭.md`

**承接**:Task 2 简报 + Task 1 调研报告。

**Step 3.1:起草 29 篇正文**
按简报里的 7 节结构,撰写:
- 每节符合 §5 写作纪律(中文短句/术语首次直觉解释/破折号多/不用 AI 化词汇)
- 严格使用"国家边界"比喻体系,禁用乐谱相关
- 战术层只展开聚合根/实体/值对象,其余概念点到为止
- 包含 §6.2 文末统一出口段
- 包含下一篇预告(指向 30 篇)

**Step 3.2:自检**
- [ ] 7 节结构完整
- [ ] 核心比喻(国家边界/护照/货币/翻译官/看门人)始终如一
- [ ] 没有出现乐谱/作曲家/音符/表情记号等 27 篇用过的比喻
- [ ] 没有回扣"第 X 篇讲过"这类硬篇号引用
- [ ] 包含 §6.2 出口段
- [ ] 末尾有下一期预告
- [ ] 估算 15000-20000 字(若超过 22000 字需要主编提示是否拆分)

**Step 3.3:提交审核初审**
把 29 篇正文正文文件路径提交给 content-auditor,等待初审反馈。

**Definition of Done**:
- [ ] 正文文件落盘
- [ ] 7 节结构对仗
- [ ] 自检通过

- [ ] **Commit**:
```bash
git add 29_DDD完整指南——AI时代工程师的第一道秩序分水岭.md
git commit -m "feat(29): DDD 完整指南——AI 时代工程师的第一道秩序分水岭(初稿)"
```

---

## Task 4:30 篇正文撰稿(content-writer)

**Files:**
- Create: `30_DDD怎么融入AI开发——我从framework仓库里捞出来的四阶段打法.md`

**承接**:Task 2 简报 + Task 1 调研报告 + 29 篇完稿(便于读懂承接点)。

**Step 4.1:起草 30 篇正文**
按简报 7-8 节结构,撰写:
- 叙事重心:通用打法抽象(framework 印证),不写新链路
- 严格使用"DDD 是 AI 的轨道"比喻,禁用乐谱/赛道
- 必引用 framework 的四个具体设计(双文档体系/四层架构 domain 零 Spring/TDD 纪律/领域事件规范)
- 不写功能延展(不加 SPI 实现/不写新业务)
- 包含 §6.2 出口段
- **末尾不写预告**(双数实践篇硬约束),直接以金句收束

**Step 4.2:自检**
- [ ] 7-8 节结构完整
- [ ] 叙事重心清晰(打法而非案例)
- [ ] 没有出现"再加一条 SPI" / "扩展业务订单"这类功能延展
- [ ] 必引用 framework 四个具体设计点到位
- [ ] 没有出现 §5.7 禁用的工具种草语气
- [ ] 包含 §6.2 出口段
- [ ] **末尾没有"下一篇预告"**(双数实践篇硬约束)
- [ ] 估算 12000-15000 字

**Step 4.3:提交审核初审**
提交给 content-auditor。

**Definition of Done**:
- [ ] 正文文件落盘
- [ ] 自检通过

- [ ] **Commit**:
```bash
git add 30_DDD怎么融入AI开发——我从framework仓库里捞出来的四阶段打法.md
git commit -m "feat(30): DDD 怎么融入 AI 开发——我从 framework 仓库里捞出来的四阶段打法(初稿)"
```

---

## Task 5:审核初审(两篇并行,content-auditor)

**Files:**
- Create: `audit/29-audit-report.md`
- Create: `audit/30-audit-report.md`

**承接**:Task 3/4 提交的初稿正文。

**Step 5.1:29 篇审核**
按 §5 写作纪律 + §7.0 完稿五要素 + §6 品牌串联 + 评审视角硬约束(比喻/术语/不重复 27-28)逐条审核,出审核报告。

**Step 5.2:30 篇审核**
同上。

**Step 5.3:打回修改(若需要)**
若任一篇审核不通过,打回对应 Task 3/4 由 content-writer 修改;再次提交。

**Definition of Done**:
- [ ] 两份审核报告落盘
- [ ] 每份包含:审核项清单(逐项 ✓/✗)+ 修改建议清单(具体可改的位置)+ 综合判定(通过 / 打回)
- [ ] 综合判定为"通过"才进入 Task 6

- [ ] **Commit**:
```bash
git add audit/29-audit-report.md audit/30-audit-report.md
git commit -m "docs(audit): 29-30 期双篇审核初报"
```

---

## Task 6:29 篇配图(content-illustrator)

**Files:**
- Create: `assets/29_DDD完整指南——AI时代工程师的第一道秩序分水岭/prompts/cover.md`
- Create: `assets/29_DDD完整指南——AI时代工程师的第一道秩序分水岭/prompts/01-*.md` ~ `06-*.md`
- Create: `assets/29_DDD完整指南——AI时代工程师的第一道秩序分水岭/batch.json`
- Create: `assets/29_DDD完整指南——AI时代工程师的第一道秩序分水岭/cover.png`
- Create: `assets/29_DDD完整指南——AI时代工程师的第一道秩序分水岭/01-*.png` ~ `06-*.png`
- Modify: `29_DDD完整指南——AI时代工程师的第一道秩序分水岭.md`(插入配图 Markdown)

**承接**:Task 2 简报的 6 张配图占位 + baoyu-cover-image / baoyu-article-illustrator skill。

**Step 6.1:写 prompts**
按 spec/简报的 6 张图,每张写一段 prompt,保存到 `prompts/` 目录。风格统一按 `baoyu-article-illustrator` skill(手绘教育插图/暖色调奶油纸/黑色草图线/柔和粉彩色块/手写体中文标签/ArchAIHarness 右下角水印)。

**Step 6.2:生成 batch.json**
按 baoyu-image-gen 批量格式生成 `batch.json`。

**Step 6.3:批量生成**
运行 `baoyu-image-gen --batchfile batch.json` 生成 6 张正文图 + 1 张封面。

**Step 6.4:质量检查**
逐张检查:① 内容是否对应核心理念 ② 文字是否清晰 ③ 风格是否统一。若不满意,调整 prompt 重生成(重生成前必须把旧图备份为 `.bak.png`,按 §5.6 纪律)。

**Step 6.5:插入正文**
把通过检查的图片按位置插入正文 Markdown:
```markdown
![统一语言的桥梁:用户说的"用户"和工程师说的"User"是两回事,DDD 让所有人说同一种话](assets/29_DDD完整指南——AI时代工程师的第一道秩序分水岭/01-unified-language.png)
```

**Definition of Done**:
- [ ] 6 张正文图 + 1 张封面落盘
- [ ] 全部按 spec/简报对应到正文位置
- [ ] 风格统一(手绘教育插图)
- [ ] 已插入正文 Markdown 引用

- [ ] **Commit**:
```bash
git add assets/29_DDD完整指南——AI时代工程师的第一道秩序分水岭/ 29_DDD完整指南——AI时代工程师的第一道秩序分水岭.md
git commit -m "feat(29): 配图 + 封面 + 正稿全数就位"
```

---

## Task 7:30 篇配图(content-illustrator)

**Files:**
- Create: `assets/30_DDD怎么融入AI开发——我从framework仓库里捞出来的四阶段打法/prompts/*.md`
- Create: `assets/30_DDD怎么融入AI开发——我从framework仓库里捞出来的四阶段打法/batch.json`
- Create: `assets/30_DDD怎么融入AI开发——我从framework仓库里捞出来的四阶段打法/cover.png`
- Create: `assets/30_DDD怎么融入AI开发——我从framework仓库里捞出来的四阶段打法/01-*.png` ~ `05-*.png`
- Modify: `30_DDD怎么融入AI开发——我从framework仓库里捞出来的四阶段打法.md`(插入配图 Markdown)

**承接**:Task 2 简报的 5 张配图占位。

**Step 7.1-7.5**:与 Task 6 同模式(5 张正文图 + 1 张封面)。

**Definition of Done**:
- [ ] 5 张正文图 + 1 张封面落盘
- [ ] 全部按 spec/简报对应到正文位置
- [ ] 风格统一

- [ ] **Commit**:
```bash
git add assets/30_DDD怎么融入AI开发——我从framework仓库里捞出来的四阶段打法/ 30_DDD怎么融入AI开发——我从framework仓库里捞出来的四阶段打法.md
git commit -m "feat(30): 配图 + 封面 + 正稿全数就位"
```

---

## Task 8:主编校对(两篇并行,content-master)

**Files:**
- Modify: `29_DDD完整指南——AI时代工程师的第一道秩序分水岭.md`
- Modify: `30_DDD怎么融入AI开发——我从framework仓库里捞出来的四阶段打法.md`

**承接**:Task 5 审核通过 + Task 6/7 配图完成。

**Step 8.1:29 篇完稿自检**
按 §7.0 完稿五要素逐项核对:
- [ ] 正文内容完整(开头四步走、核心比喻、结语、下篇预告)
- [ ] 配图全部生成并插入正文
- [ ] 封面图已生成并存放到 `assets/<文章 slug>/`
- [ ] 文末出口段已包含(§6.2)
- [ ] README.md 的文章目录和配图索引已更新

**Step 8.2:30 篇同 29 篇**
注意:30 篇是双数实践篇,**末尾不写下一篇预告**(已通过自检)。

**Step 8.3:更新进度表**
AGENTS.md §二 进度表:29/30 两篇从"设计阶段"更新为"已完成";README.md 文章目录同步更新(配图索引同步)。

**Step 8.4:打回修改(若需要)**
若任一篇不满足完稿五要素,打回 Task 6/7 配图或 Task 3/4 正文修改。

**Definition of Done**:
- [ ] 两篇均通过完稿五要素自检
- [ ] 进度表已更新(状态=已完成)
- [ ] README.md 已同步

- [ ] **Commit**:
```bash
git add AGENTS.md README.md
git commit -m "docs(planning): 29-30 期双篇完稿(§7.0 完稿五要素就位)"
```

---

## Task 9:知乎渠道包(content-publisher)

**Files:**
- Create: `.zhihu-publish/29-DDD完整指南——AI时代工程师的第一道秩序分水岭<suffix>/article.zhihu.md`
- Create: `.zhihu-publish/29-DDD完整指南——AI时代工程师的第一道秩序分水岭<suffix>/metadata.json`
- Create: `.zhihu-publish/29-DDD完整指南——AI时代工程师的第一道秩序分水岭<suffix>/publish-checklist.md`
- Create: `.zhihu-publish/29-DDD完整指南——AI时代工程师的第一道秩序分水岭<suffix>/browser-playbook.md`
- Create: 同上四件套,30 篇一份

**承接**:Task 8 完稿两篇。

**Step 9.1:29 篇知乎渠道包**
按 §7.2 渠道包目录结构:`.zhihu-publish/<article-slug><suffix>/`。准备四件套:
- `article.zhihu.md`:知乎平台适配后的正稿(标题格式/段落空行/外链处理按知乎规范)
- `metadata.json`:标题、摘要、话题、专栏 ID、封面临时目录、配图清单
- `publish-checklist.md`:发布前自检清单
- `browser-playbook.md`:Playwright 操作步骤/已登录凭证存放

**Step 9.2:30 篇知乎渠道包**:同 29 篇。

**Definition of Done**:
- [ ] 两份知乎渠道包就位(8 个文件)
- [ ] metadata.json 含完整字段,无占位

(注意:此任务只准备渠道包,不实际发稿;发稿由 Task 12-14 执行)

- [ ] **Commit**:
```bash
git add .zhihu-publish/29-*/ .zhihu-publish/30-*/
git commit -m "feat(publish-zhihu): 29-30 期知乎渠道包就位"
```

---

## Task 10:CSDN 渠道包(content-publisher)

**Files:**
- Create: `.csdn-publish/29-*/` × 4 文件
- Create: `.csdn-publish/30-*/` × 4 文件

**承接**:Task 8 完稿两篇 + §7.4 CSDN 工作流门禁要求。

**Step 10.1**:参照 §7.4 CSDN 工作流准备渠道包,关键顺序:
1. 正文注入(平台适配按 CSDN 编辑器)
2. 配图插入位置明确(i-blog CDN 锚点)
3. 发布设置清单:封面→标签→摘要→分类专栏→文章类型→可见范围
4. 最终状态 = 草稿(不得点击发布)

**Step 10.2:做 CSDN 质量分收口自检**(§5.8):
- [ ] 专业度:章节里有框架分层/上下文映射/AGENTS.md 等可验证锚点
- [ ] 内容深度:开头第一段落到真实问题/痛点
- [ ] 时效性:补一句适用边界("本文基于 2026-07 的 framework 版本,具体以仓库 README 为准")
- [ ] 基础体验:已复检(专栏文风达标)
- [ ] 原创与首发口径:如实勾选原创 + 标注知乎为首发

**Definition of Done**:
- [ ] 两份 CSDN 渠道包就位(8 个文件)
- [ ] CSDN 自检清单全数通过
- [ ] 默认遵循质量收口验证(§5.8 默认值)

- [ ] **Commit**:
```bash
git add .csdn-publish/29-*/ .csdn-publish/30-*/
git commit -m "feat(publish-csdn): 29-30 期 CSDN 渠道包 + 质量分收口"
```

---

## Task 11:掘金渠道包(content-publisher)

**Files:**
- Create: `.juejin-publish/29-*/` × 4 文件
- Create: `.juejin-publish/30-*/` × 4 文件

**Step 11**:参照 §7.4 CSDN 工作流移植到掘金平台(掘金编辑器 + juejin-publisher-v2 skill)。关键差异:掘金分类/标签格式不同、自动审核期的链接格式归一(§7.3)、图片使用 juejin CDN。

**Definition of Done**:
- [ ] 两份掘金渠道包就位

- [ ] **Commit**:
```bash
git add .juejin-publish/29-*/ .juejin-publish/30-*/
git commit -m "feat(publish-juejin): 29-30 期掘金渠道包就位"
```

---

## Task 12:知乎发稿草稿(content-publisher + §7.4 门禁)

**Files:**
- 无新文件(Playwright 操作 + 浏览器状态)

**发稿前置门禁(强制作,来源 §七)**:
**主编必须先用 `question` 工具向用户确认**:"当前内容已完成主编验收和审核初审,是否确认开始发布到知乎草稿?"

**Step 12.1**:主编发起门禁问答。用户明确确认后,启动知乎 Playwright。
**Step 12.2**:按 `browser-playbook.md` 执行 Playwright 操作,创建草稿。
**Step 12.3**:草稿保存,告知用户手动发布。

**Definition of Done**:
- [ ] 知乎两个草稿保存成功
- [ ] 等待用户手动发布,不主动点击发布按钮

(发布后由 Task 15 链接捕获)

---

## Task 13:CSDN 发稿草稿(content-publisher + §7.4 门禁)

**Files:**
- 无新文件

**发稿前置门禁**:与 Task 12 同,但**每个平台单独问一次,不得合并**——CSDN 发稿前主编再次发起 question。

**Step 13**:按 §7.4 CSDN 工作流六步顺序:
1. 正文注入(execCommand('insertText'))
2. 配图锚点插入
3. 发布设置合法顺序
4. 最终状态 = 草稿

**Definition of Done**:
- [ ] CSDN 两个草稿保存成功

---

## Task 14:掘金发稿草稿(content-publisher + §7.4 门禁)

**Step 14**:与 Task 12/13 同,但走掘金工作流。

**Definition of Done**:
- [ ] 掘金两个草稿保存成功

---

## Task 15:发布链接捕获与归档(content-master + §7.3)

**Files:**
- Modify: `AGENTS.md` §二 进度表
- Modify: `.zhihu-publish/*/metadata.json`
- Modify: `.csdn-publish/*/metadata.json`
- Modify: `.juejin-publish/*/metadata.json`
- Modify: `README.md` 进度表

**承接**:用户手动发布后,浏览器自动跳转文章详情页。

**Step 15.1**:用户告知"已发布"或主编自动检测到浏览器跳转后,读取当前 URL,确认是文章详情页(包含文章 ID/路径)。
**Step 15.2**:更新 AGENTS.md §二 进度表对应平台列;同步更新对应渠道包 metadata.json。
**Step 15.3**:**掘金链接归一**(`spost/` 自动审核中 → `post/` 审核通过,进度表一律归档 `post/` 正式格式)。
**Step 15.4**:三平台链接齐全后,在进度表状态列追加"全平台已发布"标记。

**Definition of Done**:
- [ ] 三平台 × 两篇 共 6 个 URL 已捕获
- [ ] AGENTS.md §二 + README.md 已同步
- [ ] 渠道包 metadata.json 已同步

- [ ] **Commit**:
```bash
git add AGENTS.md README.md .zhihu-publish/*/metadata.json .csdn-publish/*/metadata.json .juejin-publish/*/metadata.json
git commit -m "docs(publish): 29-30 期双篇全平台链接捕获归档"
```

---

## Task 16:跨期复盘(content-auditor + content-master)

**Files:**
- Create: `audit/29-30-retrospective.md`

**承接**:Task 15 全部归档完成。

**Step 16.1**:对照 `audit/27-28-retrospective.md` 模板撰写跨期复盘,涵盖:
- 哪些环节效率高可复盘
- 哪些环节踩坑/返工
- 5 个 reviewer 观察点的处理是否真有效(比喻体系是否避免了重复、术语节奏是否有助读、标题调性是否改善)
- 30 篇与 28 篇的差异化是否成立(避免换皮的目的是否达到)
- DDD 知识体系三模块在一篇里是否真正能讲透(若不能需要给下一篇反馈)
- 团队协作纪律层面有无新约束/红线

**Step 16.2**:主编与团队对齐复盘结论,更新 `AGENTS.md` §七 维护约定若有新沉淀。

**Definition of Done**:
- [ ] 复盘报告落盘 `audit/29-30-retrospective.md`
- [ ] 与 27-28 复盘做对比,识别可沉淀的经验

- [ ] **Commit**:
```bash
git add audit/29-30-retrospective.md
git commit -m "docs(retrospective): 29-30 期跨期复盘"
```

---

## Task Sequencing & Dependencies

```text
[Task 1: 调研] ────┬──> [Task 3: 29 撰稿] ──> [Task 5.1: 29 审核] ──> [Task 6: 29 配图] ──> [Task 8.1: 校对] ─┐
                   └──> [Task 4: 30 撰稿] ──> [Task 5.2: 30 审核] ──> [Task 7: 30 配图] ──> [Task 8.2: 校对] ─┤
                   └──> [Task 2: 撰稿简报] ─────────────────────────────────────────────────────────────┤
                                                                                                        ↓
                                                       [Task 9/10/11: 三平台渠道包(可并行)] ──────────→ │
                                                                                                        ↓
                                          [Task 12/13/14: 三平台发稿草稿(门禁 × 3)]────────────────→[Task 15: 链接归档]
                                                                                                        ↓
                                                                                          [Task 16: 跨期复盘]
```

- **可并行点**:Task 3/4(撰稿)与 Task 5(审核)与 Task 6/7(配图)在自己对应篇内部线性,但两篇之间可并行(29 撰稿 + 30 撰稿 + 调研 + 简报可并行启动);Task 9/10/11 渠道包在完稿后可三平台并行。

---

## Self-Review(本次规划自审)

**1. Spec 覆盖**:29 篇 spec 七要素(核心论点/比喻体系/三模块/承接口/配图清单/术语节奏/品牌钩子)、30 篇 spec 七要素(核心论点/比喻体系/四阶段/叙事重心/framework 锚点/品牌钩子)、AGENTS.md §五/§六/§七 全部约束,均在 Task 3-8 中有对应执行任务。✅

**2. Placeholder 扫描**:全部任务步骤均含具体动作、文件路径、产出物、commit 命令;无 TBD/TODO。✅

**3. 类型一致性**:本计划是内容创作流程,不是软件开发,所以无类型/接口 drift 风险。但 Task 间产出依赖清晰——调研(Task 1)→ 简报(Task 2)+ 撰稿(Task 3/4)→ 审核(Task 5)→ 配图(Task 6/7)→ 校对(Task 8)→ 渠道(Task 9-11)→ 发稿(Task 12-14)→ 归档(Task 15)→ 复盘(Task 16),线性依赖清晰。✅

**4. 节奏一致性**:Task 12-14 严格遵循 §7.4 发稿前置门禁(每个平台独立 question,不得合并、不得绕过);Task 15 遵循 §7.3 链接自动归档 + 掘金 spost→post 归一。✅

**5. 全局约束覆盖**:写作纪律(§5)、品牌串联(§6)、维护约定(§七)均在每个任务 DoD 中显式列出或隐含。✅

---

## 执行起点

**Task 1 优先启动**(content-researcher),同时主编(content-master)并行启动 Task 2(撰稿简报)。两份准备就位后启动 Task 3/4 撰稿。

**批准人**:content-master(主编)= 需求方在我(本对话)与 5 专员协作中的代理。任何"修改要求"由主编统一收口后指派专员返工。
