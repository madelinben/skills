---
name: code-review-server
description: Adversarial server-side review: security, data integrity, compat, perf.
agents:
  - cursor
---

/caveman full

**Repo cockpit:** `.cursor/STRUCTURE.md` + `.cursor/CONTEXT.md` + diff. **Gates** when you own the branch.

**Bind:** STRUCTURE + CONTEXT + diff.

- **Layers** — thin entry; business weight in **Manager** / service; persistence isolated per STRUCTURE; no “god controllers”.
- **Input** — all external sources validated; encoding / path traversal / upload limits per rules.
- **Authz** — every dangerous path gated.
- **Data store** — injection-safe APIs; iteration / N+1 / unbounded scans per STRUCTURE.
- **Errors / logs** — no secrets; user-safe messages per project error standard.
- **Compat** — old callers still safe.
- **Migrations** — breaking change discipline per STRUCTURE (backup tables, changelog, etc.).

**Output:** **exhaustive** `[SEV]` bullets — every issue with file:line when known. Optional **Prioritised quick wins**. Run STRUCTURE test command if possible. Remaining ambiguity → `/grill-me`.
