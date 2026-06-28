Create a hand-drawn educational architecture diagram showing the 3-layer universal agent base that emerged from real FDE delivery.

**TITLE at top:** "通用 agent 产品 · 3 层基座" in Chinese.

**MAIN LAYOUT — Three layers stacked vertically (like a layered cake cutaway), each layer with its purpose, key tech, and a small customer scenario icon:**

LAYER 1 (BOTTOM, warm brown #D4A574 base color):
- Title: "运行环境"
- Icon: [Docker container] + [code-server logo] + [OpenCode logo]
- Repository: "build-on-vscode-opencode-image"
- Key value: "客户机器装不上 → docker run 就跑"
- Bottom callout: "seed-if-absent：业务配置不被覆盖"

LAYER 2 (MIDDLE, sage green #85BAA1):
- Title: "资源调度"
- Icon: [K8s icon] + [subdomain icon] + [TTL clock icon]
- Repository: "agent-gateway"
- Key value: "一人一实例 + 自动回收 + 子域名隔离"
- Side callout: "Java + Spring Cloud Gateway + Redis"

LAYER 3 (TOP, soft blue #7BA7C9):
- Title: "交互定制"
- Icon: [VS Code icon] + [plugin icon] + [UI customizer icon]
- Repository: "a2ui-opencode"
- Key value: "客户工作流不同 → 插件层定制"
- Top callout: "OpenCode 提供 AI / VSCode 提供 UI / 客户填业务"

**RIGHT SIDE — A timeline arrow showing emergence order:**
- 客户 2 → Layer 1 (image)
- 客户 3 → Layer 1 + 2 (image + gateway)
- 客户 4 → Layer 1 + 2 + 3 (image + gateway + a2ui)

**BOTTOM ANCHOR:** "基座不是设计出来的，是被客户'砸'出来的" in a yellow sticky-note style box.

**STYLE:** Warm cream paper background (#F5F0E8), black hand-drawn sketch lines (2-3px, slightly irregular), soft pastel brand colors per layer. Each layer separated by a clear horizontal divider. Tech icons minimal and consistent. Minimal Chinese labels, simple line icons. NO dark backgrounds, NO 3D, NO realistic people. Subtle ArchAIHarness watermark bottom right. Landscape composition, 16:9 ratio.
