手绘教育插图风格, 暖色调奶油纸背景(#F5F0E8), 黑色草图线条(#2C2C2C), 柔和粉彩色块(橙色#E8A87C 绿色#85BAA1 蓝色#7BA7C9 棕色#D4A574)

画面构图: 横向时序图, gateway 用一个大的灰色虚线大框包围, 内部分块标 6 个 SPI, 框上方写 '开放主机服务 + 防腐层'

顶部横幅(手写体粗标): '链路 B: Token 校验 + 多租户上下文透传'

五个角色(从左到右, 每个上方一个矩形角色头, 下方一条竖直生命线):
1. Client(灰色方块, 标签 '客户端')
2. gateway(大灰色虚线框, 占据中间主要区域, 标签 'API 网关'): 框内分 6 个色块, 横向排列, 每个色块标一个 SPI:
   - 蓝块: 'TokenExtractor'
   - 绿块: 'AuthenticationCache'
   - 橙块: 'TokenIntrospector'
   - 棕块: 'TenantAccessValidator'
   - 紫块: 'HeaderEnricher'
   - 浅蓝块: 'TokenRenewer'
   - 大框下方写一行小字: '主过滤器只编排, 不持有业务'
   - 大框上方写: '开放主机服务 + 防腐层'
3. Cache(浅黄色小框, 标 'InMemory Cache'): 在 gateway 框内旁画, 表示本地缓存
4. auth-center(蓝色#7BA7C9 虚线框, 标 '认证上下文')
5. Downstream(绿色#85BAA1 虚线框, 标 '下游服务'): 一个齿轮+箭头小图标

时序消息(从上到下):
- 箭头 1: Client → gateway, 标签 'Authorization: Bearer xxx'
- 箭头 2(框内流转): TokenExtractor 提取 → AuthenticationCache 查
- 箭头 3(分叉): 命中走 cache, 标签 '命中' (绿色箭头); 未命中走下方分支, 标签 '未命中'
- 箭头 4: gateway → auth-center, 标签 'POST /introspect (Feign)'
- 箭头 5(虚线返回): auth-center → gateway, 标签 '返回 userId + roleIds + exp'
- 箭头 6(框内流转): TenantAccessValidator 校验租户权限
- 箭头 7(框内流转): HeaderEnricher 写入三个 Header, 标签 'x-user-id / x-tenant-id / x-tenant-ids'
- 箭头 8: gateway → Downstream, 标签 '转发 + 注入 Headers'
- 旁注小字: 'Jwts.parser().unsecured() · 读 exp 不验签 · 单一权威在 auth'

gateway 大虚线框右上角画一个蓝色小章 '防腐层(ACL)'
gateway 框内一个角落画一个细线小框, 标 'Jwt 解析', 旁边小字 '读 exp 不验签'

底部一行小字(手写体): 'gateway 软秩序: 6 SPI + 反应式纪律 + HeaderEnricher 可替换'

右下角微妙 ArchAIHarness 水印
16:9 横版, 无深色背景无3D无写实人物
