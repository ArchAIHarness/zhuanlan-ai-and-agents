---
output: ../02-lease-ttl.png
aspect_ratio: "16:9"
type: framework
style_reference: ../../09_RAG的关键从来不是向量/01-retrieval-is-the-core.png
---

Match the visual style exactly: hand-drawn educational illustration, warm cream paper, solid black sketch lines, soft pastel color fill, handwritten Chinese labels, simple icons, no dark background, no 3D, no realistic people, subtle "ArchAIHarness" watermark.

CRITICAL — color fill every element.

Topic: TTL 租约模式——图书馆座位比方的调度设计。

Composition: A side-by-side analogy:
- LEFT half (the ANALOGY, green): a library STUDY ROOM with a desk and a chair. A person sits at the desk. On the desk a TIMER says "2 小时". A sign says "每 30 分钟扫码续约". If timer runs out: a hand sweeps the books away. Caption: "图书馆座位：到期释放，不是等人走".
- RIGHT half (the REAL design, orange): an Agent Pod labeled "AI 搭子实例" with a TTL counter "3600s". A heartbeat arrow "续约 5分钟/次" goes up to keep it alive. If TTL expires: a recycling symbol points to "删 Deployment / 清 Redis". Caption: "不等人，只认心跳".
- BOTTOM connecting bridge: "同一思想：有期租用，不信任常驻".

Top title: "TTL 租约模式：到期释放比等人走更可靠".

Spelling exact: "TTL 租约模式：到期释放比等人走更可靠" "图书馆座位：到期释放，不是等人走" "2 小时" "每 30 分钟扫码续约" "3600s" "续约 5分钟/次" "删 Deployment / 清 Redis" "不等人，只认心跳" "AI 搭子实例" "同一思想：有期租用，不信任常驻".

Key insight: TTL-based lease pattern — don't wait for users to leave, auto-reclaim when heartbeat stops.
