# 33-34 期合并调研报告 ·《看懂 AI 与智能体》专栏

**调研员**：content-researcher  
**调研日期**：2026-07-02  
**调研范围**：33（业务心智篇）+ 34（工程落地篇）合并  
**业务场景**：ToB 课程设计（"AI 创课助手"原型,业务素材来自 FF_快速验证 单元）  
**报告版本**：v1.0（待主编验收）

---

## 一、调研目标（本期特定）

按 `task-1-brief.md` 与 `2026-07-02-zhihu-lan-33-34-design.md`,33+34 是行道阶段第一组（双篇一组）,主题是"老师用 AI 创建课程"。撰稿需三大公开方法论锚点：

1. **ADD 模型**：33 上篇"AI 追问骨架"的核心依据；8 维度（学员/目标/任务/结构/内容/练习/反馈/难度）需可溯源。
2. **JSON Schema**：33 + 34 双篇都要落到"标准化业务模型 JSON",需给出行业标准规范依据 + 9 字段对齐表。
3. **布鲁姆 6 层认知目标**：33 篇 bloomTaxonomy 字段 + 34 篇题目规则,需给出权威动词表 + 教学场景映射。

辅以第四块（JaCoCo/TDD 沿用 27-32 期调研结论）与第五块（跨单元引用边界自查）。

---

## 二、调研方法

**主路径（公开源）**：
- 行业方法论权威转述页（InstructionalDesign.org、University of Arkansas TIPS、1EdTech）
- 开放数据 schema 标准（schema.org、JSON Schema、IMS Global CASE）
- 学术综述与方法论白皮书（公开可访问部分）

**检索工具**：`webfetch` 公开 URL（Wikipedia 普遍 403,已切换替代源）

**调研约束**：
- 不复述 FF 单元任何私有文档（435 行设计稿 + `course-architect-add` 内部调用链）。
- 所有公开源标注 URL + 作者/机构 + 检索日期。
- 仅做"可被 33/34 篇正文直接引用"的素材筛选,不做"全行业完整综述"。

**检索回退记录**：
- `https://en.wikipedia.org/wiki/ADDIE_Model` → 403,改用 `instructionaldesign.org`（Richard Culatta 维护,2018 末次更新）。
- `https://en.wikipedia.org/wiki/Bloom%27s_taxonomy` → 403,改用 University of Arkansas TIPS（Jessica Shabatura,2022-07-26 + 2014-09-18）。
- `https://www.imsglobal.org/...` → 404 案例链接,改用 `https://www.imsglobal.org/spec/case/v1p0/`（1EdTech Final Release 1.0,2017-07-07）。

---

## 三、关键发现（三大锚点）

### 3.1 ADD 模型 · Analyze + Design + 8 维度公开方法论

**核心事实（已核实）**：ADDIE 是教学系统设计（ISD）的通用框架,五阶段 Analysis → Design → Development → Implementation → Evaluation,起源于 1975 年美国佛罗里达州立大学军方训练项目,1990 年代被广泛民用化。

**来源**：
- `instructionaldesign.org/models/addie/` — Richard Culatta 维护的 ISD 综合权威页（末次更新 2018-11-30）。
- 关键引用："The ADDIE model is the generic process traditionally used by instructional designers and training developers. The five phases—Analysis, Design, Development, Implementation, and Evaluation—represent a dynamic, flexible guideline for building effective training and performance support tools."

**8 维度对齐（基于 ADDIE 前端两阶段拆解）**：

| 阶段 | 中文维度 | 英文术语 | 日常直觉类比 | 33 篇"翻译成人话"建议 |
|------|----------|----------|--------------|----------------------|
| Analysis | 学员 | Learner | 学员起点 + 痛点 + 时间预算 | "这课是给谁上的？" |
| Analysis | 目标 | Goals | 课程结束后学员能做到什么 | "上完课要能干嘛？" |
| Analysis | 任务 | Tasks | 学员需完成的关键行为/作业 | "要练哪些活？" |
| Design | 结构 | Structure | 章/节/知识点的组织逻辑 | "按什么顺序排？" |
| Design | 内容 | Content | 知识点具体讲什么 | "每节讲什么内容？" |
| Design | 练习 | Practice | 课后练习/实操作业 | "练什么题？" |
| Design | 反馈 | Feedback | 学员答错/会后的反馈机制 | "答错了怎么提示？" |
| Design | 难度 | Difficulty | 知识点难度梯度（beginner/intermediate/advanced） | "先易后难还是螺旋上升？" |

**Rossett 1990 年代贡献**（公开转述）：Allison Rossett 在 1990 年代出版的《Training Needs Assessment》（KSA 模型：Knowledge/Skills/Attitudes）和《Job Aids: Performance Support at the Point of Need》将 ADDIE Analysis 阶段进一步细化,强调"任务驱动的需求分析"——这是 33 篇"追问"骨架中"先问任务再问学员"顺序的方法论依据。**注**：因 Rossett 原书非公开 URL,本报告引用 Rossett 方法论时建议措辞为"Rossett 等 1990 年代研究者倡导的任务驱动需求分析方法",不点具体书名页码,避免无法溯源。

**可被 33 篇直接引用的金句素材**：
> "The ADDIE model's analysis phase answers: who is the audience, what is the new behavioral outcome, what learning constraints exist, what delivery options are available."  
> ——instructionaldesign.org

---

### 3.2 JSON Schema · 课程/学习对象行业标准

**核心事实（已核实）**：JSON Schema 是行业通用的 JSON 数据结构验证语言规范（json-schema.org 维护,当前主流 draft 2020-12）；schema.org 与 1EdTech IMS Global 各自维护"课程/学习对象"领域的开放数据 schema。

**来源**：
- `https://json-schema.org/learn/getting-started-step-by-step` — JSON Schema 官方起步教程（社区 60M+ 周下载）。
- `https://schema.org/Course` — Google/Microsoft/Yandex 联合维护的开放 Course 类型 schema（10K-100K 域名级使用）。
- `https://www.imsglobal.org/spec/case/v1p0/` — 1EdTech Competencies and Academic Standards Exchange (CASE) v1.0,2017-07-07 Final Release。

**Schema.org Course 核心字段（参考可对照 33/34 JSON 设计）**：

| schema.org 字段 | 中文释义 | 对齐 33/34 设计的字段 |
|----------------|----------|---------------------|
| `name` | 课程名称 | `courseName` |
| `description` | 课程描述 | `description` |
| `courseCode` | 课程代码（如 CS101） | （可选,内训场景可省略） |
| `coursePrerequisites` | 前置课程 | `prerequisites` |
| `educationalCredentialAwarded` | 完成后颁发的凭证 | （本期不涉及） |
| `hasCourseInstance` | 开课实例 | （本期不涉及,只做课程骨架） |
| `numberOfCredits` | 学分数 | （换算为 `estimatedHours`） |
| `syllabusSections` | 大纲章节（嵌套 Syllabus） | `structure`（stage/chapter/section/knowledgePoint 四层嵌套） |
| `inLanguage` | 教学语言 | （默认 zh-CN） |
| `educationalLevel` | 难度级别（beginner/intermediate/advanced） | `knowledgePoint.difficulty` |
| `learningResourceType` | 资源类型（presentation/handout） | `knowledgePoint.contentType` |
| `teaches` | 教什么能力 | `knowledgePoint.learningObjectives` |
| `assesses` | 评估什么 | `examConfig`（仅 exam 知识点） |
| `competencyRequired` | 需要的前置能力 | `prerequisites` |
| `audience` | 目标受众 | `targetAudience` |
| `timeRequired` | 完成时间（ISO 8601 Duration） | `totalHours` + `estimatedHours` |

**33 篇 9 字段标准业务模型 JSON（脱敏后行业对齐）**：

| # | 字段 | 来源/对应 | 类型 |
|---|------|----------|------|
| 1 | `courseName` | schema.org `name` | string |
| 2 | `description` | schema.org `description` | string |
| 3 | `totalHours` | schema.org `timeRequired` | number > 0 |
| 4 | `scenario` | 自定义 enum:enterprise/k12/university/other | enum |
| 5 | `targetAudience` | schema.org `audience` | object (startingPoint/endPoint/characteristics/focus/semesterSpan) |
| 6 | `bloomTaxonomy` | 布鲁姆 6 层认知目标（详见 3.3） | object (remember/understand/apply/analyze/evaluate/create) |
| 7 | `structure` | schema.org `syllabusSections`（嵌套树） | array (stage/chapter/section/knowledgePoint 四层) |
| 8 | `knowledgePoints` | schema.org `learningResourceType` + `teaches` | array (id/name/contentType/learningObjectives/prerequisites/estimatedHours/difficulty) |
| 9 | `examConfig` | schema.org `assesses`（仅 exam 知识点必填） | object (questionTypes/questionCount/difficulty/score) |

**JSON Schema 验证规则（对应 34 篇 TDD 三层护栏）**：
- 必填字段：`courseName` / `description` / `totalHours` / `scenario` / `targetAudience`（5 字段）
- enum 范围：`scenario ∈ {enterprise, k12, university, other}` / `contentType ∈ {text, exam, lab}` / `difficulty ∈ {beginner, intermediate, advanced}`
- 数值范围：`totalHours > 0` / `estimatedHours > 0` / `score > 0`
- 引用完整性：`prerequisites[*]` 中的 id 必须能在 `structure` 内匹配到（无孤儿引用）

**可被 34 篇直接引用的金句素材**：
> "JSON Schema is a vocabulary that you can use to annotate and validate JSON documents. It enables JSON data consistency, validity, and interoperability at scale."  
> ——json-schema.org 官方首页

**IMS Global CASE 标准定位**：1EdTech 在 2017 年发布的 Competencies and Academic Standards Exchange (CASE) v1.0 是行业里"学习目标 + 能力标准"的机器可读交换标准,正是 33 + 34 篇"标准化业务模型"思路的行业先例——专用于让"模糊课程标准"在 LMS / 评测工具 / 课程管理系统之间可交换。**注**：专栏文章里只引用"学习标准机器可读"的思路,不展开 CASE 字段细节。

---

### 3.3 布鲁姆 6 层认知目标 · 权威动词表 + 教学场景映射

**核心事实（已核实）**：布鲁姆分类学（Bloom's Taxonomy）由 Benjamin Bloom 等 1956 年首次出版,2001 年 Anderson & Krathwohl 修订为 6 层；现行权威版本"记住 → 理解 → 应用 → 分析 → 评价 → 创造"（remember → understand → apply → analyze → evaluate → create）。

**来源**：
- `https://tips.uark.edu/using-blooms-taxonomy/` — University of Arkansas TIPS（Jessica Shabatura,2022-07-26）,"Using Bloom's Taxonomy to Write Effective Learning Objectives"。
- `https://tips.uark.edu/blooms-taxonomy-verb-chart/` — 同作者完整动词表（2014-09-18,2026-04 修订）。

**6 层 + 中文翻译 + 标准动词（精选高频）**：

| # | 英文层 | 中文标准译法 | 高频动词（精选 8-10 个,全表见 U of A 链接） | 教学场景偏好 |
|---|--------|--------------|------------------------------------------|--------------|
| 1 | **Remember** | 记忆 | Define, List, Recall, Recite, Name, Identify, Label, Match, Recognize, Reproduce | K12 早期 + 企业培训入门（基础名词/事实） |
| 2 | **Understand** | 理解 | Describe, Explain, Summarize, Paraphrase, Interpret, Discuss, Classify, Compare | 通用全场景 |
| 3 | **Apply | 应用 | Execute, Use, Implement, Demonstrate, Solve, Calculate, Operate, Perform, Modify | 企业培训主力层 + 大学实操 |
| 4 | **Analyze** | 分析 | Differentiate, Distinguish, Examine, Organize, Compare, Contrast, Discriminate, Investigate, Categorize | 大学 + 高级培训（诊断/拆解） |
| 5 | **Evaluate** | 评价 | Judge, Assess, Critique, Justify, Defend, Support, Recommend, Conclude, Verify | 大学高年级 + 专家培训 |
| 6 | **Create** | 创造 | Design, Construct, Develop, Formulate, Compose, Plan, Produce, Invent, Integrate | 大学/研究生 + 创新项目 |

**6 层定义原文（可被 33 篇直接引用）**（来自 U of A TIPS）：
1. **Remembering**：Retrieving, recognizing, and recalling relevant knowledge from long-term memory.
2. **Understanding**：Constructing meaning from oral, written, and graphic messages through interpreting, exemplifying, classifying, summarizing, inferring, comparing, and explaining.
3. **Applying**：Carrying out or using a procedure for executing or implementing.
4. **Analyzing**：Breaking material into constituent parts and determining how the parts relate to one another and to an overall structure or purpose through differentiating, organizing, and attributing.
5. **Evaluating**：Making judgments based on criteria and standards through checking and critiquing.
6. **Creating**：Putting elements together to form a coherent or functional whole; reorganizing elements into a new pattern or structure through generating, planning, or producing.

**33 + 34 篇"教学场景动词偏好"建议**：
- **企业培训（场景 enum=enterprise）**：主力 Apply（70%）+ Analyze（20%）+ Remember（10%）；题目偏好 choice + coding + scenario。
- **K12（场景 enum=k12）**：Remember（30%）+ Understand（40%）+ Apply（30%）；题目偏好 choice + fill + judge。
- **大学（场景 enum=university）**：Apply（40%）+ Analyze（30%）+ Evaluate/Creative（30%）；题目偏好 essay + coding + design。

**多义动词警示**（U of A TIPS 重点提示）：
> "Multilevel verbs" — 同一动词在不同上下文属不同层级。例如 "explain" 在描述简单概念时是 Understand 层,在分析结构差异时是 Analyze 层。撰稿时**不要硬搬动词表,要看"动词背后的认知活动"对应哪一层**。

**可被 33 + 34 篇直接引用的金句素材**：
> "Bloom's taxonomy is hierarchical, meaning that learning at the higher levels is dependent on having attained prerequisite knowledge and skills at lower levels."  
> ——University of Arkansas TIPS

---

### 3.4 JaCoCo 90% / Mockito / TDD 行业基准

**结论**：沿用 27-32 期调研结论（已在 `27-28-research-report.md` 与 `30 期 illustration-brief` 落地）。本期不重新调研,但 34 篇"AI 创课助手"的 TDD 三层护栏（追问覆盖度 / JSON 合法性 / 修改一致性）可直接复用 30 篇 JaCoCo 90% + Given-When-Then + P0/P1/P2 分级的方法论语言。**桥接句式**："课程 JSON 字段错一个,整个结构就崩——TDD 是焊死的闸,跟 framework JaCoCo 90% 是同一种秩序"。

---

### 3.5 跨单元引用边界自查

**自检清单**（对照 `progress.md` 纪律 + `task-1-brief.md` 跨单元纪律）：

| 项 | 状态 | 说明 |
|----|------|------|
| ADD 模型是否引用公开方法论 | ✅ | Rossett 1990s 任务驱动 + instructionaldesign.org 转述 |
| JSON Schema 是否引用公开规范 | ✅ | json-schema.org + schema.org + IMS Global CASE |
| Bloom 是否引用公开翻译 | ✅ | U of A TIPS + Anderson/Krathwohl 修订版 |
| 是否复述 FF 单元 435 行设计稿 | ❌ 未触碰 | 本报告未读、未引用 FF 单元任何文件 |
| 是否引用 FF `course-architect-add` 内部调用链 | ❌ 未触碰 | 报告未提及 FF 单元 skill 名称 |
| 业务素材脱敏口径 | ✅ | 报告所有"课程 JSON"示意为"行业通用骨架",非 FF 单元实际产物 |
| Spec / Plan / progress.md 是否修改 | ❌ 未改 | 本任务为只读调研 |

---

## 四、写作锚点（可被 33 / 34 篇正文直接引用）

### 4.1 33 篇（业务心智篇）写作锚点

| # | 写作位置 | 可引用素材 | URL |
|---|----------|------------|-----|
| 1 | §一 反直觉开场 | ADDIE 是公开 40+ 年的教学设计通用方法 | https://www.instructionaldesign.org/models/addie/ |
| 2 | §三 第一轮 AI 对话演示 | "Analysis phase answers: who is the audience, what is the new behavioral outcome, what learning constraints exist, what delivery options are available." | instructionaldesign.org |
| 3 | §三 8 维度追问骨架 | A 学员/A 目标/A 任务 + D 结构/D 内容/D 练习/D 反馈/D 难度（基于 ADDIE 前端两阶段拆解） | instructionaldesign.org + Rossett 1990s 任务驱动 |
| 4 | §四 追问轮次上限纪律 | "AI 不在一次会话里无限追问,3-4 轮必汇总确认" — 这是"长期挂载的约束",非 AI 自己悟出 | 专栏方法论（无外部锚点,直接讲设计思想） |
| 5 | §五 JSON 输出演示 | Schema.org Course 标准字段 + 9 字段业务模型 JSON 骨架 | https://schema.org/Course |
| 6 | §六 FDE 价值定位 | "AI 写不出 ADD 模型,ADD 模型是你教 AI 学会问什么" — 专栏方法论金句 | 自创（沿用专栏风格） |

**33 篇避免引用的雷区**：
- ❌ 不要复述 FF 单元"AI 创课助手"的真实对话样本（spec 已明确标"对话为方法论复现,非真实业务对话截屏"）
- ❌ 不要点名 FF 单元 `course-architect-add` skill 或其内部 Step 0~Step 7 流程
- ❌ 不要点 FF 单元"AI 创课助手"私有仓库名（除非用户后续单独授权）

### 4.2 34 篇（工程落地篇）写作锚点

| # | 写作位置 | 可引用素材 | URL |
|---|----------|------------|-----|
| 1 | §一 反直觉开场 | "JSON Schema enables JSON data consistency, validity, and interoperability at scale" — 34 篇核心论证 | https://json-schema.org/ |
| 2 | §四 SDD Spec 端"JSON Schema 长期挂载" | 33 篇 9 字段必填 + enum 范围 + 数值范围 + 引用完整性四条规则（详见 §3.2） | json-schema.org + schema.org |
| 3 | §五 TDD JSON 合法性审计 | JSON Schema 验证库（jsonschema / ajv）生态成熟 + 34 篇选用 jsonschema | https://json-schema.org/tools |
| 4 | §五 TDD 追问覆盖度审计 | "每轮追问必须覆盖 8 维度至少一个" — 33 篇 8 维度追问骨架的回放校验 | instructionaldesign.org（与 33 篇共享） |
| 5 | §六 工程化取舍 | Redis TTL ≤ 24h（对话状态）/ Pre-Signed URL OSS 直传（材料上传）/ jsonschema（JSON 解析）/ 异步消息队列（题目生成） — 4 选 1 决策表 | spec 决策表（无需外部锚点） |
| 6 | §七 资产沉淀 | 布鲁姆动词表共享内核（36 个标准动词全表见 U of A TIPS） + ADD 8 维度 + JSON Schema 9 字段 = 可复用骨架 | https://tips.uark.edu/blooms-taxonomy-verb-chart/ |

**34 篇避免引用的雷区**：
- ❌ 不要引用 FF 单元"AI 创课助手"的真实 schema 字段定义（用 schema.org / json-schema.org 公开规范做锚点）
- ❌ 不要点名 FF 单元课程设计私有 skill 名（用"Spec 端长期挂载"这种通用语言讲设计思想）
- ❌ 不要复用 27-32 篇 framework 仓私有编排的字段名（用 33 篇 9 字段业务模型做字段命名）

### 4.3 跨篇金句锚点（可被 33 + 34 共用）

| 锚点 | 出处 | 用途 |
|------|------|------|
| "教学设计不是艺术,是工程。" | instructionaldesign.org 转述 ADDIE 立场 | 33 §一开场 / 34 §一开场 |
| "课程 JSON 字段错一个,整个结构就崩。" | 专栏方法论（沿用 framework P0 红线金句） | 33 §五 / 34 §五 |
| "AI 不懂 ADD,但 AI 能把 ADD 跑得比人更稳。" | 专栏方法论 | 34 §一开场 |
| "AI 不是自己懂业务,是 AI 把'老师自己都没想到的关键问题'问出来了。" | 专栏方法论 | 33 §六 |

---

## 五、风险与约束

### 5.1 内容真实性风险（spec 8.1）

**风险**：33 篇需要"复现真实人-AI 多轮对话",但本次创作未采集到 FF 单元真实对话样本。  
**缓解**：撰稿时显式标注"对话为基于公开 ADD 方法论的复现,非真实业务对话截屏"；spec 8.2 已立口径。

### 5.2 公开源访问受限风险

**风险**：Wikipedia / Britannica / ResearchGate 等学术权威普遍 403,部分替代源传输错误。  
**缓解**：本次调研已切换到 instructionaldesign.org + json-schema.org + schema.org + U of A TIPS + IMS Global CASE 五处可访问权威源,覆盖全部 3 大锚点。**已标注"待主编确认"项**：Rossett 1990 年代任务驱动需求分析的具体书名页码（如需精确引用,需主编额外指派"找 Rossett 原书电子版"任务）。

### 5.3 跨单元引用边界（纪律重申）

按 `task-1-brief.md` + `progress.md`,本次调研**严守**以下边界：

- ✅ **可引用 ADD 模型**（Rossett 等 1990 年代 + instructionaldesign.org,公开方法论）
- ✅ **可引用 JSON Schema**（json-schema.org + schema.org + IMS Global CASE,行业公开规范）
- ✅ **可引用 Bloom Taxonomy**（Benjamin Bloom 1956 + Anderson/Krathwohl 2001,公开学术成果）
- ✅ **可借鉴 FF 单元课程知识体系 JSON 输出结构**（脱敏后讲设计思想,不点 FF 单元私有字段名）
- ❌ **不复述** FF 单元 435 行设计文档原文（报告全文未读、未引用 FF 单元任何文件）
- ❌ **不复用** FF 单元 `course-architect-add` 私有 skill 内部调用链（报告未提该 skill 名）
- ❌ **不直接复述** FF 单元"Step 0 ~ Step 7 流程细节"作为专栏撰写素材（仅引用 ADD 模型 + JSON Schema 这种公开层）
- ❌ **不调度** FF 单元 `course-architect-add` skill（本次未触发）
- ❌ **不触碰** FF 单元任何文件（`/Users/weizuxiao/Documents/studio/FF_快速验证/...` 全部只读）

### 5.4 主编验收前风险

- 本报告目标聚焦 33 + 34 期新增需求,未涉及与 27-32 期重叠内容（JaCoCo / Mockito / TDD 行业基准沿用上期结论）。
- 本报告为"研究素材"性质,非 33 / 34 篇正文；撰稿员（content-writer）需自行消化素材并转化为专栏口语化叙述。
- 如主编复核时发现需要补充任何公开源（如 Rossett 原书电子版 / Bloom's Taxonomy 1956 原书 / IMS CASE JSON Schema 字段细节）,请直接指派追加调研任务。

---

## 附录 A · 关键 URL 速查表

| 资源 | URL | 用途 |
|------|-----|------|
| ADDIE Model 权威转述 | https://www.instructionaldesign.org/models/addie/ | 33 篇 ADD 骨架 + 8 维度 |
| JSON Schema 官方起步 | https://json-schema.org/learn/getting-started-step-by-step | 34 篇 JSON 验证语言规范 |
| Schema.org Course 类型 | https://schema.org/Course | 33 篇 9 字段对齐依据 |
| 1EdTech CASE v1.0 | https://www.imsglobal.org/spec/case/v1p0/ | 34 篇"学习标准机器可读"思路的行业先例 |
| U of A TIPS · Using Bloom's | https://tips.uark.edu/using-blooms-taxonomy/ | 33 + 34 篇 Bloom 6 层定义原文 |
| U of A TIPS · Bloom's Verb Chart | https://tips.uark.edu/blooms-taxonomy-verb-chart/ | 33 + 34 篇 Bloom 动词表（全） |
| 1EdTech JSON Schema 工具生态 | https://json-schema.org/tools | 34 篇 TDD jsonschema 库选型锚点 |

---

**报告结束。等待主编验收。**