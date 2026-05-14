---
name: design-review-sync
description: Audit design tokens vs design tool (Figma etc.): diff table only; no auto-write.
agents:
  - cursor
---

/caveman full

**Repo cockpit:** `.cursor/STRUCTURE.md` (Tailwind / CSS var source paths, design MCP policy) + `.cursor/CONTEXT.md`.

**Bind:** STRUCTURE for tailwind / CSS var source + design file access (MCP or export).

1. List design-tool variables (colours, spacing, radius).
2. List code theme keys (config paths in STRUCTURE).
3. Table: token | design | code | action (align / add / flag) — **complete** set for agreed scope (no silent omission; mark “out of scope” rows explicitly).
4. Tenant / brand variants — separate row group if STRUCTURE says multi-brand.

**Rule:** no repo or Figma writes unless user explicitly orders apply step.
