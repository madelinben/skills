---
name: implement
description: Orchestrate a change: bind repo STRUCTURE, grill-me, delegate stack skill, run STRUCTURE gates, QA handoff.
agents:
  - cursor
---

/caveman full

**Repo cockpit:** Read `.cursor/STRUCTURE.md` (dirs, patterns, **Gates**, rules load list) + `.cursor/CONTEXT.md` (domain terms, invariants). Greenfield repo → author those two first; skills stay portable; **STRUCTURE overrides** this file on conflict.

**Bind:** One primary repo root per run; load only `.cursor/rules/*.mdc` (or `.cursorrules`) paths STRUCTURE names. Multi-repo change → rerun skill per root.

**Plan:** ≤8 bullets (goal, files, edge cases, risks). No code until plan exists.

**Norms:** STRUCTURE + CONTEXT only; do not bulk-load whole AGENTS unless STRUCTURE points there.

**Ambiguity:** scope / authz / contract / UX unclear → `/grill-me` (one question at a time).

**Delegate:** open exactly one stack skill after STRUCTURE names stack:

| STRUCTURE says | Open skill (path under `.cursor/skills/`) |
|----------------|------------|
| UI framework (React/Vue/Svelte/RN…) | `code/code-implement-client` |
| Typed HTTP API service in this repo | `code/code-implement-api` |
| Server PHP / similar interpreted backend | `code/code-implement-server` |

**Execute:** smallest diff; match neighbour files STRUCTURE lists.

**Gates:** copy-run every command in STRUCTURE **Gates** until green. Fail → paste error + fix + retry.

**Loop:** diff vs STRUCTURE patterns; still fuzzy → `/grill-me` again.

**Handoff:** **exhaustive** — list everything material: shipped behaviour, files touched, how to verify (commands + manual checks), risks left open, follow-ups (tests, docs, migrations, contract regen if STRUCTURE says), owner questions. **No artificial bullet cap.** If anything still ambiguous for the next agent or reviewer → run `/grill-me` until closed or explicitly parked with ticket ref.

### Optional examples (non-normative)

Monorepo with nested `implement` skill: load that `SKILL.md` + **one** add-*.md it references — never load whole `references/` tree at once.

**Generic file tree (adapt paths to STRUCTURE):**

```text
.cursor/
  STRUCTURE.md    ← dirs, patterns, Gates, which rules to load
  CONTEXT.md      ← product language, invariants
  rules/*.mdc
src/ or app/      ← entrypoints per STRUCTURE
```
