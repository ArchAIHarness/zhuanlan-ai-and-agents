# 32 篇配图清单(插画专员工作指令)

> **本文档仅给插画专员(content-illustrator)用,撰稿员(content-writer)不要读**。
> **配图内容由插画专员自己读完正文后决定**,本文档只提供参考框架与风格规范。
> 本文件**不嵌入正文**,由插画专员按本清单生成(风格:手绘教育插图,暖色调奶油纸背景 + 黑色草图线 + 柔和粉彩色块 + 右手写体中文标签 + 右下角 ArchAIHarness 水印)。
> 正文入口:`32_framework整合实战——DDD-TDD-SDD三件套在framework仓的真实落地.md`

## 标题最终建议(开写前可校准)

候选(对应 `AGENTS.md` §四 32 篇 spec):
- **首选**《framework 整合实战——DDD/TDD/SDD 三件套在 framework 仓的真实落地》(直接点题,4 篇收束)
- 备选一《我从 framework 仓库里捞出来的三件套落地》(口语钩子)
- 备选二《DDD/TDD/SDD 不是抽象的——看 framework 怎么把它谱成乐谱》(强调"乐谱"金句)

**比喻体系(延续 29-31 餐饮后厨)**:**framework = 一座已经搭好的厨房**
- 六模块分层 = 厨房分区(切配/炒菜/装盘/甜品/凉菜)
- domain + common 零 Spring = 主菜区+调料区焊死(不让人随便改灶具)
- JaCoCo 90% + P0 红线 = 试菜员常驻门口
- 双文档体系 = 厨房墙上挂两本手册(给新人看的 + 给供应商看的)
- SPI 默认实现 = 后厨的"通用灶具接口"——默认配的是标准款,但你换高级款也能用
- 留白区在 SPI 设计里 = 灶具接口职责焊死(必须能炒菜),但具体怎么炒(用什么火、用什么锅)AI 自由决定

**严格禁用**:乐谱/作曲家/音符(27 篇);护照/国境/货币/看门人(2026-07-01 已废);赛道/焊边界(28 篇);试菜员主线(30 篇独有比喻,32 只在"framework 落 TDD"小节短暂提及,不重画)。

---

## 图 1:一座已经搭好的厨房(位于 §一,反直觉开场)

- **核心概念**:DDD/TDD/SDD 听上去都是抽象方法论,真要落地需要一座"已经搭好的厨房";**framework 就是这座厨房**,新服务直接搬走,不用重新搭工种分区、重新培养试菜员、重新写 Spec 手册。
- **视觉建议**:一座按"工种分区 + 试菜员 + 墙上挂手册 + 留白区"标准搭好的厨房全景图,主厨指着厨房对新人(AI 小机器人 + 一位 FDE 工程师)说"搬走,直接开干"——这就是 framework 仓库;背景标注"ArchAIHarness/framework 公开 MIT 协议"。
- **prompt 草稿**:暖色调奶油纸背景,黑色草图线条,柔和粉彩色块(主色橙+绿+蓝+紫+淡灰)。画面中央一座完整搭好的厨房全景图(从左到右):① 切配区 + 炒菜区 + 装盘区 + 甜品区(DDD 工种分区);② 门口站着试菜员(TDD 强制审计);③ 墙上挂着手册(SDD Spec 端);④ 灶具接口位置标"留白区 SPI";⑤ 工程师(右侧 FDE 工程师)和 AI 小机器人(主厨手把手)进入厨房。主厨手举钥匙,头顶手写体标签"framework = 一座已经搭好的厨房"。背景水印小字"ArchAIHarness/framework · 公开 MIT 协议 · 新服务搬走直接开干"。底部小字金句"DDD/TDD/SDD 听上去抽象,framework 把它落地为可复用工程骨架"。右下角 ArchAIHarness 水印。

## 图 2:六模块分层铁律图(位于 §二,framework 怎么落 DDD)

- **核心概念**:六模块分层铁律(bootstrap / interfaces / application / **domain** ⭐零 Spring / infrastructure / **common** ⭐零框架);**业务边界 = 模块边界**;`common` 与 `domain` 零 Spring 依赖。
- **视觉建议**:一张六层楼房透视图(自下而上),最底 domain + common 楼层红色钢门焊死"零 Spring / 零框架";上面四层(bootstrap/interfaces/application/infrastructure)敞开通行,楼层间有单向箭头表示依赖方向(下层不能反向依赖上层)。
- **prompt 草稿**:暖色调奶油纸背景,黑色草图线条,柔和粉彩色块(主色橙+绿+蓝+紫+红+灰)。画面中央一座六层楼房透视图(自下而上):① Domain(最底,⭐ 标注) ② Common(最底,⭐ 标注) ③ Application ④ Infrastructure ⑤ Interfaces ⑥ Bootstrap(最上)。Domain + Common 楼层用红色钢门锁死(门上两块警告牌:"@Service? ×" "@Component? ×" 标注"零 Spring / 零框架");Application / Infrastructure / Interfaces / Bootstrap 四层敞开,楼层间有单向箭头(下方楼层不能依赖上方)。Domain + Common 内可见纯 Java 文件的 User / Tenant 聚合根;Application/Interfaces 内可见 @Service / @RestController。底部小字"framework 六模块分层铁律 = 业务边界 = 模块边界"。右下角 ArchAIHarness 水印。

## 图 3:JaCoCo 90% 强制覆盖率闸门(位于 §三,framework 怎么落 TDD)

- **核心概念**:JaCoCo 强制覆盖率(全集 BRANCH 30% / LINE 70%;**common + domain 各层 ≥ 90%** 行/分支双门槛,P0 准入);P0/P1/P2 分级;Given-When-Then 强制;Mock 边界规范。
- **视觉建议**:一座大门(覆盖率闸门),门上方大牌子"JaCoCo ≥ 90%(P0 准入)";门左侧三个红绿灯并排(P0 红灯 / P1 黄灯 / P2 绿灯),P0 红灯亮起(闸门关闭);门旁边站一位试菜员(TDD 审计);AI 小机器人抱着代码文件准备通过闸门;底部小字"Mock 边界:禁止 Mock 实体"。
- **prompt 草稿**:暖色调奶油纸背景,黑色草图线条,柔和粉彩色块(主色橙+绿+蓝+红+黄)。画面中央一座大门(覆盖率闸门),门上方挂着一块大牌子"JaCoCo ≥ 90%(P0 准入)";门左侧三个红绿灯并排(P0 红灯亮起 / P1 黄灯 / P2 绿灯),旁边标"common + domain 各层 ≥ 90% 行/分支双门槛";门右侧站着试菜员(TDD 审计),手举"Given-When-Then 强制"标牌;AI 小机器人(右侧)抱着代码文件准备通过闸门,表情紧张。底部小字"Mock 边界:禁止 Mock 实体 / 真造真测 / P0 不通过直接退回"。右下角 ArchAIHarness 水印。

## 图 4:双文档体系对照图(位于 §四,framework 怎么落 SDD)

- **核心概念**:双文档体系(`readme.md` 人友好讲架构 + 示例 / `AGENTS.md` AI 友好讲 P0/P1/P2 清单 + 禁止事项);**同秩序两种表达**;`readme.md` / `AGENTS.md` / `DOCS.md` 三文件分别面向不同读者。
- **视觉建议**:左右对照——左 `readme.md`(带流程图 Mermaid + 示例代码块),旁边站着戴眼镜的人类开发者(手写体标签"给人看");右 `AGENTS.md`(带 P0/P1/P2 清单 + 禁止事项表格),旁边站着 AI 工程师(手写体标签"给 AI 看");中间一条虚线连接,标注"同一套秩序";两份文件上方再悬一份"DDD 限界上下文"共享 Spec 手册。
- **prompt 草稿**:暖色调奶油纸背景,黑色草图线条,柔和粉彩色块(主色橙+绿+蓝)。画面中间一条横向虚线连接两份文件;左侧一份 `readme.md`(画面里有 Mermaid 流程图 + 示例代码块,标注"给人看"),旁边站一位戴眼镜的人类开发者;右侧一份 `AGENTS.md`(画面里有"P0 / P1 / P2"清单 + 禁止事项表格,标注"给 AI 看"),旁边站一位 AI 小工程师;两份文件上方再悬一份"DDD 限界上下文"共享 Spec 手册(表示 Spec 端"长期挂载");底部小字金句"同一套秩序两种表达 / Spec 端 + readme + AGENTS.md 三位一体"。右下角 ArchAIHarness 水印。

## 图 5:边界焊死 + 选择放开对照图(位于 §五,核心创新)

- **核心概念**:**硬秩序焊边界**(三个限界上下文:auth-center / user-center / tenant-center)vs **软秩序放选择**(6 个 SPI + `@ConditionalOnMissingBean` 让 AI 按需替换默认实现);两层合起来才是 framework 的工程价值。
- **视觉建议**:左栏三块焊死的钢墙(三个限界上下文:auth-center / user-center / tenant-center)——硬秩序;右栏一扇敞开的旋转门(6 个 SPI + `@ConditionalOnMissingBean`)——软秩序;中间铁桥连接,AI 列车在铁桥上平稳通过。
- **prompt 草稿**:暖色调奶油纸背景,黑色草图线条,柔和粉彩色块(主色橙+绿+蓝+红)。画面左栏三块焊死的钢铁墙(从左到右标注):① "auth-center" ② "user-center" ③ "tenant-center"——每块墙上有块小标牌("P0 红线 / 分层纪律 / Header 命名"),墙外立红牌"不许越";右栏一扇敞开的旋转门,门内六个可替换的方块("SPI 1~6 / @ConditionalOnMissingBean"),门内挂绿牌"随便换";中间一条铁桥连接墙与门,铁桥上 AI 小机器人驾驶列车平稳通过。底部左边小字"framework 告诉你不能做什么",右边小字"gateway 告诉你可以怎么做",最底部小字金句"边界焊死 + 选择放开 = framework 真正的工程价值"。右下角 ArchAIHarness 水印。

---

## 撰稿约束(本篇硬约束,撰稿员必守)

- **结构**:7 节(开场 / framework 落 DDD / framework 落 TDD / framework 落 SDD / 边界焊死 + 选择放开 / framework 落团队班规 / 写在最后,4 篇金句收束)
- **篇幅**:**不靠字数,讲清楚就行**;目标 8000-12000 字
- **5 句金句必背**:
  1. "DDD/TDD/SDD 听上去都是抽象方法论,真要落地需要一座已经搭好的厨房——framework 就是这座厨房。"
  2. "framework 的六模块分层铁律 + 零 Spring 依赖,是 AI 时代工程师给 AI 焊死的最硬的边界。"
  3. "硬秩序焊边界(三个限界上下文)+ 软秩序放选择(6 个 SPI + @ConditionalOnMissingBean)——这两层加在一起,才是 framework 真正的工程价值。"
  4. "framework 的留白区在 SPI 设计里——6 个接口职责焊死,但默认实现可换,AI 在边界内自主决定。"
  5. "抽象方法论一旦落地为可复用工程骨架,AI 时代的工程师才算真正从重复告知规范里解放出来,把精力放在业务本身。"
- **5 张配图占位**:`@@@IMG_1@@@` 到 `@@@IMG_5@@@`
- **末尾不写预告**(32 是 4 篇一组收束篇 + 双数实践篇,按 §5.2 节奏新规则**正文末尾不写任何"下一篇"预告**),直接以金句收束在"未来真正会用 AI 的工程师..."上
- **真实锚点**(按 2026-07-01 framework 拆解档案 F1-F21 校准,21 条事实清单完整)
- **framework 仓落地数据**(行业印证):
  - 新服务搭建从天级压缩到小时级
  - 整体交付缩短 30%~40%
  - 架构腐化率近 0(由 AGENTS.md 强制约束)
  - 领域层测试覆盖 ≥ 90%
- **不暴露 framework / gateway / auth-center / user-center / tenant-center 仓库私有编排与未公开 roadmap**
- **不暴露真实客户、真实业务数据、真实账号、真实租户信息**
- **不要写"加 SPI 实现"或"业务订单"等功能延展**,严格落在"DDD/TDD/SDD 三件套在 framework 里的真实落地"上
- **不种草**,framework 仓只作可验证样本印证方法论,不是 framework 教程
- **不写升华/站高/终章/总结全文语气**,直接以金句收束
