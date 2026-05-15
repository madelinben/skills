---
name: design-review-accessibility
description: "A11y review: keyboard, semantics, contrast, tooling when available."
agents:
  - cursor
---

/caveman full

**Repo cockpit:** `.cursor/STRUCTURE.md` (WCAG target, doc paths, Gates) + `.cursor/CONTEXT.md`.

**Bind:** STRUCTURE lists WCAG target + paths to project a11y docs (if any).

- **Keyboard** — full flow; visible focus; modal focus trap only in real modals.
- **Semantics** — real controls (`button`, `a href`); heading order; labels tied to inputs.
- **Media** — meaningful `alt`; decorative empty alt.
- **Contrast** — meet STRUCTURE target (often AA minimum).
- **Tools** — Lighthouse/axe in browser MCP if STRUCTURE allows automated pass.

**Output:** **exhaustive** issue — criterion — concrete fix per finding. Optional severity ordering.
