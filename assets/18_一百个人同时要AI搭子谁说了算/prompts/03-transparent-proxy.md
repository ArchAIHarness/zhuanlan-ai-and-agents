---
output: ../03-transparent-proxy.png
aspect_ratio: "16:9"
type: framework
style_reference: ../../09_RAG的关键从来不是向量/01-retrieval-is-the-core.png
---

Match the visual style exactly: hand-drawn educational illustration, warm cream paper, solid black sketch lines, soft pastel color fill, handwritten Chinese labels, simple icons, no dark background, no 3D, no realistic people, subtle "ArchAIHarness" watermark.

CRITICAL — color fill every element.

Topic: /agent/* 透明代理——送到门口，不翻包。

Composition: A clear FLOW from left to right.
- LEFT: a user (simple person icon) with a request arrow labeled "/agent/session?directory=/project → x-user-id".
- CENTER: the "大脑" (brain icon) that does THREE things in sequence:
  1. "查 Redis 找 userId 对应的实例"
  2. "去掉 /agent 前缀"
  3. "透传路径/参数/方法/请求体"
  Then an arrow passes through with a RED line crossing out "Authorization" with "清掉：防止越权" label.
- RIGHT: an Agent Pod labeled "AI 搭子实例" receiving the cleaned request "/session?directory=/project". Caption: "送到门口，不翻包".
- BELOW: WebSocket flow shown as a secondary path "/agent/ws/* → 字节级透明转发" with "不解析、不缓冲、不改内容".

Top title: "透明代理：送到门口，不翻包".

Spelling exact: "透明代理：送到门口，不翻包" "/agent/session?directory=/project → x-user-id" "查 Redis 找 userId 对应的实例" "去掉 /agent 前缀" "透传路径/参数/方法/请求体" "清掉：防止越权" "Authorization" "/agent/ws/* → 字节级透明转发" "不解析、不缓冲、不改内容" "AI 搭子实例".

Key insight: transparent proxy — deliver to the door, don't rummage through the luggage.
