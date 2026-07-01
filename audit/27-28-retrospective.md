# 复盘 · 27/28 篇全链路交付（2026-07-01）

> 跨"调研 → 撰稿 → 审核 → 插画 → 发布 → 验收"全链路的真实事故记录。
> 这一篇给将来的自己看——别再在同一类坑里摔两次。

## 一、最终交付状态

| 项 | 状态 | 关键 ID / 证据 |
|---|---|---|
| 27 篇 CSDN 草稿 | ✅ 已保存 | articleId `162467502` |
| 28 篇 CSDN 草稿 | ✅ 已保存 | articleId `162467734`（封面 `93b4ebbd40244a39903d9bf5276b2834.png`、摘要 142 字、标签 AI编程） |
| 27 篇 掘金 草稿 | ✅ 已保存 | draftId `7657104125783539722`（4 张图，位置/alt 全部正确，无需修改） |
| 28 篇 掘金 草稿 | ✅ 已保存 | draftId `7656730922040410122`（清掉末尾 6 张重复图，12→6） |
| Git 推送 | ✅ commit `bcaa517` 已推到 main | `ArchAIHarness/zhuanlan-ai-and-agents` |
| AGENTS §5.2 新规 | ✅ 奇+偶一期节奏规则落地 | 奇数理论篇有预告、双数实践篇无预告 |

## 二、出过的事（按发生顺序）

### 事故 1：图片 Markdown 语法被连续 sed 改成 `![alt(url)`（最严重）
- **现象**：28 篇正文里 6 张图全是 `![alt(url)` 缺 `]` 的坏语法，平台不渲染。
- **根因**：上一轮我用 sed 替换 `(assets/` → `<assets/` 时把 `(` 换没了，然后用第二个 sed 把 `>` 换回 `)` 时漏补 `]`。两次操作各删一个字符，留下永久坏语法。
- **修复**：用 `sed -i '' 's|跑](assets/|…|'` 一次性把 6 处补上 `]`。
- **教训**：
  - **不要用 sed 反复编辑同类字符**，第二次 sed 的 diff 必然丢失上一次替换的状态。
  - 每次编辑后**立即用 `od -c` 或 `xxd` 二进制验证文件字符**，不靠"grep -n 能匹配"就认为正确。
  - 平台渲染时坏语法会**沉默失败**（不报错、只显示原文），人工截图才看出问题——必须用户视角验收。

### 事故 2：28 篇掘金草稿 12 张图（6 正 + 6 末重复）
- **现象**：正文 6 个正确位置插了正确的 6 张图，但文末 export 段后又追加了 6 张用 `01-loose-vs-track.png` 这种文件名 alt 的图。
- **根因**：发布专员并行跑两个草稿时，27 篇的图素材被错塞进了 28 篇草稿的末尾。
- **修复**：用 CodeMirror `replaceRange('', {line:430,ch:0}, {line:441,ch:0})` 一次删除末尾 11 行（6 张图 + 5 个空行）。
- **教训**：
  - **发布专员串行**，不要并行——同一份图片素材在两个草稿间会串。
  - **必须用真实编辑器文本（`cm.CodeMirror.getValue()`）核对**，不能信预览 DOM——预览有时只渲染前 N 张图。
  - 用 `replaceRange` 删行比 sed 安全（位置由 CodeMirror API 算，不靠 grep 估算行号）。

### 事故 3：CSDN 28 篇标签错误（"gateway" 替代了正确标签）
- **现象**：发布专员报告"标签：人工智能/语言模型/AI编程"，实际页面只显示 `人工智能/gateway`。
- **根因**：subagent 报告与真实状态不一致——CSDN 标签区有"用户偏好"和"AI 推荐"两套，"gateway"是某个被误点的 AI 推荐项，没被报告捕获。
- **修复**：先 `closeBtn.click()` 删除 gateway，重新打开 `mark_selection_box` 标签 popover，点选 `AI编程`。
- **教训**：
  - **永远不要信 subagent 的报告**——只信从浏览器实时 evaluate 抓出来的 DOM 状态。
  - CSDN 的发布设置 modal 在 `body > div.modal__publish-article`，单独 selector 就能定位，不要全文搜 "modal"。
  - 标签修改要先关掉错的、刷新弹层，再选新的——直接在错的状态上叠加会留下脏数据。

### 事故 4：网络中断导致 CSDN 草稿保存失败
- **现象**：点击"保存为草稿"无 toast、无 modal 关闭，console 报 `ERR_INTERNET_DISCONNECTED`。
- **根因**：用户网络瞬断（与本次操作无关）。
- **修复**：等 `navigator.onLine === true` 后用 `force: true` 的 click 重试，第二次成功显示 "文章已保存 09:47:36"。
- **教训**：
  - **保存按钮必须等待 toast 反馈**才能认为成功，仅 modal 关闭不算。
  - 网络异常时用 `navigator.onLine` 探测比 `await page.waitForTimeout` 靠谱。

### 事故 5：发布专员并行导致图片素材串了
- **根因**：上一轮我同时派发了 27 篇 CSDN + 27 篇 掘金 + 28 篇 CSDN + 28 篇 掘金 4 个 subagent，并发跑导致图片素材共享状态错乱。
- **教训**：
  - **发布任务必须串行**——一个草稿跑完、验收完，再开下一个。
  - 即使时间紧迫，**也不能用并发换速度**——并发必然引入状态污染，最后的修复成本远超节省的时间。

## 三、流程纪律的沉淀（写到 AGENTS）

以下规则值得升级到 `.plugins/skills/csdn-publisher-v2/SKILL.md` 和 `juejin-publisher-v2/SKILL.md`：

### CSDN
1. **发布设置 modal** 必须从 `body > div.modal__publish-article` 单独定位；不要全文搜。
2. **封面图**通过 `button.upload-img-box` 触发文件选择，**文件选定后必须等 `vicp-wrap` 激活**才能点 `vicp-operate-btn` 确认——跳过确认等于没上传。
3. **标签修改**先 `closeBtn.click()` 关错的、刷新 popover、再选新的；不要在脏状态上叠加。
4. **保存草稿**必须等 toast（"文章已保存 HH:MM:SS"）才认为成功；仅 modal 关闭不算。

### 掘金
1. **图片状态验证**用 `cm.CodeMirror.getValue()`（真实编辑器文本），不信预览 DOM。
2. **末尾重复图**用 `replaceRange('', {line:startLine,ch:0}, {line:endLine,ch:0})` 一次删干净。
3. **自动保存**触发后无需手动 Ctrl+S——编辑动作本身就是保存信号。

### 通用
1. **发布任务必须串行**，不并发——并发必串素材。
2. **验收只看 DOM 真实状态**，不信 subagent 报告。
3. **网络异常**用 `navigator.onLine` 探测 + `force: true` 重试。
4. **每次图片语法编辑后**用 `od -c` 二进制校验字符完整性。

## 四、本次没有做但应该做的

- [ ] 把 5 条新规则正式合并进 `csdn-publisher-v2` 和 `juejin-publisher-v2` 的 SKILL.md
- [ ] 给 27/28 篇建独立的渠道包（`.csdn-publish/27_…/metadata.json` 和 `.juejin-publish/27_…/metadata.json`），记录 articleId/draftId/CDN URL，方便后续发布追踪
- [ ] 28 篇文件名仍然过长（包含 "AI不是AI写代码-是AI在秩序内写代码-…"），如果用户后续要求改名，需要同步改正文、assets 目录、所有引用（README/AGENTS/illustration-briefs/audit/research），**单点改名=多源失败**

## 五、最硬的一条总结

> **发布任务要串行、不并发；验收只看 DOM、不信报告；图片语法编辑后必须二进制校验；保存必须等 toast。**
> 这四条做到了，发布链路就不出事。

---

**总结日**：2026-07-01
**执行人**：内容创作主编
**commit**：`bcaa517`