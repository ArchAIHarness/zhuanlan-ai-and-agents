手绘教育插图风格, 暖色调奶油纸背景(#F5F0E8), 黑色草图线条(#2C2C2C), 柔和粉彩色块(橙色#E8A87C 绿色#85BAA1 蓝色#7BA7C9 棕色#D4A574)

画面构图: 横向时序图, 顶部一道横幅标题, 下方四个角色的纵向生命线从左到右排列

顶部横幅(手写体粗标): '链路 A: AK/SK 换 accessToken'

四个角色(从左到右, 每个上方一个矩形角色头, 下方一条竖直生命线):
1. Client(灰色方块, 标签 '客户端'): 一个终端/手机小图标
2. gateway(灰色方块, 标签 'API 网关'): 一个网关小图标
3. auth-center(蓝色#7BA7C9 虚线框, 标签 '认证上下文'): 一个锁形图标, 右上角小红章 '聚合根 AccessToken'
4. user-center(绿色#85BAA1 虚线框, 标签 '用户上下文'): 一个用户小人图标

时序消息(从上到下, 每个箭头水平横穿两到四个角色, 箭头边有手写标签):
- 箭头 1: Client → gateway, 标签 'POST /token {ak, sk}'
- 箭头 2: gateway → auth-center, 标签 'createAccessToken'
- 箭头 3: auth-center → user-center, 标签 'POST /access/validate (Feign)', 下方虚线小字 '←─── customer-supplier ───→'
- 箭头 4(虚线返回箭头): user-center → auth-center, 标签 '返回 accessId + roleIds'
- 箭头 5: auth-center 内部(自循环), 标签 'AccessToken.create() + Tokener.generate(jwt)', 旁边画一个小灯标 'USED 状态机焊死'
- 箭头 6(虚线返回箭头): auth-center → gateway, 标签 'access_token + refresh_token'
- 箭头 7(虚线返回箭头): gateway → Client, 标签 '返回 token'

auth-center 虚线框右上角画一个红色小章 '聚合根 AccessToken'
auth-center 框内 'AuthCode.java:120' 位置画一个小灯泡, 标 'USED 状态机焊死'

底部一行小字(手写体): 'DDD 边界 + Feign 客户-供应商 + TDD 覆盖 + AGENTS.md P0 红线'

右下角微妙 ArchAIHarness 水印
16:9 横版, 无深色背景无3D无写实人物
