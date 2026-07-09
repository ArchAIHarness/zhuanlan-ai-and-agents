# CSDN 浏览器操作手册 - 23篇

## 安全操作边界

### 安全操作
- 通过「更多操作 → 导入」导入 Markdown 文件填充正文
- 使用 `execCommand('insertText')` 全量替换正文
- 通过 file chooser API 上传文件
- 使用 `value + dispatchEvent` 设置标题、摘要等输入框内容

### 禁止操作
- 不使用 element.innerText 设置编辑器内容
- 不使用 Playwright fill() 方法填充编辑器
- 不直接操作编辑器 DOM 节点
- 不点击「发布文章」「定时发布」按钮

## 发布设置步骤
1. 登录CSDN → 进入博客管理
2. 点击「写文章」
3. 使用 execCommand('insertText') 注入 article.csdn.md 正文
4. 上传配图（按 images.map.json 逐一上传）
5. 设置标题 → 封面图 → 标签 → 摘要 → 分类专栏 → 文章类型 → 可见范围
6. 保存为草稿
7. 🔴 不点击「发布文章」
