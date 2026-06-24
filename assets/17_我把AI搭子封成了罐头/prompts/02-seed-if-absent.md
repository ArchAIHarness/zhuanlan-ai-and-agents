---
output: ../02-seed-if-absent.png
aspect_ratio: "16:9"
type: framework
style_reference: ../../09_RAG的关键从来不是向量/01-retrieval-is-the-core.png
---

Match the visual style exactly: hand-drawn educational illustration, warm cream paper, solid black sketch lines, soft pastel orange/green/blue color fill, handwritten Chinese labels, simple icons, no dark background, no 3D, no realistic people, subtle "ArchAIHarness" watermark.

CRITICAL — color fill every element.

Topic: seed-if-absent 模式——文件存在就不覆盖，不存在才兜底注入默认。

Composition: A flowchart with TWO branches from a "检查文件是否存在?" diamond:
- BRANCH A (right, "文件存在" → green check mark → "保持不动，尊重业务配置" → a hand holding back the template).
- BRANCH B (down, "文件不存在" → orange arrow → "从模板复制注入默认" → a template file flowing into the empty slot). 
- BELOW, THREE small concrete example rows, each being an if-absent file + a check mark:
  1. "settings.json → 不存在 → 注入精简布局模板"
  2. "tasks.json → 不存在 → 注入 folderOpen 自动任务"
  3. "AGENTS.md → 不存在 → 注入默认项目规矩"
- CAPTION: "每一行都一样：你管我不管，你不管我兜底".

Top title: "seed-if-absent：默认兜底 + 用户优先".

Spelling exact: "seed-if-absent：默认兜底 + 用户优先" "检查文件是否存在?" "文件存在" "保持不动，尊重业务配置" "文件不存在" "从模板复制注入默认" "settings.json → 不存在 → 注入精简布局模板" "tasks.json → 不存在 → 注入 folderOpen 自动任务" "AGENTS.md → 不存在 → 注入默认项目规矩" "每一行都一样：你管我不管，你不管我兜底".

Key insight: seed-if-absent is the universal pattern for "default but don't override".
