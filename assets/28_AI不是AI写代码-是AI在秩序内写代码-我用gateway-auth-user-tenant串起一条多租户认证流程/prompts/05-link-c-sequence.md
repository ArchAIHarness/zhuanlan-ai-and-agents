手绘教育插图风格, 暖色调奶油纸背景(#F5F0E8), 黑色草图线条(#2C2C2C), 柔和粉彩色块(橙色#E8A87C 绿色#85BAA1 蓝色#7BA7C9 棕色#D4A574)

画面构图: 横向时序图, 中间是 Kafka 紫色图标, 两侧是发布者和订阅者, 配 DB 图标

顶部横幅(手写体粗标): '链路 C: 租户成员变更事件同步'

六个角色(从左到右):
1. Admin(灰色方块, 标 '管理员'): 一个用户小人图标, 手拿一个扳手
2. tenant-center(橙色#E8A87C 虚线大框, 标 '租户上下文(权威源)'): 框右上角红章 'saveEvent() 焊死', 框内一个 'TenantUserAppService' 小标签
3. t_tenant_user(数据库小图标, 标 't_tenant_user'): 一个圆柱数据库图标
4. Kafka(紫色#B19CD9 大圆角方块, 标 'Kafka'): 
   - 圆块内写一行大字: 'topic = tenant_user_event_topic'
   - 副标: 'Published Language'
   - 上方挂一个小白板框, 列事件 schema:
     - 'tenantUserId'
     - 'tenantId'
     - 'userId'
     - 'roleIds'
     - 下方小字: 'P0: @NoArgsConstructor + 字段非 final'
5. user-center(绿色#85BAA1 虚线大框, 标 '用户上下文(缓存)'): 框内一个 'KafkaEventConsumer' 小标签 + 'TenantServiceImpl' 标签
6. t_user_tenant(数据库小图标, 标 't_user_tenant'): 一个圆柱数据库图标

时序消息(从上到下):
- 箭头 1: Admin → tenant-center, 标签 'PUT /tenant/{id}/users'
- 箭头 2(框内流转): TenantUserAppService.update()
- 箭头 3(下钻): tenant-center → t_tenant_user, 标签 '实时查 (不允许用 x-accessible-tenants Header)'
- 箭头 4(自循环): tenant-center 内部, 标签 'savedEvent() 注册事件'
- 箭头 5: tenant-center → Kafka, 标签 'publish event'
- 箭头 6: Kafka → user-center, 标签 'consume event'
- 箭头 7(框内流转): user-center 内部, 标签 'TenantServiceImpl.save() · 检查 userId/roles 变化(幂等)'
- 箭头 8(下钻): user-center → t_user_tenant, 标签 'UPSERT'

Kafka 上方小白板框列出 schema 字段(手写体小字)
tenant-center 虚线框右上角红章 'saveEvent() 焊死'
Kafka 圆角方块左侧画一条细线表示 '发布-订阅', 右侧 '消费订阅', 顶端标 '领域事件 = 共享语言'

底部一行小字(手写体): 'DDD 发布-订阅 + 幂等保证 + DomainEvent 序列化规范'

右下角微妙 ArchAIHarness 水印
16:9 横版, 无深色背景无3D无写实人物
