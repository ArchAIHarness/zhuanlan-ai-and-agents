# 28 篇配图清单

> 配图不嵌入正文，由插画专员按本清单生成（风格：手绘教育插图，暖色调奶油纸背景 + 黑色草图线 + 柔和粉彩色块 + 右手写体中文标签 + 右下角 ArchAIHarness 水印）。
>
> 本文件为第 28 篇《AI 不是 AI 写代码，是 AI 在秩序内写代码——我用 gateway + auth + user + tenant 串起一条多租户认证流程》的配图生成 brief。

## 封面（cover.png）

- 核心概念：三个限界上下文 + 一个平台层的清晰分层
- 视觉建议：分层蛋糕图，最上层是 platform（gateway，灰色），下面三块分别是 auth（蓝色）/ user（绿色）/ tenant（橙色）三个限界上下文；底部一行小字 "x-user-id · x-tenant-id · x-tenant-ids" 共享内核
- prompt 草稿：暖色调奶油纸背景，黑色草图线条，柔和粉彩色块。画面分四层：最上层是一台"反应式 API 网关"小方块（灰色，标 "gateway · 平台层 · 不持有业务语义"）；下面一层是三块拼在一起的方块（蓝/绿/橙，分别标 "auth-center 认证上下文" / "user-center 用户上下文" / "tenant-center 租户上下文（权威源）"）；最底层一条灰色横线写着 "Shared Kernel · x-user-id · x-tenant-id · x-tenant-ids"。右侧用三个箭头标出 "Feign 客户-供应商"、"Kafka 发布-订阅"、"SPI 开放主机服务"。右下角 ArchAIHarness 水印。底部手写体标签："架构师定义秩序 · AI 在秩序内写代码"。

## 图 1：开篇反差图——放手 vs 在赛道（位于 §一）

- 核心概念：你以为的"AI 自主开发" vs 真实的"AI 在秩序内自主开发"
- 视觉建议：左右对比图
- prompt 草稿：暖色调奶油纸背景，黑色草图线条，柔和粉彩色块。左右两栏：左栏一位 AI 小人站在开放草地上自由奔跑，周围散落着混乱的代码文件（标 "user 表 + tenant 表 + token 全混一起"），底下写 "放手让它跑 = 架构腐化"；右栏同一位 AI 小人站在红色跑道内沿着清晰赛道跑，跑道外立着 "P0 红线 / Header 小写 / DDD 分层 / 覆盖率门槛" 的牌子，跑道内画着 "6 个 SPI / Feign / Kafka / AGENTS.md"，底下写 "在赛道里跑 = AI 自主开发"。中间一条灰色虚线分开两栏，标注 "前者混乱 / 后者秩序"。右下角 ArchAIHarness 水印。

## 图 2：四个组件的完整分层图（位于 §二）

- 核心概念：三个限界上下文 + 一个平台层 + 共享内核
- 视觉建议：分层图（用 ASCII 风格画）
- prompt 草稿：暖色调奶油纸背景，黑色草图线条，柔和粉彩色块。画面纵向分四层，从上到下：① 最顶层一块灰色横条写 "Platform Layer · gateway · 6 SPI + @ConditionalOnMissingBean"；② 中间三大块并列（蓝/绿/橙），分别写 "auth-center · AccessToken/AuthCode/AccessSecret"、"user-center · User/Account/AccessKey/Role/TenantUser (缓存)"、"tenant-center · Tenant/TenantUser (权威源)"，三块之间有箭头标 "Feign 客户-供应商" 和 "Kafka 发布-订阅"；③ 底层一条窄横条写 "Shared Kernel · x-user-id · x-tenant-id · x-tenant-ids"；④ 右上角小字 "gateway/pom.xml 单模块 · 无 domain/application/interfaces 分层"。右下角 ArchAIHarness 水印。

## 图 3：链路 A 时序图——AK/SK 换 accessToken（位于 §三）

- 核心概念：client → gateway → auth-center → user-center 的客户-供应商映射
- 视觉建议：时序图 + 上下文边界标注
- prompt 草稿：暖色调奶油纸背景，黑色草图线条，柔和粉彩色块。横向时序图，从左到右四个角色：Client / gateway（灰色）/ auth-center（蓝色虚线框）/ user-center（绿色虚线框）。时序：Client → gateway `POST /token {ak, sk}` → auth-center `createAccessToken` → user-center `POST /access/validate (Feign)` → 返回 `accessId + roleIds` → auth-center `AccessToken.create() + Tokener.generate(jwt)` → 返回 `access_token + refresh_token`。auth-center 虚线框右上角标 "聚合根 AccessToken"；auth → user 的箭头下方标 "←─── customer-supplier ───→"；auth 内部 `AuthCode.java:120` 标注为小灯 "USED 状态机焊死"。右下角 ArchAIHarness 水印。

## 图 4：链路 B 时序图——Token 校验 + 多租户透传（位于 §四）

- 核心概念：Token 校验 + 多租户透传，gateway 防腐层（OHS + ACL）
- 视觉建议：时序图 + SPI 标注
- prompt 草稿：暖色调奶油纸背景，黑色草图线条，柔和粉彩色块。横向时序图，从左到右五个角色：Client / gateway（灰色大虚线框，里面分块标 6 个 SPI）/ InMemory Cache / auth-center（蓝色）/ Downstream（绿色）。时序：Client → gateway `Authorization: Bearer xxx` → TokenExtractor 提取 → AuthenticationCache 查 → 命中/未命中分支（未命中调 TokenIntrospector → auth introspect）→ TenantAccessValidator 校验 → HeaderEnricher 写入 `x-user-id/x-tenant-id/x-tenant-ids` → 转发 Downstream。每个 SPI 用不同色块标注；gateway 大虚线框上方标 "开放主机服务 + 防腐层（主过滤器只编排）"；gateway 框内 Jwts.parser().unsecured() 处标 "读 exp 不验签 · 单一权威在 auth"。右下角 ArchAIHarness 水印。

## 图 5：链路 C 时序图——租户成员变更同步（位于 §五）

- 核心概念：tenant-center → Kafka → user-center 的发布-订阅 + 幂等保证
- 视觉建议：时序图 + 事件 schema 标注
- prompt 草稿：暖色调奶油纸背景，黑色草图线条，柔和粉彩色块。横向时序图，从左到右六个角色：Admin / tenant-center（橙色虚线框）/ t_tenant_user（DB 图标）/ Kafka（紫色，标 topic = "tenant_user_event_topic (Published Language)"）/ user-center（绿色虚线框）/ t_user_tenant（DB 图标）。时序：Admin → tenant-center `PUT /tenant/{id}/users` → `TenantUserAppService.update()` → 实时查 `t_tenant_user` → `savedEvent()` 注册事件 → Kafka → user-center `KafkaEventConsumer` 消费 → `TenantServiceImpl.save()` 检查 userId/roles 变化（幂等）→ UPSERT `t_user_tenant`。Kafka 上方小框列事件 schema 字段："tenantUserId / tenantId / userId / roleIds（P0：@NoArgsConstructor + 非 final）"。tenant-center 虚线框右上角标 "权威源 · saveEvent() 焊死"。右下角 ArchAIHarness 水印。

## 图 6：硬秩序 vs 软秩序对照图（位于 §六）

- 核心概念：三个限界上下文焊边界（钢墙）vs 平台层放选择（旋转门）
- 视觉建议：左右对比图
- prompt 草稿：暖色调奶油纸背景，黑色草图线条，柔和粉彩色块。左右对照：左栏一堵钢铁焊死的钢墙，墙顶立着三块焊死的标牌（手写体）："P0 红线"、"Header 全小写"、"domain 零 Spring"；墙外立红色警示牌 "不许越"；墙内标 "三个限界上下文 = 硬秩序"；墙下小字 "乐谱上的音符"。右栏一扇敞开的旋转门，门内是六个可替换的方块（标 "TokenExtractor / TokenIntrospector / AuthenticationCache / TenantAccessValidator / HeaderEnricher / TokenRenewer"），每个方块下面挂一个可选实现（"Redis / Caffeine / JWT / OPA / MapStruct / Lombok"）；门上方挂绿色牌 "随便换"；门下标 "平台层 = 软秩序"；门下小字 "表情记号（强弱、快慢由指挥定）"。左下角写 "framework 告诉你不能做什么"，右下角写 "gateway 告诉你可以怎么做"。右下角 ArchAIHarness 水印。
