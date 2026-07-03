# 2026-07-02 · CSDN 33+34 篇发布流水与 Skill 迭代沉淀

> 适用范围:`看懂 AI 与智能体`专栏 33 篇(业务心智篇)+ 34 篇(工程落地篇)在 CSDN 平台的草稿落地。本文件作为该次发布的可追溯档案 + publisher 提的 csdn-publisher-v2 Skill 7 条迭代建议沉淀。

---

## 一、流水线摘要

| 项 | 33 篇 | 34 篇 |
|---|---|---|
| **任务边界** | 补完发布设置(原草稿已存在)| 从 0 创建草稿 |
| **articleId** | `162520055`(原值,稳定) | `162523900`(新分配) |
| **草稿 URL** | `https://editor.csdn.net/md?not_checkout=1&articleId=162520055` | `https://editor.csdn.net/md?not_checkout=1&articleId=162523900` |
| **详情页 URL(发布后)** | `https://blog.csdn.net/wzx_cx/article/details/162520055` | `https://blog.csdn.net/wzx_cx/article/details/162523900` |
| **状态** | 草稿 | 草稿 |
| **正文字符数** | 23683 | 14307 |
| **正文 section 数** | 194 | 179 |
| **配图数** | 5 | 5 |
| **配图 hash(取第一张作印记)** | i-blog CDN 已就位 | i-blog CDN 已就位 |
| **封面** | 独立 i-blog CDN 已就位 | 独立 i-blog CDN 已就位 |
| **专栏** | 看懂AI和智能体(本次新勾)| 看懂AI和智能体(本次新建勾选) |
| **标签** | 人工智能 · AI编程 · 语言模型 | 人工智能 · AI编程 · SDD |
| **摘要字数** | 150 | 123 |
| **文章类型** | 原创 | 原创 |
| **可见范围** | 全部可见 | 全部可见 |
| **多平台发布** | 否 | 否 |
| **保存状态** | ✓「文章已保存 16:28:43」 | ✓「文章已保存 16:44:42」 |
| **回写 metadata.json** | 无变化(原值都对)| 新增 draft_id/URL/已写新值 |
| **AGENTS.md 更新** | §二 状态列已更新 + 备注 | §二 链接列已填 + 状态备注 |
| **artifactId 失效兜底** | 稳定,无需兜底 | 稳定,无需兜底 |
| **发布时间** | 由用户手动确认(本次不发布)| 由用户手动确认(本次不发布)|

> **关键边界**:本流水**严禁**任何「发布」类按钮被点击。仅「保存草稿」「补完发布设置」。发布动作须由用户在 CSDN 编辑器手动执行,届时 §7.3 发布链接自动归档流程接管。

---

## 二、§7.4 发稿前置门禁执行记录

| 阶段 | question 状态 | 用户回复 | 后续动作 |
|---|---|---|---|
| 启动 CSDN 流水线前 | ✅ 已用 `question` 工具向用户确认 | 用户回复"确认启动" | publisher 子任务派单,CSDN 33+34 推进 |
| 启动掘金流水线前 | 🔄 进行中(下一轮执行)| - | - |

---

## 三、临时文件清理决策

publisher 报告里 34 篇渠道包产生了 .bak 文件:

- `article.text.md.bak`(publisher 自动备份,逐行删除图片 markdown 前的原稿)
- `metadata.json.bak`(publisher 自动备份,回写 articleId 前的原稿)

**决策**:按专栏「体系审计」主张与 §5.6 配图备份纪律精神,**保留** .bak 文件**就地存放**(与原文件同目录,不另开归档)。

- 含义:可回滚 / 可对照修改前后差异
- 命名规则沿用 publisher 的 `<name>.bak` 风格
- 后续若 publisher 再次回写 metadata.json,可考虑 `metadata.json.bak2` 递增 — 本批因为只回写一次,留 .bak 即可

---

## 四、csdn-publisher-v2 Skill 迭代建议沉淀

publisher 报告 7 条经验沉淀,本文件按"问题 + 解决 + 状态"三段式记下,供主编(content-master)后续迭代该 Skill 时采纳。

### 4.1 正文 textContent 注入的解析机制

- **问题**:对 csdn-publisher-v2 Step 4「文件输入元素注入法」的 `editor.innerText = md` 路径不熟,担心 markdown 语法会被转义。
- **解决**:实测 CSDN 的 bytemd/cledit 是「token 高亮」而非「html 渲染」——`#` 解析为 h1 token、`**` 解析为粗体 token,渲染由 CSDN 自家 markdown 引擎接管,**不需要在注入端做转义**。
- **状态**:沉淀到 skill Step 4 注释,**不阻塞本批任务**。

### 4.2 `@@@IMG_N@@@` 占位符策略与实际图片 markdown 残留

- **问题**:skill 默认 `article.csdn.md` 用 `@@@IMG_N@@@` 占位符(便于 sed 删除)。但本批 33/34 实际用的是真实 `assets/...` 路径,sed 匹配 `@@@IMG_` 会"不命中任何东西"导致 text.md 没被清理,markdown 残留 → CSDN 显示为断图占位。
- **解决**:publisher 本次用 Python 一行(精确匹配 `![...](assets/...)`)剥离图片 markdown。Skill 应增加一行 `sed -E 's/!\[[^]]*\]\(assets\/[^)]+\)//g' article.csdn.md > article.text.md` 或更安全的 Python 模板。
- **状态**:**Skill 迭代优先级 P1**。下次发布前必须先修。

### 4.3 Vue `el-tag` close 按钮的"半失效"现象

- **问题**:点 `el-tag` 里的 `.el-tag__close` 删除标签时,UI 上看已删,但 Vue 内部状态 stale(尤其在 dropdown 打开时)。后续添加新标签时会把"看似已删"的标签又带回来。
- **解决**:每次删除后等 800~1000ms 再重查 DOM,或关闭重开 modal 让 Vue 重新 fetch 真实状态。
- **状态**:沉淀到 skill Step 4「发布设置 → 标签」节,**不阻塞本批任务**。

### 4.4 CSDN 自动提取「推荐标签」的干扰

- **问题**:用户输入第一个标签时,CSDN 自动填入基于文章关键词的 1~3 个推荐标签(本批 34 篇自动填了"人工智能"/"tdd"/"json")。这些是平台默认的、非用户主动选择,**必须删掉重填**否则污染最终标签列表。
- **解决**:publisher 操作时,见到非预期标签立刻 EntDel 删除,等 DOM 重渲染后再继续。
- **状态**:沉淀到 skill Step 4「发布设置 → 标签」节。**首次接触该字段时必读**。

### 4.5 自定义标签添加方式:Enter 还是点下拉?

- **问题**:skill 此前记录"Enter 不会直接添加,必须点下拉"。本次实测,**Enter 键对自定义标签是有效的**(下拉里没有匹配项时,直接 Enter 把当前文本添加为自定义 tag)。可能因 CSDN 版本而异。
- **解决**:skill 应记录两种 fallback:①Enter 添加自定义 ②下拉 li 选已有。
- **状态**:沉淀到 skill Step 4「发布设置 → 标签」节。

### 4.6 专栏 checkbox 的"看似勾上但未持久化"陷阱

- **问题**:只 `chk.checked = true; dispatchEvent('change')` 不够;必须同时确保页面**验证**显示该专栏出现在「分类专栏」选中列表。
- **解决**:验证方式 — `分类专栏 [专栏名] 新建分类专栏` 这段 innerText 里有没有该专栏名。
- **状态**:沉淀到 skill Step 4「发布设置 → 分类专栏」节。**首次接触该字段时必读**(本批 33 篇就是这个坑)。

### 4.7 大文件正文注入的 fallback:HTTP server + CORS

- **问题**:`article.text.md` 14k 字符太大,Playwright `setInputFiles` + JS `files[0].text()` 路径在某些环境下读不出(可能是浏览器自动 file path 处理有 bug)。
- **解决**:publisher 起了临时 Python http server(配 `Access-Control-Allow-Origin: *`),用 `fetch()` 加载——最稳路径。Skill 应记录为 fallback 路径。
- **状态**:沉淀到 skill Step 4「正文注入」节。

---

## 五、待主编手动操作(用户接管)

| 文章 | 操作 |
|---|---|
| **33 篇 CSDN** | CSDN 编辑器中目检草稿(已就绪),确认无误后手动点「发布文章」按钮 |
| **34 篇 CSDN** | CSDN 编辑器中目检草稿(已就绪,articleId 162523900),确认无误后手动点「发布文章」按钮 |

发布动作由用户执行。发布后,§7.3 「发布链接自动归档」流程接管(publisher 子任务自动捕获详情页 URL,回写 metadata.json + AGENTS.md)。

---

## 六、下一流水线预热

- **掘金平台**:门禁 question 2 待发起。33/34 两个渠道包 metadata 中 `draft_id=null`,需走 juejin-publisher-v2 完整流程(无 articleId 失效兜底机制同 csdn)。
- **本 batch 不动知乎**:专栏 AGENTS.md 33/34 行「知乎」列仍为 🔗 待捕获。

---

## 七、档案责任

- 本文件由 content-master(content-master)创建,见一次 publish 流水、立一份沉淀。
- 沉淀物若有更新(尤其 4.2、4.4、4.6 三条 Skill 迭代),由内容团队次轮 publish 时一并改 .plugins/skills/csdn-publisher-v2/SKILL.md。
- 临时文件清理决策若变更,以本文件第三段为准。
