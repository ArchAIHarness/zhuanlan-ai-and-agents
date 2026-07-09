# CSDN 浏览器操作手册：别再找 Prompt 模板了：提示词的本质，是你和 AI 的任务契约

## 原则

- 不读取 Cookie、Token、密码、浏览器 profile 或 `.env`。
- 不点击发布或更新，除非用户明确回复“确认发布到 CSDN”或“确认更新 CSDN 文章”。
- 不执行评论、私信、关注、批量运营、引流等动作。
- 出现验证码、安全验证、登录异常、审核提示或账号风险提示时立即停止。

## 安全操作边界

### ✅ 安全操作

- 通过「更多操作 → 导入」导入 Markdown 文件填充正文
- 使用 `execCommand('selectAll') + execCommand('insertText')` 全量替换正文
- 使用 `execCommand('insertText')` 在光标位置插入文本
- 点击工具栏按钮打开对话框（图片、链接、更多插入等）
- 通过 file chooser API 上传文件（封面图、正文图片）
- 使用 `value + dispatchEvent` 设置标题、摘要等输入框内容

### ❌ 禁止操作

- 直接修改编辑器 innerHTML / innerText（会破坏编辑器内部状态）
- 使用 fill() 方法填充编辑器（会清空整个内容）
- 直接操作编辑器 DOM 节点（删除、插入节点）
- 用 createTextNode + appendChild 设置内容（格式会丢失）
- 绕过登录态、验证码、安全验证的任何操作

## 草稿流程

### 第一阶段：基础内容填充

1. 打开 CSDN 创作中心或 Markdown 编辑器。
2. 如未登录，让用户在浏览器页面手动登录。
3. 选择 Markdown 编辑器或确认当前编辑器支持 Markdown。
4. **推荐方式**：点击「更多操作 → 导入」选择 `article.csdn.md` 导入内容。
5. 修正标题：导入后标题会变成文件名，需手动设置正确标题。
   - 设置方式：`titleInput.value = 标题` + dispatchEvent 触发 input/change 事件
   - 降级选择器：`input[placeholder*="标题"]` → `#txtTitle` → `.article-title input`
6. 填写或核对分类、标签和原创/转载/翻译声明。

### 第二阶段：图片上传（有图片时执行）

本文无正文配图，跳过图片上传阶段。



### 第三阶段：元信息完善

1. 填写摘要（80-160 字，不含敏感信息）。
2. 设置分类和标签（2-5 个技术标签）。
3. 确认原创/转载/翻译声明。
4. 上传封面图（如有）。

### 第四阶段：验收与发布前检查

1. 切换到预览模式检查：
   - 代码块闭合且高亮正常
   - 所有图片正常显示（无「外链图片转存失败」）
   - 外链可访问
   - 目录结构正确
   - 标题与正文首屏一致
2. 保存草稿。
3. 停在发布前，等待用户明确回复“确认发布到 CSDN”。

## 降级选择器参考

CSDN UI 可能变化，每个操作建议准备 2-3 个选择器，第一个失败就试下一个。

| 操作 | 首选选择器 | 降级选择器 | 备选 |
|------|-----------|-----------|------|
| 标题输入框 | `input[placeholder*="标题"]` | `#txtTitle` | `.article-title input` |
| 工具栏图片按钮 | 「更多插入」左侧第二个按钮 | `button[aria-label*="图片"]` | `button[title*="图片"]` |
| 标签输入框 | `input[placeholder*="请输入文字搜索"]` | `input[placeholder*="标签"]` | `.tag-dialog input` |
| 摘要输入框 | `textarea[aria-label*="摘要"]` | `textarea[placeholder*="摘要"]` | `#txtSammary` |
| 保存草稿按钮 | `button:has-text("保存草稿")` | `.button-save` | `button[aria-label*="保存"]` |
| 发布文章按钮 | `button:has-text("发布文章")` | `.publish-btn` | `button[aria-label*="发布"]` |

## 验收重点

- 标题与正文首屏一致。
- 摘要没有敏感信息和夸大表达。
- 分类和标签符合文章主题。
- 原创声明选择正确。
- 代码块闭合且高亮正常。
- 图片显示正常（0 张全部渲染，无转存失败提示）。
- 外链可访问。
