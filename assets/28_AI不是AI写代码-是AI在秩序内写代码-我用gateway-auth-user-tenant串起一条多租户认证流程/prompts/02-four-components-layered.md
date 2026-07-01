手绘教育插图风格, 暖色调奶油纸背景(#F5F0E8), 黑色草图线条(#2C2C2C), 柔和粉彩色块(橙色#E8A87C 绿色#85BAA1 蓝色#7BA7C9 棕色#D4A574)

画面构图: 纵向四层分层图, 中间用清晰的水平线分隔, 自上而下

顶部横幅(手写体粗标): '四个组件的清晰分层'

第一层(最顶层, 灰色横条, 较薄):
- 居中一个灰色方块图标(反应式 API 网关示意), 标签手写体: 'Platform Layer · gateway'
- 右边一行小字: '6 SPI + @ConditionalOnMissingBean'
- 最右角小图标: 'WebFlux + Reactor 反应式纪律'

第二层(中间三大块并列, 等宽, 用细虚线隔开):
- 左块(蓝色#7BA7C9, 占 1/3 宽度): 
  * 上方一个锁形图标
  * 标签手写体粗: 'auth-center · 认证上下文'
  * 下方列出聚合根: 'AccessToken / AuthCode / AccessSecret'
  * 下方小字: '上游: user-center (Feign)'
- 中块(绿色#85BAA1, 占 1/3 宽度):
  * 上方一个用户小人图标
  * 标签手写体粗: 'user-center · 用户上下文'
  * 下方列出聚合根: 'User / Account / AccessKey / Role / TenantUser(缓存)'
  * 下方小字: '上游: tenant-center (Kafka)'
- 右块(橙色#E8A87C, 占 1/3 宽度):
  * 上方一个办公楼小图标
  * 标签手写体粗: 'tenant-center · 租户上下文'
  * 下方列出聚合根: 'Tenant / TenantUser(权威源)'
  * 下方小字: '下游: user-center (Kafka)'

第二层三大块之间画细虚线连接箭头, 标 'Feign 客户-供应商' (左到中) 和 'Kafka 发布-订阅' (右到中)

第三层(底层窄横条, 棕色调, 横贯):
- 居中手写体: 'Shared Kernel · Header 规范'
- 横条上三个小标签: 'x-user-id · x-tenant-id · x-tenant-ids'
- 最右边小字: '四仓横向交叉遵守, 不许任何上下文私自扩展'

右上角小字批注(手写体): 'gateway/pom.xml 单模块 · 无 domain/application/interfaces 分层'
右中角小字: '三仓六模块分层, domain 零 Spring'

画面底部一行小字(手写体): '三个限界上下文 + 一个平台层 = AI 自主开发的工厂'

右下角微妙 ArchAIHarness 水印
16:9 横版, 无深色背景无3D无写实人物
