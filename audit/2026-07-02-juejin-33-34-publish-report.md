# 2026-07-02 · 掘金 33+34 篇发布流水与 Skill 迭代沉淀

> 适用范围:`看懂 AI 与智能体`专栏 33 篇(业务心智篇)+ 34 篇(工程落地篇)在掘金平台的草稿落地。本文件作为该次发布的可追溯档案 + publisher 提的 juejin-publisher-v2 Skill 5 条迭代建议沉淀。

---

## 一、流水线摘要

| 项 | 33 篇 | 34 篇 |
|---|---|---|
| **任务边界** | 从 0 创建 | 从 0 创建 |
| **draftId** | `7657781902920925194`(新分配) | `7657831024920231963`(新分配) |
| **草稿 URL** | `https://juejin.cn/editor/drafts/7657781902920925194` | `https://juejin.cn/editor/drafts/7657831024920231963` |
| **详情页 URL(发布后)** | `https://juejin.cn/post/7657781902920925194` | `https://juejin.cn/post/7657831024920231963` |
| **状态** | 草稿 | 草稿 |
| **正文字符数** | 25232(含 5 张 CDN 图) | 17176(含 5 张 CDN 图) |
| **正文字数(纯文本)** | 25228 chars(经主编 read-only 浏览器验证) | 17166 chars(经主编 read-only 浏览器验证) |
| **行数** | 724 | 396 |
| **配图数** | 5 张(p0-xtjj 私链 CDN) | 5 张(p0-xtjj 私链 CDN) |
| **封面** | 独立上传(hash 与正文图片不同)| 独立上传(hash 与正文图片不同)|
| **分类** | 人工智能 | 人工智能 |
| **标签(实际)** | 人工智能 · AI编程 · 后端 | 人工智能 · AI编程(⚠️ SDD 标签缺失)|
| **专栏** | 看懂AI与智能体 | 看懂AI与智能体 |
| **摘要字数** | 76(掘金 ≤100 字限) | 82 |
| **可见范围** | 所有人可见 | 所有人可见 |
| **多平台发布** | 否 | 否 |
| **回写 metadata.json** | draft_id、draft_url、column_id、tags | draft_id、draft_url、tags(去 SDD)、notes |
| **AGENTS.md 更新** | §二 状态列 + 链接列 | §二 状态列 + 链接列 + 备注 SDD 缺失 |
| **draftId 失效兜底** | 全新草稿,无兜底触发 | 全新草稿,无兜底触发 |
| **发布时间** | 用户手动确认(本次不发布)| 用户手动确认(本次不发布)|

> **关键边界**:本流水**严禁**任何「发布」类按钮被点击。仅「保存草稿」「补完发布设置」。发布动作须由用户在掘金编辑器手动执行,届时 §7.3 发布链接自动归档流程接管。

---

## 二、§7.4 发稿前置门禁执行记录

| 阶段 | question 状态 | 用户回复 | 后续动作 |
|---|---|---|---|
| 启动 CSDN 流水线前 | ✅ 已用 `question` 工具向用户确认 | 用户回复"确认启动" | publisher 子任务派单,CSDN 33+34 推进 |
| 启动掘金流水线前 | ✅ 已用 `question` 工具向用户确认 | 用户回复"确认启动掘金" | publisher 子任务派单,掘金 33+34 推进 |
| 启动知乎流水线前 | ❌ 不在本批范围,未征询 | — | — |

---

## 三、临时文件清理决策

publisher 报告里 34 篇渠道包产生了 `.bak` 与 `var/draft.png`:

- `metadata.json.bak`(publisher 自动备份,回写 draftId 前的原稿)
- `var/draft.png`(publisher 自存草稿页面截图,358KB / 283KB)

**决策**:沿用 CSDN 流水 audit `2026-07-02-csdn-33-34-publish-report.md` §三 的统一决策 →

- `metadata.json.bak`**就地保留**(可回滚 / 可对照修改前后差异)。
- `var/draft.png`**就地保留**(publisher 调试证据 + 主编验收可对照)。下次发布时若 `var/` 目录体积显著增长,可在归档阶段批量压缩或迁移。

---

## 四、juejin-publisher-v2 Skill 迭代建议沉淀

publisher 报告 5 条特异性坑(已与 CSDN 流水 7 条对照,本节只记掘金特异性 + 跨平台反向用法)。

### 4.1 正文预处理不能过早剥离图片 markdown(P0 · 掘金特异性 · 本次中招)

- **问题**:audit `2026-07-02-csdn-33-34-publish-report.md` §四.3 第 4.2 条说「article.text.md 提前剥离图片 markdown」是为了走 CSDN 的内联图插入路径。**但掘金的 juejin-publisher-v2 Skill Step 4 算法是按上传顺序回填到原 markdown 的 `assets/...` 位置,boy 文件必须保留 `![alt](assets/...)` 标记**,否则 Step 4 的 split-join 算法找不到替换点,会把图片"剥离出去但 CDN 链接没插回去"(本地路径 0、CDN 0、imgMd 0)。
- **解决**:publisher 发现后立即重做——把 `article.body.md` 还原成"含 5 张图片 markdown"的版本,重新注入 + 重新上传 + 重跑 Step 4,验证 5 张图全部回填成功(`localPathsRemaining=0`、`cdnUrlsInFinal=5`)。
- **Skill 迭代建议**(P0):**Juejin-publisher-v2 Skill Step 2 必须明确写「body 必须保留 5 个 `![alt](assets/...)` 行(不剥离)」**;Step 4 算法依赖这些路径做 split-join。**这是与 CSDN-skill 反向的口径,两个 Skill 必须在 Step 2 互相点名,避免下次 publisher 错用 CSDN 习惯**。

### 4.2 掘金 Enter 键不接收自定义标签(P1 · 掘金特异性 · 跨平台反向)

- **问题**:CSDN 流水 audit 4.5 说「Enter 键对自定义标签有效」,且 audit `2026-07-02-csdn-33-34-publish-report.md` §四.3 把这点当作 skill 兜底。**但掘金实测:输入框里填了不存在于下拉的标签(如 SDD),按 Enter 不会创建标签,反而会清空输入并把最近一次添加的标签(AI编程)一起删掉**(tags 数组从 2 个变成 1 个)。
- **解决**:遇到掘金下拉无匹配的标签,**放弃该标签(不强行加),用现有标签兜底**,回写 metadata.json `notes` 说明。
- **Skill 迭代建议**(P1):juejin-publisher-v2 Skill Step 5 「标签」节必须明确写「**掘金 Enter 不能添加自定义标签,只支持下拉点选;若下拉无匹配,该标签直接跳过,不在 metadata 中保留(除非下拉能命中近似)**」,并把 audit 4.5 的 CSDN Enter 兜底标注「仅 CSDN 适用」。

### 4.3 标签配额上限是 3 不是 2(P3 · 经验修正)

- **问题**:Skill 注释里写「通常 2」是过时经验。本次实测 `.tag-number-container` 提示「你还能添加 1 个标签」时已挂 2 个标签,意味着上限是 **3**。
- **解决**:无影响,只是 quota 比预期宽。
- **Skill 迭代建议**:把「通常 2」改为「通常 3」,并以 tag-number-container 文字为准。

### 4.4 body 注入用 `run_code_unsafe` 路径,不是 `browser_file_upload`(P2 · MCP 工具栈适配)

- **问题**:`playwright_browser_file_upload` 工具要求 `fileChooser modal state` 存在,不能用于 hidden input 直传。Skill 默认描述的「文件输入法」靠 hidden input,本次发现 MCP 工具栈下 `browser_file_upload` 只接受 modal。
- **解决**:本次走 `playwright_browser_run_code_unsafe` 路径成功(`setInputFiles` + `fi.files[0].text()` + `cm.setValue`),比 HTTP server 路径更稳。
- **Skill 迭代建议**(P2):Skill Step 2 注入示例**增加 `run_code_unsafe` 写法作为首选,HTTP server 降为最后 fallback**(本次实测根本用不到 HTTP server)。MCP 工具栈下的 publisher 必须知道 hidden input 路径走 `run_code_unsafe`。

### 4.5 标题输入触发 draftId 自动分配(P3 · 机制澄清)

- **实测**:在 `https://juejin.cn/editor/drafts/new?v=2` 页面输入标题前 `page.url()` 仍是 `?v=2`,**输入标题后 URL 立刻变成 `https://juejin.cn/editor/drafts/<draftId>`**——这意味着"输入标题"就是触发草稿创建的动作,不需要额外"新建草稿"按钮点击。
- **Skill 迭代建议**:Skill Step 1 在 Playwright 路径下应改成"先输入标题拿到 draftId,再注入正文"。这与原文档"打开 → 等 → 设置标题 → 正文" 的流程描述**逻辑相同**(输入标题本来就早于注入正文),只是 skill 注释应该把"draftId 在标题输入后自动生成"这一点写出来,避免 publisher 担心"草稿没新建完就被注入正文会丢失"。

---

## 五、跨平台编辑器差异对照(沉淀到下次复盘)

| 维度 | CSDN | 掘金 |
|---|---|---|
| 编辑器内核 | bytemd / cledit(token 高亮)| CodeMirror(Milkdown/ProseMirror)|
| 注入方式 | 文件输入元素注入法(`editor.innerText = md`)| 文件输入元素注入法 + `cm.setValue`(MCP 工具栈下走 `run_code_unsafe`)|
| 配图 CDN | i-blog CDN(私链) | p0-xtjj-private.juejin.cn(私链)|
| 配图上传 API | `el-upload` + 标签内 inline | 工具栏图片按钮 + 上传 modal |
| 专栏支持 | ✅ 有「分类专栏」checkbox | ✅ 有「专栏」dropdown(用 tag 替代)|
| 自定义标签支持 | ✅ Enter 可加自定义 | ❌ Enter 清空 + 删除最近 tag |
| 草稿创建触发 | 设置标题后 URL 不变,显式「保存」| **输入标题后 URL 自动变化** = draftId 自动分配 |
| `images[]` 数量 | 5 ✓ | 5 ✓ |
| 链接归一规则 | `/article/details/<articleId>` | `/post/<draftId>`(`spost/` 永远不写) |

---

## 六、风险点(请主编关注)

1. **34 篇 SDD 标签缺失** ⚠️
   - 掘金标签库无 `SDD`,Enter 也不接受自定义,与 CSDN 表现不一致(SDD 在 CSDN 33/34 都已成功挂上)。
   - **当前决策**:仅挂 2 个标签 `人工智能 + AI编程`,SDD 跳过,已回写 metadata.json `notes` 字段说明。
   - **建议**:主编可在用户发布前手动在掘金编辑器后台加 SDD 标签(若用户账号支持),或维持 2 个标签状态发布。

2. **metadata.json 标题字段的引号合法性**(已修复,与 CSDN 流水一致)
   - 33 篇 / 34 篇 title 字段含 ASCII `"离谱"` 引号(34 篇也有 `"问问"` 等),直接写 JSON 会破坏格式。本次已用中文弯引号或转义 ASCII 写法修复。原始 metadata.json.bak 是带原引号的版本。

3. **draftId 失效兜底未触发(本批全新,符合预期)**
   - 本批 33/34 都是 null(全新),无需触发 skill 中提到的「权限认证错误 → 新建一份」流程。下次若更新已发布草稿需注意。

4. **草稿未发布(完全符合约束)**
   - 两个 draftId 均处于「草稿」状态(标题设置时自动创建,正文 + 设置完成后点"取消"自动 persist),**未点任何发布/确定并发布/定时发布按钮**。
   - **用户确认发布后,按 §7.3 自动捕获链接到 `published_url` 字段,把进度表的"草稿已就绪"切换为"全平台已发布"**。

---

## 七、待主编手动操作(用户接管)

| 文章 | 操作 |
|---|---|
| **33 篇 CSDN** | CSDN 编辑器中目检草稿(已就绪,articleId 162520055),确认无误后手动点「发布文章」按钮 |
| **34 篇 CSDN** | CSDN 编辑器中目检草稿(已就绪,articleId 162523900),确认无误后手动点「发布文章」按钮 |
| **33 篇 掘金** | 掘金编辑器中目检草稿(已就绪,draftId 7657781902920925194),确认无误后手动点「发布」按钮 |
| **34 篇 掘金** | 掘金编辑器中目检草稿(已就绪,draftId 7657831024920231963),确认无误后手动点「发布」按钮(同时决定是否手动补 SDD 标签)|

发布动作由用户执行。发布后,§7.3「发布链接自动归档」流程接管(publisher 子任务自动捕获 `/post/<id>` 正式 URL,回写 metadata.json + AGENTS.md 状态列标「全平台已发布」)。

---

## 八、与 CSDN 流水 audit 的协作关系

- 本文件是 CSDN 流水 audit `2026-07-02-csdn-33-34-publish-report.md` 的姊妹篇。
- 跨平台通用的发布纪律(门禁、临时文件清理决策、自迭代纪律)在 CSDN audit §一-§三 已统一,本文件不重复。
- 掘金特异性决策 / Skill 迭代建议在本文件 §四 单独沉淀;§五 增加跨平台对照,便于后续 publisher 跨平台感知差异。
- 后续审计 / 复盘若同时涉及 CSDN + 掘金,可创建 `2026-MM-DD-platform-comparison-report.md`(跨平台复盘)关联引用。

---

## 九、档案责任

- 本文件由 content-master 创建,记录一次掘金 publish 流水、立一份沉淀。
- 沉淀物若有更新(尤其 4.1、4.2 两项 P0/P1 Skill 迭代),由内容团队次轮 publish 时一并改 `.plugins/skills/juejin-publisher-v2/SKILL.md`。
- 临时文件清理决策若变更,以本文件第三段为准;CSDN 同步决策以 CSDN 流水 audit §三 为准。
