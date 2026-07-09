# 浏览器操作剧本 · CSDN · 34_为什么我的AI创课助手不会写糊

> 渠道包:CSDN 专栏《看懂AI和智能体》
> 来源正文:`34_为什么我的AI创课助手不会写糊——SDD把追问规范长期挂载、TDD把每一个JSON字段都验证.md`
> 主编指派日期:2026-07-02

---

## 0. 发稿前置门禁(§7.4,全平台强制)

**本剧本只是草稿准备 + 浏览器操作,真正发布前主编必须用 `question` 工具单独确认一次**:
> 当前内容已完成主编验收和审核初审,是否确认开始发布到 CSDN 草稿?

- 用户明确回复"确认"或同类肯定 → 进入 Step 1
- 用户回复"否/等等/先停"或任何犹疑 → 立即停止,回到主编验收/审核环节
- **不得合并征询**;每个平台发布前都要单独问一次(本剧本只覆盖 CSDN,知乎/掘金 各有独立剧本)

---

## 1. 登录

- 入口:`https://editor.csdn.net/md?not_checkout=1&articleId={id}`(凭 session cookies 直入)
- 不进登录页(如有 cookies);若 cookies 过期:用账号密码 / 微信扫码 / 短信验证码登录
- 验证方法:页面右上角显示当前 CSDN 账号头像

---

## 2. 进入编辑器

- 入口 URL:`https://editor.csdn.net/md?not_checkout=1&articleId={id}`(新建草稿不带 `articleId` 也能进)
- 编辑器类型:bytemd-like(主区有 `.editor__inner` 节点)
- 关闭可能弹出的"新人引导"弹窗(右上角 × 或底部"知道了")

---

## 3. 正文 + 图 + 封面注入(顺序不可调,按 §7.4)

### 3.1 标题

- 找到页面顶部输入框:`input[placeholder*="标题"]`
- 用 `value` setter + `input` 事件触发(不是简单的 `type`),写入:
  ```
  为什么我的 AI 创课助手不会写糊——SDD 把追问规范长期挂载、TDD 把每一个 JSON 字段都验证
  ```

### 3.2 正文注入

- 主元素:`.editor__inner`
- 用 `document.execCommand('insertText', false, articleCsdnMarkdown)` 注入完整 Markdown(已剥离 H1)
- 比 import 文件更可控(§7.4 明文)
- **不点击"导入.md"按钮**(走 `execCommand` 路径)

### 3.3 配图插入(5 张,逐张,位置逐段核对;必须在发布设置之前完成)

按 `publish-checklist.md` "图片位置核对"逐张插入。每张图操作流程:

1. **定位光标**:用 Selection API 找到目标 `cledit-section` 节点
2. **点击图片按钮**:**必须用 CDP 鼠标事件**(`Chrome DevTools MCP click` 工具),不用 Playwright `.click()` —— CSDN 的 Vue 组件会拦截 Playwright click
3. **触发 file chooser**:按钮点击后弹出文件选择对话框
4. **上传文件**:`Playwright setInputFiles` 上传 `assets/34_.../0X-*.png`
5. **等待 CDN URL 插入**:CSDN 上传到 `i-blog.csdnimg.cn/direct/{hash}.png`
6. **位置校验**:插入后对比该图前后的文字段落

若位置错误:从 DOM 删除该 `cledit-section`(从高索引到低索引),提取 CDN URL,在正确位置用 `execCommand('insertText', false, '![alt](url)')` 重新插入。

**图片 URL 劫持修复**(关键):编辑器会包装为 `img-home.csdnimg.cn/images/...{hash}.png?origin_url=...`,需正则替换回原 `i-blog.csdnimg.cn/direct/{hash}.png` CDN URL。

### 3.4 封面注入

- 找到右侧栏"封面"区域
- 上传 `assets/34_为什么我的AI创课助手不会写糊——SDD把追问规范长期挂载、TDD把每一个JSON字段都验证/cover.png`
- CSDN 封面 16:9 自动适配

---

## 4. 发布设置(右侧栏按合法顺序填,§7.4)

按 `publish-checklist.md` "发布前必备检查"清单逐项填。**顺序不可调**:

1. **封面图**(已在 3.4 上传,确认已显示)
2. **标签**:`人工智能` / `AI编程` / `SDD`(右侧栏「添加标签」input)
3. **摘要**:`33 篇把含糊需求剥成 9 字段 JSON,34 篇把 AI 创课助手的智能厨房搭出来:DDD 三限界切分工种、SDD 双端让 ADD 菜谱表长期挂载、TDD 三层闸拦截写糊 JSON。AI 不懂 ADD 但跑得更稳,一次创建多次复用,价值复利。`(右侧栏「摘要」textarea)
4. **分类专栏**:`人工智能`(右侧栏「分类」下拉) + 专栏《看懂AI和智能体》(右侧栏「添加到专栏」+ 搜索「看懂AI和智能体」)
5. **文章类型**:**原创**(勾选)
6. **可见范围**:**全部可见**

---

## 5. 保存草稿(终态)

- CSDN 编辑器在所有设置完成后自动保存草稿
- **不得点击「发布文章」「定时发布」「确定并发布」**
- 草稿 URL 形如:`https://editor.csdn.net/md?not_checkout=1&articleId={id}`
- 记录 articleId 记入 `metadata.json` 的 `draft_id` 字段

---

## 6. 通知主编验收

向主编汇报:

- ✅ 草稿已就绪
- 📋 articleId(从 URL 中提取)
- 🔗 草稿 URL
- 📸 草稿页面截图(存 `.var/screenshots/34_csdn_draft.png`)

---

## ⚠️ 红线(§7.4 强制,绝对不可越界)

- **不得点击「发布文章」「定时发布」「确定并发布」** 等任何公开按钮
- **不得向需求方直接汇报** 发布进度,完成后必须通知主编验收
- **不得修改正文内容**(§7.2 + 主编约束);只搬运 `article.csdn.md` 原文
- 图片按钮必须通过 **CDP 鼠标事件**(`Chrome DevTools MCP click` 工具)点击;Playwright `.click()` 会被 Vue 拦截,不可用
- 临时文件必须放 `.var/{temp,caches,screenshots}/`,绝不放 studio 根目录
- 主编发布后,按 §7.3 自动捕获正式链接到 `metadata.json` 的 `published_url` 字段
- **34 篇是双数实践篇,按 §5.2 节奏新规则,正文末尾无下一篇预告**(已在 metadata.json `notes` 字段标记)
