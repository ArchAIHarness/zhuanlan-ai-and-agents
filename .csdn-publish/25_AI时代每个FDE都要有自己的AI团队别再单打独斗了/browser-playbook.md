# 浏览器操作剧本 · CSDN · 25_AI时代每个FDE都要有自己的AI团队别再单打独斗了

## 入口
- 直达: `https://editor.csdn.net/md?not_checkout=1&articleId={id}`
- 不进登录页（凭 session cookies 直接进）

## 编辑器
bytemd-like (有 .editor__inner)

## 关键 DOM 元素（待验证，可能因改版变化）
- 标题: input[placeholder*="标题"]
- 正文: 编辑器主元素
- 分类: 右侧栏「分类」下拉
- 标签: 右侧栏「添加标签」input
- 专栏: 右侧栏「添加到专栏」+ 搜索「看懂AI和智能体」
- 封面上传: 右侧栏「封面」+ 选择文件
- 摘要: 右侧栏「摘要」textarea
- 保存按钮: 保存草稿

## 关键操作
1. 进编辑器，关闭可能弹出的引导弹窗
2. 设置标题
3. 注入正文（execCommand insertText 或 setValue）
4. 上传正文配图
5. 设置元信息（标签/分类/专栏/封面/摘要）
6. 点击「保存草稿」

### CSDN 特殊
- 编辑器主元素: `.editor__inner`（textContent 设置）
- 标题单独字段，用 value setter + input 事件触发
- 配图按钮: `button[data-title*="图片"]` → file chooser
- 图片 CDN: `i-blog.csdnimg.cn/direct/{hash}.png`
- **图片URL劫持修复**（关键）: 编辑器会包装为 `img-home.csdnimg.cn/images/20230724024159.png?origin_url=...`，需正则替换回原CDN URL


## 红线
- 不点击「发布文章」、「定时发布」按钮
- 只点「保存草稿」
- 临时文件必须放 `.var/{temp,caches,screenshots}/`，绝不放studio根目录
