---
name: test-plan
description: Produce markdown manual QA plan: matrix, edge cases, sign-off slots.
agents:
  - cursor
---

/caveman full

**Repo cockpit:** `.cursor/STRUCTURE.md` (output path e.g. `docs/qa/`, environments, roles) + `.cursor/CONTEXT.md`.

**Bind:** STRUCTURE for output path (e.g. `docs/qa/`).

**Sections:** scope / out-of-scope; personas + roles; data matrix (empty, huge, unicode, slow network); ordered steps + expected; abuse (double submit, refresh, back); regression list; sign-off line — **complete** for the stated scope (no “…” placeholders).

**Rule:** each checklist row = observable outcome, not vague “works”.
