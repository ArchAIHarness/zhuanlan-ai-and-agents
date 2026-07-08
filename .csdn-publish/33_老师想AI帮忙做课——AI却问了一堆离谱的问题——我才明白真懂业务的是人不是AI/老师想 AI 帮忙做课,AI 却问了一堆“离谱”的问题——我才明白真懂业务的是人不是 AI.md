
AI 越来越能干,你越来越不敢让它干活。

不是怕它写错代码——是怕它把一节课讲成另一个东西。

你让它给社招新人做个 Java 培训,它点头答应得很快,忘得更快。三天后它交给你一份大纲,你打开一看:18 章,从 Java 历史讲到 JVM 调优,再讲到设计模式,再讲到 Spring 源码。看上去很全。可你心里清楚——**这不是你想要的课**。你想要的是新人能用上的 40 小时速成,它给你的是"Java 百科全书"。

你跟它说不对。它点头,说"好的,我重写"。再交一份,还是不对。再来一次,还是不对。

你是不是也卡在这儿过?

不是 AI 太笨。是它从一开始就没弄明白你想要什么。它没问你"学员已经会什么"、"每天能学多久"、"40 小时后要能干嘛"。它没问你"按知识逻辑还是按任务逻辑排"、"哪些知识点配题、配什么题"。它一口气把"语料库里所有 Java 培训大纲的平均值"抄了一份给你。

你以为它懂。其实它不懂。

你最近开始觉得:AI 不是不聪明,是**没人教它问什么**。

这一篇我想跟你聊一件最近让我重新理解了一遍的事——**AI 时代的 FDE,不是去写代码的,是去给 AI 当"翻译官"的**。把老师那句含糊的"我要做 Java 培训",剥成 AI 听得懂、能跑、不会跑偏的标准化业务模型。这条路怎么走,我刚走完一段,拿出来给你看。

下面我们一段一段拆。


## 一、AI 不是自己懂业务,是它把"老师自己都没想到的关键问题"问出来了

你可能觉得这标题反了——AI 不是越来越能自己懂业务吗?给它一段上下文,给它几个例子,它就能模仿出像样的需求文档,还需要"问出来"?

听起来很有道理。可真实现场不是这样。

我先把现场摆给你看。我最近在做的一个 ToB 课程设计项目——给企业培训师、老师用 AI 把"模糊的创课念头"剥到"标准化的课程大纲"。我一开始也是按"AI 能写"思路干,随口说一句"我要给社招新人做个 Java 培训,40 小时,要有 Spring 全家桶"给它,它给我写出来一份看上去很像样的大纲。我打开看了一下,心里咯噔一下——这份大纲跟另外七份"我也能写"的大纲长得几乎一样。

**这才是问题。**

不是因为 AI 写得不好,而是它**写得过于像"AI 印象里的 Java 培训"**。它没问"社招新人起点是会 Java SE 还是没碰过 Java"、"40 小时是连续上课还是每周 5 小时×8 周"、"终点是要跟师傅带项目还是要独立 CRUD 模块"、"按 Java 知识逻辑排还是按问题逻辑排"、"Spring 全家桶包含哪些——Boot、Cloud、Security、数据,还是要 Spring 源码"。它把这些事全凭"印象"默认了。

我不是怪 AI。

AI 没见过你的学员,没听过你的预算,不知道你的项目压不压得住。它没这些信息,你让它"按业务来写",它只能写"印象里的业务"。

那怎么办?我后来才想明白——

**AI 不是自己懂业务,是 AI 把"老师自己都没想到的关键问题"问出来了。**

**AI 不是自己懂业务,是**人 + AI 一起**把模糊念头剥到可用边界。**

这两句你都得记牢。前一句说 AI 在追问什么,后一句说人和 AI 怎么一起做——它们是同一件事的两面。AI 不会自己懂业务,人才是业务的源头;但人不会系统追问,AI 才把追问变成结构化。**人出业务、AI 出结构,合在一起才是"可用边界"。**

这两句一起,才是这一篇的底色。

老师从业 5 年,他脑子里有一大堆"我以为大家都知道"的假设——学员会 Java SE、每天能学 1 小时、终点要会写 CRUD、Spring 是默认必学的。这些假设他从来没系统列过。可真要落到一份能直接拿去上课的课程大纲,这堆假设必须被一句一句问出来、被一句一句确认下来。

这些事,**AI 替我们问出来了**。

不是我问的——AI 问的。它按一套公开 40 多年的教学设计方法(ADD 模型),把"学员是谁、终点是什么、要练哪些活、按什么顺序排、每节讲什么、练什么题、答错了怎么提示、先易后难还是螺旋上升"这 8 个维度挨个追了一遍。问完,我拿到的不是一份"AI 印象里的 Java 培训",是一份**这家企业这家老师这家新人具体该怎么上的 Java 培训**。

下面这套方法,如果你正打算让 AI 进你的业务、接你的需求,这一篇就是给你写的。

### 为什么这件事过去没人提

你可能想问:AI 问问题、剥需求,这不是常识吗?谁家 AI 助手不先问几句?

因为过去不需要。

过去 AI 是"印象式输出"——给它一个 prompt,它凭语料库的平均值回一份。**对大多数 C 端场景这就够了**——你让它写封邮件、起个标题、画张图、做个摘要,平均输出就是你要的,你不需要它"懂业务"。

ToB 业务场景反过来。

ToB 业务不是"平均输出能用就行",而是"必须严格符合这家客户的特定学员画像、特定时间预算、特定项目压得住的程度"。AI 一凭印象写,就完蛋。

可 ToB 业务又有自己的特点——**客户的原始需求是碎片化的、口语化的、零结构的**。"我要做 Java 培训"这句话,是一个真实的项目需求,但也是一句 AI 完全没法直接干活的废话。FDE 拿到这种需求,**第一步不是进 IDE、不是画架构图、不是写测试**,是去和老师 + AI 做三方对话,完成"业务剥离"。

这件事过去没人提,是因为过去没有 AI 需要"被教会问什么"。今天有 AI 进场了,**教 AI 问什么**变成了 FDE 的核心动作。

那具体怎么教?AI 用什么"菜谱表"问?下一节我们正式讲这套方法。

## 二、真实场景引子——老师一句话原始需求,AI 三轮问完才动手

我们把"老师一句话需求,AI 怎么问"摆到桌面上。

我最近接的这个 ToB 课程设计项目,对接的是企业培训负责人。一上来,他跟我说了这么一段话——

> "我们要给社招新人做 Java 培训,40 小时,要 Spring 全家桶,但具体怎么排课我自己也说不清,先给我列一下吧。"

你看到这段话,可能也觉得"挺正常"。可这是典型的**碎片化、口语化、零结构的原始需求**——

- 没有学员画像(社招新人是从学校直接出来的,还是已经工作 1-2 年想转技术栈?)
- 没有知识点结构(40 小时里 Java SE 还讲不讲?数据结构还补不补?)
- 没有题目规划(练什么题、几道、什么难度、每题几分?)
- 没有课时分配(每天 1 小时×40 天,还是每周 5 小时×8 周?)
- 没有难度曲线(先易后难还是螺旋上升?Spring 全家桶上来就 Boot+Cloud 一把梭,还是先 Boot 后 Cloud?)
- 没有项目压不压得住的考虑(新人跟师傅带项目,这个"师傅"是不是得有 SpringBoot 实际项目经验?)

老师自己没系统想过这些事。他做了 5 年企业培训,这些事"他脑子里都有",可"脑子里有"和"能写出来"是两回事。

那 FDE 拿到这段需求,第一步做什么?

**不是进 IDE,不是问 AI"帮我写个 Java 培训大纲"**。是拉上老师,叫上 AI,做三方对话,把这段含糊的话一句一句剥清楚。

这一步的本质——**功能不是工程师主观设计,只是把老师原生需求提纯、规范化。**

这一句你也记下来。它是这一篇的第二个核心判断。

FDE 不是设计师——不是"我设计一门 Java 课程",是"我把老师心里那堆没成型的想法剥成可执行的结构"。老师是真正的业务拥有者,他嘴里说出"我要做 Java 培训"的时候,他已经在脑子里过了 100 件事——只是没说出口。FDE + AI 的工作,就是**把那 100 件事替他问出来、写下来、变成下游所有 Agent 都能看懂的标准件**。

听起来简单。但这事做起来有一个核心工具——**ADD 教学设计模型**。这不是凭空发明的工具,是从业者几十年踩坑沉淀下来的方法论骨架。

ADD 是 1990 年代公开的教学设计通用框架(Analysis + Design 两阶段,把"学员/目标/任务/结构/内容/练习/反馈/难度"这 8 个维度系统化拆开)。不是私有方法论,公开 40 多年,任何教学设计师都在用——Rossett 等研究者进一步把它细化成"任务驱动需求分析",强调"先问任务、再问学员、再问终点"。

这套方法就是 AI 追问的"菜谱表"。AI 拿到原始需求后,不是凭印象追问,是**按 ADD 8 维度挨个追问**——

- 学员是谁?
- 终点目标是什么?
- 要练哪些关键任务?
- 按什么逻辑组织结构?
- 每节讲什么内容?
- 配什么练习?
- 答错怎么反馈?
- 难度怎么排?

8 维度挨个问完,4 轮追问 + 1 轮汇总够了。

下面我们把这套对话展开给你看。

## 三、第一轮 AI 对话演示——ADD 8 维度挨个追,4 轮追问 + 1 段汇总把需求问透

**对话为方法论复现,非真实业务对话截屏。**

> 下面这段对话,是我用 ADD 公开方法论 + 当时真实的对话感还原出来的,**不是真实业务对话的截屏**——本项目的真实素材来自 ToB 课程设计场景,但具体措辞是按 ADD 方法论推演的典型追问样例。这点我得跟你说清楚,免得你以为这是 AI 真在那儿自动问出来的。




**老师**:"我们要给社招新人做个 Java 培训,40 小时,要 Spring 全家桶,但具体怎么排课我自己也说不清,先给我列一下吧。"

**AI**:"好的。这门课是企业培训?中学?大学?还是别的?"

**老师**:"企业培训。我们公司内部用的。"

**AI**:"好。这批社招新人是从学校直接出来的,还是有 1-2 年其他语言经验想转 Java?已经会 Java SE 吗?接触过 Spring 吗?"

**老师**:"大部分是计算机相关专业应届,Java SE 在学校学过,但没碰过 Spring 全家桶。少部分是从其他语言转过来的,基础参差。"

**AI**:"明白。每天能学多久?集中 40 小时,是每周排班还是连续 5 天×8 小时?还是周末集中 + 平时碎片?"

**老师**:"每周 5 个工作日,每天 2 小时,总共 4 周。周末不上课,新人要消化。"

**AI**:"好,4 周 40 小时。终点目标是什么?新人上完课,是要能独立写 CRUD 模块?能跟师傅带项目?能看懂 Spring 源码?还是能排查线上问题?"

**老师**:"最重要的是能跟师傅带项目、独立完成业务模块开发。排查线上问题是加分项,源码理解不强求。"

**AI**:"好的,这个终点很明确。那课程结构按什么逻辑排——按 Java 知识逻辑(JDBC → Spring → SpringBoot → 微服务 → 源码)?按任务逻辑(从零做一个完整订单系统)?按问题逻辑(新人最常见的 10 个踩坑集)?"

**老师**:"按任务逻辑。师傅带项目也是按任务带的,新人最好跟着任务走。订单系统就订单系统,贴近我们公司实际业务。"

**AI**:"明白了。按任务逻辑走,那我会把课程拆成'搭建 SpringBoot 工程 → 接入 MyBatis → 写订单 CRUD → 加 Redis 缓存 → 加 MQ 异步 → 加 Spring Security 鉴权 → 加单元测试 → 加 Docker 部署'这 8 个任务模块。每个任务对应一章,每章拆 2-3 节,每节配 1-3 个知识点。这块内容、练习、反馈、难度的具体设计,接下来我汇总后给你看,可以吗?"

**老师**:"可以,你先汇总,我看完再说。"




对话跑完。

你可能也注意到了——**AI 一共用了 4 轮追问 + 1 段汇总确认**。第一轮确认场景(企业培训)、第二轮画像学员(应届 + 少部分转语言 + 已学 Java SE + 未碰 Spring)、第三轮锁定终点(跟师傅带项目 + CRUD 模块开发)、第四轮确认结构(任务逻辑),第五段(汇总确认)把整门课拆成 8 个任务模块提议给老师。每一轮覆盖 ADD 8 维度里的 1-2 个,加一起把 8 维度全过了一遍。

这套追问**不是 AI 自己悟出来的**。AI 没悟性,没语料库平均值之外的世界观。它凭什么追问"按知识逻辑、任务逻辑、问题逻辑"?凭 ADD 模型。ADD 模型告诉它"Design 阶段的第一个维度是 Structure(结构),结构的三种典型组织方式是知识/任务/问题"。AI 按菜谱表问,问得专业、问得系统、问得**比从业 5 年的老师自己系统想过一遍还细**。

这就是专栏的核心金句之一——

**AI 追问的 12 个问题,正是你从业 5 年没系统想过的事——AI 给你当翻译官。**

这一句你记下来。

AI 不是替你思考,AI 是把你脑子里零散的思考**按一套公开菜谱表系统化**。菜谱表不是 AI 写的,是你教 AI 用的。Rossett 等研究者 1990 年代写的,ADD 模型 40 年前定的,公开方法论——AI 拿到这套菜谱,才能问得像样。

**AI 写不出 ADD 模型,ADD 模型是你教 AI 学会问什么。**

这一句你也记下来。它是 FDE 在 AI 时代核心价值的浓缩。

FDE 不是写代码的,FDE 是**把团队几十年沉淀下来的方法论,翻译成 AI 能听懂、能按部就班追问的话**。方法论哪儿来的?从业者一代一代踩坑踩出来的。AI 不知道这些坑,可它能严格按菜谱表跑——你给它菜谱表,它跑得比你还稳。

下面我把这段对话的关键骨架画成雷达图,让你直观看到 8 维度是怎么覆盖的。


## 四、追问轮次上限纪律——4 轮追问 + 1 轮汇总硬约束,不是 AI 自己悟出来的

你可能想问:既然 AI 按菜谱表问,为什么不一口气问到 8 维度全覆盖完?

因为老师会炸。

我亲测过——**超过 4 轮追问,用户体验崩**。老师是业务方,不是产品经理,他对你的耐心是"我有空,我配合一下"。你让他回答 8 轮、每轮 3 个追问,他心里已经骂开了:"这 AI 有完没完?我自己列不就完了?"

**4 轮追问 + 1 轮汇总确认**——这是 ToB 业务场景的硬约束,不是技术最优,是**用户可承受**。

这套约束从哪儿来的?从 Spec 端长期挂载——**追问规则不是 AI 学出来的,是 Spec 端长期挂载的硬规矩**。

这一句是为下一篇工程落地篇埋的钩子——下一篇会展开讲"Spec 端怎么把这些追问规则长期挂在 AI 工作台上",这一篇只先把"必须 4 轮追问 + 1 轮汇总上限"这条纪律立住。

### 4 轮追问 + 1 轮汇总硬约束怎么落地

落到具体做法上,有这么几条硬规矩——

**0. 老师回答得略粗,AI 也能兜底**——如果老师没系统答,比如对"按什么逻辑组织?"只回一句"按你专业建议来",AI 不要卡住,而是按 ADD 默认选项(任务逻辑)补全追问,把它做成可用的业务模型,**汇总时把"AI 自动补全"标清楚**让老师 review。老师没空不是 AI 不动的理由。

**1. 每轮覆盖 1-2 个 ADD 维度**——不要一次追 5 个维度。4 轮追问加一起覆盖 8 维度,平均每轮 2 个。

**2. 每轮最多 3 个追问**——老师一回消息,AI 不要甩 10 个问题过去。3 个之内,老师答得了;超过 3 个,他会挑着答或者跳过。

**3. 第 4 轮追问结束后,第 5 段是汇总确认**——"老师,根据你这 4 轮追问的回答,我梳理成下面这份课程骨架,你确认下没问题我就开始写完整大纲"——这是**收口动作**。AI 跑完追问,自动出汇总,老师看一眼,说 OK 就开始。AI 不允许"继续追问下去,直到天荒地老"。

**4. 老师跳过某个维度的回答,不无限重试**——他答了 2 个、某个说"先这样吧",AI 不要追问"那 X 维度您具体什么想法",直接汇总时把 X 维度标"待老师后续补充",推进下一步。

这四条规矩合起来,就是 ADD 追问的"约束面"。菜谱表是 ADD 8 维度(能问什么),约束面是 4 轮追问 + 1 轮汇总硬约束(问到什么时候停)。**两者合起来,才是 AI 时代 FDE 真正能用的追问骨架**。

这一节写完,我得回到开头那张图,把对话时间线画给你看。

你可能又会问:那这条 4 轮追问 + 1 轮汇总硬约束的纪律,我让 AI 自己学不行吗?每次新会话开始前我提示它一下"问到 4 轮就停、第 5 段汇总确认"。

行,但**那是人临时教的,不是 AI 自己悟出来的**。临时教一次两次可以,教 100 次呢?新会话一次又一次忘了呢?这条规矩不是"知识",是"行为准则",AI 不靠大量数据就学不会——而且就算它学会了,你也得每次提醒它想起来。**Spec 端长期挂载的意义不是"让 AI 学",是"让 AI 不用学也守规矩"**——规矩直接焊死在 AI 工作台,AI 跑就完事。


### 为什么 4 轮追问 + 1 轮汇总必须是硬约束而不是"AI 自己学到的"

你可能想问:为什么不让 AI 自己学"问到 4 轮就停、第 5 段汇总"?这是个好问题。

答案藏在 AI 的"工作记忆"机制里。

AI 在一次会话里,有上下文窗口限制——超过一定长度它会"忘前文"、会"漏答"、会"前后矛盾"。会话越长,AI 的"失忆成本"越高。**4 轮追问 + 1 轮汇总恰好是 AI 工作记忆最稳、追问精度最高的区间**。再长,它开始"凑合回答";再短,它还没问全 8 维度。

4 轮追问 + 1 轮汇总不是随便定的——是 ADD 模型 8 维度 + AI 上下文窗口 + 用户耐心上限**三件事的最优交汇点**。

这件事 FDE 必须焊死在 Spec 端,**不能靠 AI 自己悟**。下一篇我会展开讲 Spec 端怎么挂——但 33 上篇只先把这条纪律立住:**AI 追问的 4 轮 + 1 轮汇总硬约束,是 Spec 端长期挂载的死规矩,不是 AI 自己学到的**。

那追问完之后,AI 拿什么交付?一份含糊的话?一份结构散乱的大纲?

都不是。AI 拿的是一份**标准化、机器可读、可被下游所有 Agent 复用的业务模型 JSON**。下面我们把这块讲透。

## 五、JSON 全景——从"含糊的话"到"标准菜谱"长什么样

我们把"AI 追问完之后交付什么"摆到桌面上。

AI 跑完 4 轮追问 + 1 轮汇总确认,得到的不是一份 Word 大纲,是一份 **JSON**——标准化、机器可读、可被下游所有 Agent(题目生成 Agent、材料生成 Agent、排课 Agent、考评 Agent)直接复用的业务模型。

这份 JSON 长什么样?

我以"Java 社招新人 40 小时速成"这门课为例,展示完整的 9 字段骨架——

```json
{
  "courseName": "Java 社招新人 40 小时速成",
  "description": "面向社招新人的 Spring 全家桶入门课,以订单系统为业务主线,4 周 40 小时,跟师傅带项目",
  "totalHours": 40,
  "scenario": "enterprise",
  "targetAudience": {
    "startingPoint": "已掌握 Java SE,有 1-2 年 CRUD 经验但未接触过 Spring 全家桶",
    "endPoint": "能独立完成 SpringBoot 业务模块开发、跟师傅带项目、排查常见线上问题",
    "characteristics": "在职新人、每天 1-2 小时碎片学习 + 周末集中",
    "focus": "Spring 全家桶 + 排查能力",
    "semesterSpan": "4 周"
  },
  "bloomTaxonomy": {
    "remember": [
      "说出 Spring IoC 容器初始化流程",
      "列举 Spring 5 种作用域",
      "复述 Spring Boot 自动装配原理"
    ],
    "understand": [
      "解释 AOP 与 IoC 的核心区别",
      "总结 Spring Boot 与 Spring Cloud 的协作关系"
    ],
    "apply": [
      "搭建 SpringBoot 工程",
      "集成 MyBatis 完成 CRUD",
      "接入 Redis 缓存",
      "接入 Spring Security 完成鉴权",
      "用 Docker 部署 SpringBoot 应用"
    ],
    "analyze": [
      "排查 Bean 循环依赖问题",
      "分析接口性能瓶颈并定位根因"
    ],
    "evaluate": [
      "评审代码是否符合团队规范",
      "判断不同缓存策略的适用场景"
    ],
    "create": [
      "从零搭建一个 SpringBoot 订单系统骨架"
    ]
  },
  "structure": [
    {
      "type": "stage",
      "name": "筑基阶段(Week 1)",
      "children": [
        {
          "type": "chapter",
          "name": "Spring IoC 容器",
          "children": [
            {
              "type": "section",
              "name": "Bean 的生命周期",
              "contentType": "text",
              "knowledgePoints": [
                {
                  "id": "kp-001",
                  "name": "Bean 实例化流程",
                  "contentType": "text",
                  "learningObjectives": "用 apply 动词描述 Bean 实例化的 5 个阶段",
                  "prerequisites": [],
                  "estimatedHours": 1.5,
                  "difficulty": "intermediate"
                }
              ]
            }
          ]
        },
        {
          "type": "chapter",
          "name": "SpringBoot 工程搭建",
          "children": [
            {
              "type": "section",
              "name": "第一个 SpringBoot 应用",
              "contentType": "text",
              "knowledgePoints": [
                {
                  "id": "kp-002",
                  "name": "SpringBoot 自动装配",
                  "contentType": "text",
                  "learningObjectives": "用 apply 动词演示 SpringBoot 自动装配过程",
                  "prerequisites": ["kp-001"],
                  "estimatedHours": 2,
                  "difficulty": "intermediate"
                }
              ]
            }
          ]
        }
      ]
    },
    {
      "type": "stage",
      "name": "实战阶段(Week 2-3)",
      "children": [
        {
          "type": "chapter",
          "name": "订单系统业务模块",
          "children": [
            {
              "type": "section",
              "name": "订单 CRUD 模块开发",
              "contentType": "lab",
              "knowledgePoints": [
                {
                  "id": "kp-003",
                  "name": "SpringBoot + MyBatis 订单 CRUD",
                  "contentType": "lab",
                  "learningObjectives": "用 apply 动词完成订单 CRUD 业务模块",
                  "prerequisites": ["kp-002"],
                  "estimatedHours": 6,
                  "difficulty": "intermediate"
                }
              ]
            }
          ]
        },
        {
          "type": "chapter",
          "name": "性能与安全加固",
          "children": [
            {
              "type": "section",
              "name": "Redis 缓存接入",
              "contentType": "lab",
              "knowledgePoints": [
                {
                  "id": "kp-004",
                  "name": "Redis 缓存订单查询",
                  "contentType": "lab",
                  "learningObjectives": "用 apply 动词接入 Redis 缓存订单查询接口",
                  "prerequisites": ["kp-003"],
                  "estimatedHours": 3,
                  "difficulty": "intermediate"
                }
              ]
            },
            {
              "type": "section",
              "name": "Spring Security 鉴权",
              "contentType": "lab",
              "knowledgePoints": [
                {
                  "id": "kp-005",
                  "name": "Spring Security 接口鉴权",
                  "contentType": "text",
                  "learningObjectives": "用 apply 动词接入 Spring Security 鉴权",
                  "prerequisites": ["kp-003"],
                  "estimatedHours": 4,
                  "difficulty": "intermediate"
                }
              ]
            }
          ]
        }
      ]
    },
    {
      "type": "stage",
      "name": "巩固阶段(Week 4)",
      "children": [
        {
          "type": "chapter",
          "name": "排查能力与部署上线",
          "children": [
            {
              "type": "section",
              "name": "线上问题排查实战",
              "contentType": "text",
              "knowledgePoints": [
                {
                  "id": "kp-006",
                  "name": "Bean 循环依赖排查",
                  "contentType": "text",
                  "learningObjectives": "用 analyze 动词独立排查 Bean 循环依赖",
                  "prerequisites": ["kp-001"],
                  "estimatedHours": 3,
                  "difficulty": "intermediate"
                }
              ]
            },
            {
              "type": "section",
              "name": "Docker 部署上线",
              "contentType": "lab",
              "knowledgePoints": [
                {
                  "id": "kp-007",
                  "name": "SpringBoot Docker 镜像构建与部署",
                  "contentType": "lab",
                  "learningObjectives": "用 apply 动词把 SpringBoot 应用打包成 Docker 镜像并部署",
                  "prerequisites": ["kp-002", "kp-003"],
                  "estimatedHours": 2.5,
                  "difficulty": "intermediate"
                }
              ]
            },
            {
              "type": "section",
              "name": "综合考核",
              "contentType": "exam",
              "knowledgePoints": [
                {
                  "id": "kp-008",
                  "name": "期末综合考核",
                  "contentType": "exam",
                  "learningObjectives": "用 create / evaluate 动词独立完成订单系统综合考核",
                  "prerequisites": ["kp-002", "kp-003", "kp-004", "kp-005"],
                  "estimatedHours": 4,
                  "difficulty": "advanced"
                }
              ]
            }
          ]
        }
      ]
    }
  ],
  "knowledgePoints": [
    {
      "id": "kp-001",
      "name": "Bean 实例化流程",
      "contentType": "text",
      "learningObjectives": "用 apply 动词描述 Bean 实例化的 5 个阶段",
      "prerequisites": [],
      "estimatedHours": 1.5,
      "difficulty": "intermediate"
    },
    {
      "id": "kp-002",
      "name": "SpringBoot 自动装配",
      "contentType": "text",
      "learningObjectives": "用 apply 动词演示 SpringBoot 自动装配过程",
      "prerequisites": ["kp-001"],
      "estimatedHours": 2,
      "difficulty": "intermediate"
    },
    {
      "id": "kp-003",
      "name": "SpringBoot + MyBatis 订单 CRUD",
      "contentType": "lab",
      "learningObjectives": "用 apply 动词完成订单 CRUD 业务模块",
      "prerequisites": ["kp-002"],
      "estimatedHours": 6,
      "difficulty": "intermediate"
    },
    {
      "id": "kp-004",
      "name": "Redis 缓存订单查询",
      "contentType": "lab",
      "learningObjectives": "用 apply 动词接入 Redis 缓存订单查询接口",
      "prerequisites": ["kp-003"],
      "estimatedHours": 3,
      "difficulty": "intermediate"
    },
    {
      "id": "kp-005",
      "name": "Spring Security 接口鉴权",
      "contentType": "text",
      "learningObjectives": "用 apply 动词接入 Spring Security 鉴权",
      "prerequisites": ["kp-003"],
      "estimatedHours": 4,
      "difficulty": "intermediate"
    },
    {
      "id": "kp-006",
      "name": "Bean 循环依赖排查",
      "contentType": "text",
      "learningObjectives": "用 analyze 动词独立排查 Bean 循环依赖",
      "prerequisites": ["kp-001"],
      "estimatedHours": 3,
      "difficulty": "intermediate"
    },
    {
      "id": "kp-007",
      "name": "SpringBoot Docker 镜像构建与部署",
      "contentType": "lab",
      "learningObjectives": "用 apply 动词把 SpringBoot 应用打包成 Docker 镜像并部署",
      "prerequisites": ["kp-002", "kp-003"],
      "estimatedHours": 2.5,
      "difficulty": "intermediate"
    },
    {
      "id": "kp-008",
      "name": "期末综合考核",
      "contentType": "exam",
      "learningObjectives": "用 create / evaluate 动词独立完成订单系统综合考核",
      "prerequisites": ["kp-002", "kp-003", "kp-004", "kp-005"],
      "estimatedHours": 4,
      "difficulty": "advanced"
    }
  ],
  "examConfig": {
    "kp-008": {
      "questionTypes": ["coding", "scenario"],
      "questionCount": 5,
      "difficulty": "advanced",
      "score": 100
    }
  }
}
```

你可能看完这堆 JSON 觉得"太长了"。但这就是 AI 时代 FDE 真正交付的东西——**不是一份 Word 大纲,不是一份 PPT 课件,是一份 9 字段标准化业务模型**。

下面我把这 9 字段拆给你听。

### 9 字段怎么来的

这套字段不是凭感觉造的——它来自 `schema.org/Course` 这个全球通用的开放课程元数据标准(Google、Microsoft、Yandex 联合维护,被 10K-100K 个生产级站点使用),同时对齐了布鲁姆 6 层认知目标分类法(1956 年 Benjamin Bloom 提出,2001 年 Anderson & Krathwohl 修订为 remember / understand / apply / analyze / evaluate / create),用 JSON Schema 校验规则做了必填 + enum + 数值范围 + 引用完整性四道闸。

9 字段拆分——

- **courseName / description / totalHours**——课程元信息,标准化命名的入口。
- **scenario**——场景枚举(enterprise / k12 / university / other),决定下游 Agent 切哪套模板。
- **targetAudience**——学员画像,展开成 startingPoint / endPoint / characteristics / focus / semesterSpan 五个子字段。
- **bloomTaxonomy**——6 层认知目标分布,每层挂该层的目标动词 remember / understand / apply / analyze / evaluate / create。这是 33 + 34 双篇共享的"教学目标骨架",也是 FDE 一线工程师做课程评审的统一语言。
- **structure**——嵌套 4 层结构(stage → chapter → section → knowledgePoint),按 ADD 模型 Design 阶段的"Structure 维度"展开。
- **knowledgePoints**——扁平数组,每个知识点带 id / name / contentType(text / exam / lab 三种)/ learningObjectives / prerequisites(引用其他 kp 的 id)/ estimatedHours / difficulty(beginner / intermediate / advanced)。
- **examConfig**——仅对 contentType=exam 的知识点必填,包含 questionTypes / questionCount / difficulty / score 四个子字段。非 exam 知识点禁止填。

这套 9 字段为什么是"标准件"?

因为下游所有 Agent 拿到这份 JSON,**不需要再问老师一句**——题目生成 Agent 直接读 knowledgePoints + examConfig 出题、材料生成 Agent 直接读 structure 配 PPT、排课 Agent 直接读 estimatedHours 排日程、考评 Agent 直接读 bloomTaxonomy 出试卷。**一个 JSON,四个 Agent 共用**。

老师一句话原始需求 → AI 4 轮追问 + 1 轮汇总确认 → 标准 JSON 业务模型 → 四个 Agent 直接干活——这条链就是 ToB 课程设计业务从"含糊念头"到"可交付产品"的全部转换过程。

下面这张图把 JSON 的层级树画出来,让你直观看到它长什么样。


### 这份 JSON 给谁看的?老师、AI、下游 Agent 三方共用

你可能想问:这份 JSON 是不是给老师看的?

不是。老师看到这堆 JSON 会头大——他要的是一份能直接发培训部评审的标准化课程文档,不是这一堆 JSON 技术件。

**这份 JSON 不是给老师看的,是给机器看的**。下游 Agent(题目生成 / 材料生成 / 排课 / 考评)拿到这份 JSON 直接干活,不问老师一句。老师看完大纲觉得"OK",AI 自动把这份 JSON 推给下游,Agent 流水线跑起来——题目生成 Agent 出 5 道 coding 题、材料生成 Agent 配 8 章 PPT、排课 Agent 排 4 周×5 天×2 小时、考评 Agent 出综合考核卷。

**老师 + AI + 下游 Agent + 这份 JSON = 完整的 ToB 业务流水线。**

FDE 在这条流水线里的位置——**把老师脑子里零散的"100 件事"剥成这份 JSON,把 JSON 推给下游,下游 Agent 接力跑完**。FDE 不是写代码的,FDE 是**业务翻译官**——把含糊的需求翻译成下游所有 Agent 都懂的标准件。

这个角色在 AI 时代被重新定义了一遍。下一节我们正式讲。

## 六、FDE 价值定位——AI 时代的工程师不是写代码,是让 AI 知道问什么

我们把"FDE 在 AI 时代的核心价值"摆到桌面上。

最近这一年,我自己反复在思考一件事——**AI 越来越能干,FDE 越来越该干什么**。

传统 FDE 是"前线部署工程师"——客户要个新功能,FDE 跑去客户现场,理解业务、画架构、写代码、部署上线、交接维护。整套动作的核心是**写代码**——你写得好,交付快,客户满意,你就是好 FDE。

AI 时代这事的重心偏了。

AI 写代码比人快、比人稳、比人不知疲倦——你让 AI 写一个 SpringBoot 订单 CRUD,AI 半小时出活;你让人写,半天起步。**写代码这个动作,正在从 FDE 的核心价值变成"基础设施"**。FDE 不再以"写代码"为荣,而是以"让 AI 知道写什么"为荣。

听起来有点反直觉。可你想想——你最近一次跟 AI 协作,卡住你最久的环节是写代码吗?

不是。

你卡住最久的环节,是**AI 写的代码不是你想要的**。你让它写 SpringBoot CRUD,它给你整出一堆"语料库平均值的实现"——日志规范不对、Header 命名不对、错误码体系不对、分页插件没换、Redis 序列化没用团队的、监控埋点没埋……你跟它说了 8 遍,它下次还是错。

问题出在哪?不是你不会写代码——是**你没把"我想要的"翻译成 AI 能听懂的标准件**。

AI 时代的 FDE,核心价值不是写代码,是——

**让 AI 知道问什么。**

这一句你记下来。它是这一篇的最后一根金句。

"问什么"是什么意思?不是"你下次帮我写得对一点"——那是模糊期待,AI 听不懂。"问什么"是**把团队的规范、业务的边界、用户的偏好,沉淀成一份 AI 能按部就班追问的菜谱表**。

ADD 模型是菜谱表的一部分。布鲁姆动词表是菜谱表的一部分。4 轮追问 + 1 轮汇总硬约束是菜谱表的一部分。9 字段 JSON 是菜谱表的产出物。Spec 端长期挂载追问规则、JSON Schema 校验、追问覆盖度审计——这些都是菜谱表的工程化形态。

**FDE 是给 AI 写菜谱表的人,不是给客户写代码的人。**

这一句你记下来。它是 FDE 在 AI 时代的重新定位。

下面这张三方对话协作图,把 FDE 在 ToB 业务里的角色画出来。


### FDE 的新三角关系:老师 + FDE + AI

你可能想问:FDE + AI 协作,老师的角色是什么?

老师的角色没变——他仍然是业务拥有者,他仍然说"我要做 Java 培训"。可他对 AI 的关系变了——**他不直接跟 AI 谈,他跟 FDE 谈,FDE 把他的话翻译成 AI 听得懂的标准追问脚本**。这不是"老师被绕开",而是"老师多了一个翻译官帮他说清需求"。

这是 AI 时代的新型三角关系——

- **老师**——业务专家,懂学员、懂场景、懂业务目标,但不系统想"这课程结构该怎么排"。
- **FDE**——业务翻译官,把老师含糊的话剥成 AI 听得懂的菜谱脚本 + 标准 JSON 产出物。
- **AI**——执行引擎,严格按 FDE 给的菜谱跑,跑完产出可被下游 Agent 复用的 JSON。

这三方里,谁是核心?

不是 AI——AI 谁都能换模型、换工具,换一家还是照样干活。

不是老师——老师是业务拥有者,他来定业务目标,可他不会系统写课程结构。

**是 FDE。**

FDE 是**把老师原生需求翻译成 AI 能跑的标准件的桥梁**。FDE 不懂业务细节?他没法翻译。FDE 不懂 AI 工作机制?他没法落地。**两边都懂、两边都不需要懂到顶——这是 FDE 的独特位置**。

你说未来 FDE 会被 AI 替代吗?

我觉得——**不会**。AI 能写代码,能跑追问脚本,能出标准 JSON——三件事 AI 都能干。但 AI 干完活之后,"这课程到底要解决什么""这条需求要不要追问、追问到什么程度""这块学员起点写错了、难度定低了"这些判断,AI 干不了,得靠 FDE。AI 不是替代 FDE,AI 是放大 FDE——FDE 越会用 AI,交付质量越高,业务覆盖越广。

AI 是工具,FDE 是那个知道把工具使在哪的人。工具越来越强,**用工具的人越来越值钱**。

### 专栏这一篇立住的判断

立柱的话我再说一遍,这一篇的底色已经讲完了——

- **AI 不是自己懂业务,是**人 + AI 一起**把模糊念头剥到可用边界**——也是 **AI 把"老师自己都没想到的关键问题"问出来了**。两句话是同一件事的两面:前一句说人和 AI 怎么一起做,后一句说 AI 在追问什么。FDE 的价值,不是替代老师思考,是把老师没系统想过的"100 件事"按菜谱表问出来,剥到下游 Agent 能跑的标准件。
- **功能不是工程师主观设计,只是把老师原生需求提纯、规范化**——FDE 不是设计师,是翻译官。
- **AI 追问的 12 个问题,正是你从业 5 年没系统想过的事——AI 给你当翻译官**——AI 把含糊的需求系统化,跑得比老师自己系统想一遍还细。
- **AI 写不出 ADD 模型,ADD 模型是你教 AI 学会问什么**——菜谱表是人写的,AI 严格按菜谱表跑。
- **未来真正会用 AI 做业务的人,不是会写 Prompt 的人,是会教 AI 问什么的人**——FDE 的新定位。

这五句你记下来。它们是 33 上篇立住的判断,也是后续业务实战连载的起点。

五句话不是五个独立判断,是同一件事的不同侧面——**AI 不是自己懂业务,而是 FDE 给它搭了一个"懂业务"的菜谱脚本;AI 不是会问,而是 ADD 模型这套公开方法论在替它问;FDE 不是写代码,而是把方法论翻译成 AI 能跑的标准件**。三条线拧成一根绳,就是 AI 时代 FDE 的新三角。

## 七、写在最后——业务模型有了,真正落成可跑的产品还有几条死规矩

回到开头那个反直觉的判断——**AI 不是越来越懂业务,是越来越需要人教它问什么**。

你最近接的 ToB 业务,是不是也卡在"AI 写得不对"上?不是 AI 太笨,而是没人给它菜谱表。

这篇给你看了一件事——**怎么把"老师一句话原始需求"剥成"AI 能跑的标准 JSON"**。这条路走通了:ADD 8 维度追问 + 4 轮追问 + 1 轮汇总硬约束 + 9 字段 JSON 产出物。AI 跑得稳、跑得快、跑得**比老师自己系统想一遍还细**。

可这只是业务心智——把"业务边界"剥清。**业务模型有了,真正落成可跑的产品却还有几条死规矩**——

- **DDD 怎么切三限界上下文**?课程(主域)、题目(支撑域)、材料(支撑域)三个限界上下文怎么分?上下文之间怎么映射?customer-supplier 关系怎么走?
- **SDD 怎么把对话脚本 + 追问规则 + JSON 规范长期挂载**?4 轮追问 + 1 轮汇总硬约束怎么挂?ADD 8 维度追问骨架怎么挂?JSON Schema 校验规则怎么挂?Spec 端长期挂载是不是比"每次新会话重讲"更省成本?
- **TDD 怎么把每一个 JSON 字段都验证**?追问覆盖度审计怎么写?JSON 合法性审计怎么写?修改一致性审计怎么写?CI/CD 流水线怎么卡死?

——**下一篇到工程落地的实战里把这些一道道拆给你看**。

业务心智是 33 上篇,工程落地是 34 下篇。下一篇我会接着讲"业务模型有了,怎么把它落成可跑的 Agent 产品"——DDD 切限界上下文、SDD 长期挂载规则、TDD 自动化审计、工程化取舍四个主决策。

行,这一篇就到这儿——

### 这一篇留给你的

读完这一篇,你能拿走三件事——

- **一套 ToB 业务剥离的菜谱表**——ADD 8 维度追问骨架。你下次接 ToB 业务,把这段直接复制粘贴进项目 Spec,AI 按这个跑就稳。
- **一条 4 轮追问 + 1 轮汇总的硬约束**——超过 4 轮追问,用户体验崩。这条是死规矩,不是 AI 自己悟出来的,焊在你的 Spec 端。
- **一份 9 字段标准化业务模型 JSON**——courseName / description / totalHours / scenario / targetAudience / bloomTaxonomy / structure / knowledgePoints / examConfig。下游所有 Agent 拿到这份 JSON 直接干活,不问老师一句。

这三件事,是你能直接搬到下一个 ToB 项目里的工具。不是方法论——是**工具**。方法论再多,落到工具上才能用。

业务模型有了,工具齐了。下一篇我们去看工具怎么落成工程骨架。




### 关于 ArchAIHarness

这篇文章是「看懂 AI 与智能体」专栏的一部分,由 [**ArchAIHarness**](https://github.com/ArchAIHarness) 持续输出。

ArchAIHarness 是一套面向 AI 时代软件工程的人机协同架构哲学与公开工程资产,主张:

> **架构师定义秩序,AI 在秩序中生长。人立法,AI 执行,体系审计。**

如果你也希望 AI 在明确的架构边界内协作,而不是在混沌中碰运气,欢迎到 GitHub 上看看我们在做什么:

- **组织主页**:[github.com/ArchAIHarness](https://github.com/ArchAIHarness) — 了解完整理念与资产全景
- **本专栏**:[`zhuanlan-ai-and-agents`](https://github.com/ArchAIHarness/zhuanlan-ai-and-agents) — 所有文章的源码与发布记录
- **实践指南**:[`docs`](https://github.com/ArchAIHarness/docs) — 架构哲学、工程方法和落地指南
- **开源工具**:[`agent-workflows`](https://github.com/ArchAIHarness/agent-workflows) — 可复用的 AI 协作 Agents、Skills 与 Tools
- **工程样例**:[`framework`](https://github.com/ArchAIHarness/framework) — DDD + AI 协作的工程底座,展示如何在开发中融合 AI

> Engineered by Architects · Empowered by AI · Audited by Discipline