# CSDN 发布检查清单 · 33_老师想AI帮忙做课

> 渠道包:CSDN 专栏《看懂AI和智能体》
> 来源正文:`33_老师想AI帮忙做课——AI却问了一堆离谱的问题——我才明白真懂业务的是人不是AI.md`
> 主编写卡日期:2026-07-02

---

## 发布前必备检查

- [ ] 浏览器已登录 CSDN(对应账号)
- [ ] metadata.json 字段(标题/标签/分类/专栏/摘要/封面)与 `browser-playbook.md` 流程一致
- [ ] 正文 `article.csdn.md` 中 5 张图片相对路径与 `assets/33_.../0X-*.png` 对应
- [ ] 正文不含 `@@@IMG_N@@@` 占位符
- [ ] 正文不含孤立 `!` 前缀(注入残留)
- [ ] 标题:`老师想 AI 帮忙做课,AI 却问了一堆"离谱"的问题——我才明白真懂业务的是人不是 AI`
- [ ] 标题长度 < 30 字(本篇约 44 字 —— CSDN 长标题可写但需检查前台展示)
- [ ] 摘要字数符合 CSDN 要求:**≤ 150 字**(本包摘要 150 字 ✅)
- [ ] 标签 3 个已选:`人工智能` / `AI编程` / `语言模型`
- [ ] 分类专栏已选:`人工智能`(一级)+ 专栏《看懂AI和智能体》(已订阅)
- [ ] 文章类型已选:**原创**
- [ ] 封面 16:9 已设置:`assets/33_.../cover.png`
- [ ] 可见范围已设:**全部可见**

## 图片位置核对(共 5 张)

1. `01-raw-requirement-bubble-and-laptop.png` — §一前
2. `02-radar-add-eight-dimensions.png` — §三末
3. `03-dialogue-timeline-with-summary-gate.png` — §四处
4. `04-json-knowledge-tree.png` — §五末
5. `05-fde-three-way-collaboration.png` — §六末

## 发布流程(顺序不可调,按 §7.4 门禁)

1. 打开 `https://editor.csdn.net/md?not_checkout=1&articleId={id}`(凭 session cookies 直入)
2. 关闭可能弹出的引导弹窗
3. **正文注入**:`execCommand('insertText')` 注入完整 Markdown(去掉 H1,平台用标题字段)
4. **配图必须在发布设置之前插入**:每张按"定位光标(Selection API) → 点击图片按钮(CDP 鼠标事件,非 Playwright click) → setInputFiles 上传 → 等待 CDN URL 插入"操作
5. **图片位置错误修正**:若图片已上传但位置不对,从 DOM 删除该 `cledit-section`(从高索引到低索引),提取 CDN URL,在正确位置 `execCommand('insertText', false, '![alt](url)')` 重新插入
6. **发布设置合法顺序**:封面图 → 标签 → 摘要 → 分类专栏 → 文章类型 → 可见范围
7. **最终状态只能是「草稿」**,CSDN 编辑器自动保存草稿
8. **不得点击「发布文章」「定时发布」或「确定并发布」**
9. 记录草稿 ID(articleId)记入 `metadata.json` 的 `draft_id` 字段

## 验证清单(发布后,刷新草稿页截图存 `.var/screenshots/`)

- [ ] 标题正确
- [ ] 5 张图位置对应章节,无错位
- [ ] 标签 / 分类 / 专栏正确
- [ ] 摘要完整
- [ ] 文末「关于 ArchAIHarness」出口段完整
- [ ] 无多余 `!` 字符或残留占位符
- [ ] 封面 16:9 正常显示

---

## ⚠️ 红线(§7.4 强制)

- **不得点击「发布文章」「定时发布」「确定并发布」** 等任何公开按钮
- **不得向需求方直接汇报** 发布进度,完成后通知主编验收
- 图片按钮必须通过 **CDP 鼠标事件**(Chrome DevTools MCP `click`)点击;Playwright `.click()` 会被 Vue 拦截,不可用
- 临时文件统一放 `.var/screenshots/`,绝不放 studio 根目录
- 主编发布后,按 §7.3 自动捕获链接到 `metadata.json` 的 `published_url` 字段
