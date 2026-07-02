# 33 篇配图索引

> **文章**:老师想 AI 帮忙做课,AI 却问了一堆"离谱"的问题——我才明白真懂业务的是人不是 AI
> **风格**:手绘教育插图风格(hand-drawn educational framework diagram) — 暖色调奶油纸背景 / 黑色草图线条 / 柔和粉彩色块(主色橙绿蓝) / 手写体中文标签 / 右下角 ArchAIHarness 水印
> **生成工具**:豆包 Seedream 5.0 Lite(baoyu-image-gen batch mode)
> **生成日期**:2026-07-02

---

## 封面 cover

- **文件**:`cover.png`
- **brief 图编号**:图 1(封面)
- **核心概念**:专栏 33 篇首图——老师(大厨)随口说一句"我要做 Java 培训"(原始需求),身边 AI 助手(副厨)用 ADD 教学设计菜谱表帮他把模糊念头剥到"标准化课程";温暖专业、同辈感。
- **视觉锚点**:老师大厨(白高厨帽 + 橙色围裙) + AI 副厨(蓝副厨帽 + 蓝围裙) + ADD 教学设计菜谱表 8 章节(学员/目标/任务/结构/内容/练习/反馈/难度) + 桌面半杯咖啡 + 窗户透光
- **不插入正文**:✅ 仅作各平台发布封面

---

## 正文配图(按出现顺序)

### 01 — 原始需求录:老师一句话,AI 准备追问

- **文件**:`01-raw-requirement-bubble-and-laptop.png`
- **brief 图编号**:图 2(01)
- **对应正文位置**:`@@@IMG_1@@@`(正文第 23 行,开头"下面我们一段一段拆"之后)
- **核心概念**:典型 ToB 业务原始需求 = 碎片化 + 口语化 + 没结构;AI 不直接干,先停下来问。
- **视觉锚点**:上半对话气泡(老师一句话原始需求 + 戴学士帽老师小头像 + 橙色叹号警示) + 下半笔记本(AI 助手界面 + "我先问 3-4 个问题,咱们把课程需求剥清楚再开始写") + 中间虚线箭头 + 标签"AI 不直接干 · 先停下来问"
- **正文引用**:`![老师一句话原始需求,从口语化到 AI 准备追问的全过程](assets/33_老师想AI帮忙做课——AI却问了一堆离谱的问题——我才明白真懂业务的是人不是AI/01-raw-requirement-bubble-and-laptop.png)`

---

### 02 — 追问雷达图:ADD 8 维度挨个追,3 轮覆盖

- **文件**:`02-radar-add-eight-dimensions.png`
- **brief 图编号**:图 3(02)
- **对应正文位置**:`@@@IMG_2@@@`(正文第 183 行,§三末尾"下面我把这段对话的关键骨架画成雷达图"之后)
- **核心概念**:AI 按 ADD 8 维度追问的覆盖广度——8 顶点(学员/目标/任务/结构/内容/练习/反馈/难度)+ 三层蓝色叠加(3 轮追问累计覆盖)+ 每个顶点外侧对话气泡线(追问话术示例)。
- **视觉锚点**:八边形雷达图 + 中心 AI 助手橙色圆点 + 3 层蓝色多边形(浅/中/深)+ 8 个对话气泡追问示例 + 标语"3-4 轮覆盖 8 个维度 · 不允许无限追问"
- **正文引用**:`![AI 按 ADD 8 维度追问、3 轮覆盖的雷达图](assets/33_老师想AI帮忙做课——AI却问了一堆离谱的问题——我才明白真懂业务的是人不是AI/02-radar-add-eight-dimensions.png)`

---

### 03 — 对话时间线:4 轮追问 + 1 轮汇总硬约束

- **文件**:`03-dialogue-timeline-with-summary-gate.png`
- **brief 图编号**:图 4(03)
- **对应正文位置**:`@@@IMG_3@@@`(正文第 221 行,§四"4 轮追问 + 1 轮汇总硬约束"处)
- **核心概念**:原始需求 → 多轮追问 → 汇总确认的完整对话流;4 轮追问 + 1 轮汇总 = Spec 端长期挂载的死规矩,不是 AI 自己学到的。
- **视觉锚点**:横向时间线 + 4 个圆形锚点(橙/蓝/绿/红,4 轮)+ 老师橙色气泡 + AI 蓝色气泡(每轮对话)+ 最右红色铁门"汇总闸"(挂"硬约束 · 必须汇总确认" / "3-4 轮上限纪律")
- **正文引用**:`![4 轮追问 + 1 轮汇总确认的对话时间线,最右挂着红色汇总闸](assets/33_老师想AI帮忙做课——AI却问了一堆离谱的问题——我才明白真懂业务的是人不是AI/03-dialogue-timeline-with-summary-gate.png)`

---

### 04 — JSON 全景:9 字段 + 嵌套 4 层结构

- **文件**:`04-json-knowledge-tree.png`
- **brief 图编号**:图 5(04)
- **对应正文位置**:`@@@IMG_4@@@`(正文第 580 行,§五末尾"下面这张图把 JSON 的层级树画出来"之后)
- **核心概念**:最终产物"标准化业务模型 JSON"长什么样——9 个顶层字段 + structure 字段嵌套 4 层(stage → chapter → section → knowledgePoint → examConfig);机器可读、可被下游 Agent 复用。
- **视觉锚点**:根节点"课程知识体系 JSON (根)" + 9 个一级节点(courseName/description/totalHours/scenario/targetAudience/bloomTaxonomy/structure/knowledgePoints/examConfig)+ structure 节点进一步向下分叉 4 层 + 右下角小标注牌"机器可读 / 可被下游 Agent 复用 / 标准菜谱的最终形态"
- **正文引用**:`![标准化课程业务模型 JSON 的 9 字段 + 嵌套 4 层树状图](assets/33_老师想AI帮忙做课——AI却问了一堆离谱的问题——我才明白真懂业务的是人不是AI/04-json-knowledge-tree.png)`

---

### 05 — FDE 价值定位:老师 + FDE + AI 三方协作

- **文件**:`05-fde-three-way-collaboration.png`
- **brief 图编号**:图 6(05)
- **对应正文位置**:`@@@IMG_5@@@`(正文第 632 行,§六"下面这张三方对话协作图,把 FDE 在 ToB 业务里的角色画出来"之后)
- **核心概念**:FDE 在 AI 时代的核心价值 = 让 AI 知道问什么——人(老师 + FDE 双重身份)+ AI 三方协作;FDE 在中间做"业务翻译官",老师是业务专家,AI 是执行引擎。
- **视觉锚点**:三人横向构图(老师学士帽 + FDE 工程师帽手举"业务翻译手册" + 橙色 AI 机器人)+ 三人各自彩色背景阴影(蓝/橙/绿)+ 各气泡对话 + 协作三角形 + 底部金句"未来真正会用 AI 做业务的人,不是会写 Prompt 的人,是会教 AI 问什么的人"
- **正文引用**:`![老师、FDE、AI 三方对话协作关系图,FDE 在中间做业务翻译官](assets/33_老师想AI帮忙做课——AI却问了一堆离谱的问题——我才明白真懂业务的是人不是AI/05-fde-three-way-collaboration.png)`

---

## 目录结构

```
assets/33_老师想AI帮忙做课——AI却问了一堆离谱的问题——我才明白真懂业务的是人不是AI/
├── README.md                                              # 本索引文件
├── batch.json                                             # 批量生成配置(baoyu-image-gen)
├── cover.png                                              # 封面(不插入正文)
├── 01-raw-requirement-bubble-and-laptop.png               # 正文图 1
├── 02-radar-add-eight-dimensions.png                      # 正文图 2
├── 03-dialogue-timeline-with-summary-gate.png             # 正文图 3
├── 04-json-knowledge-tree.png                             # 正文图 4
├── 05-fde-three-way-collaboration.png                     # 正文图 5
└── prompts/                                               # prompt 源文件
    ├── cover.md
    ├── 01-raw-requirement-bubble-and-laptop.md
    ├── 02-radar-add-eight-dimensions.md
    ├── 03-dialogue-timeline-with-summary-gate.md
    ├── 04-json-knowledge-tree.md
    └── 05-fde-three-way-collaboration.md
```

---

## 质量自检(2026-07-02)

- [x] 6 张图全部生成(5 正文 + 1 封面)
- [x] 中文标签清晰可读
- [x] 风格统一(暖色奶油纸 + 黑线 + 粉彩,主色橙/绿/蓝,符合专栏 §5.6 二)
- [x] 每张图与 brief 的"核心概念"对齐
- [x] 5 处 `@@@IMG_N@@@` 全部替换为 `![alt](path)` 形式
- [x] 封面 16:9 比例正确
- [x] 无深色背景、无 3D、无写实人物(符合 §5.6 二禁忌)
- [x] 右下角 ArchAIHarness 水印均在
- [x] README 索引完整

---

## 主编决断

按规则,本期配图已全部完成,提交主编校对。发布动作由主编手动触发,发布后链接由主编反馈给插画专员归档(对齐 §7.0 / §7.3)。
