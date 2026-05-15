---
name: test-flow
description: "Run manual plan in browser: hypothesis row per step, then reality vs expected."
agents:
  - cursor
---

/caveman full

**Repo cockpit:** `.cursor/STRUCTURE.md` (base URL patterns, browser policy) + `.cursor/CONTEXT.md`.

**Bind:** `test/test-plan` skill output or user steps + base URL from STRUCTURE / user.

1. Write **expected** UI state per step before click.
2. Browser MCP: navigate → snapshot → act → snapshot (follow MCP server lock/snapshot rules).
3. Table: step | action | expected | actual | severity | follow-up — **one row per planned step** plus abuse rows below.
4. Abuse cases after happy path (STRUCTURE may list minimum count; default: cover double submit, refresh, back).

**Blockers** (login, captcha) — record blocker; stop; no fake creds.

No browser → give same table with empty “actual” for human fill.
