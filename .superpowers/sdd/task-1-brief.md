# Task 1 Brief: 33-34 期合并调研

## 任务定位

为《看懂 AI 与智能体》专栏 33 + 34 期做调研。这两期是行道阶段第一组(双篇一组)，主题是"老师用 AI 创建课程"——即 ToB 课程设计业务。33 是"业务心智篇"(上篇),34 是"工程落地篇"(下篇)。

业务素材来自 FF_快速验证 单元已有项目 `AI创课助手`(435 行设计文档 + `course-architect-add` skill)。**但你需要调研的是"对外可引用层",不是 FF 私有内部细节**——参见下文"跨单元纪律"。

## 关键输入

| 文件 | 用途 |
|------|------|
| `docs/superpowers/specs/2026-07-02-zhihu-lan-33-34-design.md` | 完整方案(必读) |
| `docs/superpowers/plans/2026-07-02-zhihu-lan-33-34-plan.md` | 14 任务执行计划(本任务对应 Task 1) |
| `FF_快速验证/AI创课助手-知识体系生成Agent技能设计方案.md` | FF 单元业务素材(参考用,严守边界) |
| `../27-28-research-report.md`(114KB) | 上期调研报告,看完整结构模板 |
| `../30-illustration-brief.md`/`31-illustration-brief.md` | 看简单模板 |

## 跨单元纪律(必守)

- ✅ 可引用 ADD(Analyze + Design 教学设计模型,Rossett 等 1990 年代提出,公开方法论)
- ✅ 可引用 JSON Schema(行业通用规范)
- ✅ 可引用 Bloom Taxonomy(布鲁姆 6 层认知目标,公开翻译)
- ✅ 可借鉴 FF 单元的"课程知识体系 JSON 输出结构"(脱敏后讲设计思想)
- ❌ **不复述** FF 单元 435 行设计文档原文
- ❌ **不复用** FF 单元私有 skill 内部调用链
- ❌ **不直接复述** FF 单元的"Step 0 ~ Step 7 流程细节"作为专栏撰写素材(只能引用 ADD 模型 + JSON Schema 这种公开层)
- ❌ **不调度** FF 单元 `course-architect-add` skill

## 调研任务清单

按 `2026-07-02-zhihu-lan-33-34-plan.md` Task 1 的 Step 1.1 + Step 1.2 执行:

1. **ADD 模型公开方法论**——核实 ADD(Analyze + Design + Develop 三段)的原文出处和权威定义。
   - 找 2-3 处可引用的公开来源(Gary Kearsley / Allison Rossett 等 1990 年代著作原文或权威转述)
   - 把 ADD 8 维度(学员 / 目标 / 任务 / 结构 / 内容 / 练习 / 反馈 / 难度)准确列出
   - 给出每个维度的"日常直觉类比"(可被 33 篇"翻译成人话"段落直接引用)

2. **JSON Schema 行业标准**——调研"课程知识体系"通用 schema。
   - 关键词搜索:course schema, curriculum schema, knowledge point schema, learning objective
   - 公开样例:Coursera / edX / IMS Global Learning Consortium(LTI / CASE)等行业 schema 引用
   - 提炼核心 9 字段(对照 FF 设计):courseName / description / totalHours / scenario / targetAudience / bloomTaxonomy / structure / knowledgePoints / examConfig

3. **布鲁姆 6 层认知目标权威翻译**——记忆 / 理解 / 应用 / 分析 / 评价 / 创造的标准动词表。
   - 给出每层的 5-10 个常用动词(apply, analyze, design, evaluate 等)
   - 给出"教学场景映射"(企业培训 / K12 / 大学 各自的常用动词偏好)

4. **JaCoCo 90% / Mockito / TDD 行业基准**(沿用 27-32 期调研结论,无需重新查)

5. **跨单元引用边界自查**——对照 `.superpowers/sdd/progress.md` 的纪律清单自检。

## 调研报告产出

按 `27-28-research-report.md`(114KB)模板结构,但**目标聚焦 33-34 期新增需求**,篇幅建议 ≤ 8KB(本任务范围小,不需要 114KB 那么厚)。

结构:
1. 调研目标(本期特定)
2. 调研方法(公开源为主)
3. 关键发现(ADD / JSON Schema / Bloom 三大锚点)
4. 写作锚点(可被 33 / 34 篇直接引用的具体方法论原文 + URL)
5. **风险与约束**(FF 单元私有 skill 禁区 + 跨单元引用边界)

## 交付清单

| 路径 | 内容 |
|------|------|
| `research/33-34-research-report.md` | 调研报告主文 |

## 交付后

返回报告路径 + 主要发现摘要(≤ 5 行)+ 是否触发了任何问题(没有就回 NONE)。

## 不要做

- 不要写 33 / 34 篇正文
- 不要写 illustration-brief
- 不要调度任何 FF 单元 skill
- 不要触碰 FF 单元任何文件
- 不要修改本任务的输入文件(spec / plan / progress.md)
