---
name: code-review-client
description: "Adversarial UI review: patterns, edge cases, a11y, perf, smallest diff."
agents:
  - cursor
---

/caveman full

**Repo cockpit:** `.cursor/STRUCTURE.md` + `.cursor/CONTEXT.md` + diff. Same **Gates** as implement when you own the branch.

**Bind:** STRUCTURE + CONTEXT + diff.

- **Placement** — right layer/dir per STRUCTURE; no feature leakage into shared primitives.
- **Atomic / return shape** — one component per file where project standard says so; single main `return` unless STRUCTURE allows guard-only early returns; no god-components.
- **Style** — Tailwind-only surface; flag stray CSS modules / inline styles unless STRUCTURE-approved exception.
- **Validation** — single source; no duplicate client paths.
- **State / UX** — error vs empty distinct; nested ternaries → extract.
- **A11y** — STRUCTURE doc paths (keyboard, labels, contrast).
- **Perf** — rerenders, keys, bundle hotspots if STRUCTURE cares (e.g. storefront).
- **i18n** — no hardcoded user strings if project uses catalogue.

**Output:** **exhaustive** `[SEV] file — issue — fix` list for every finding (no arbitrary cap). Optional subsection: **Prioritised quick wins** (ordered subset) for same-day fixes. If scope / severity still unclear → `/grill-me`. Run STRUCTURE **Gates** if you own branch.
