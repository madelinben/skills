---
name: code-review-api
description: "Adversarial HTTP API review: authz, schemas, versioning, errors."
agents:
  - cursor
---

/caveman full

**Repo cockpit:** `.cursor/STRUCTURE.md` + `.cursor/CONTEXT.md` + diff (+ OpenAPI diff if repo tracks it). **Gates** when you own the branch.

**Bind:** STRUCTURE + diff (+ OpenAPI diff if repo tracks it).

- **Schema** — request/response matches storage + clients; optional fields backward compatible.
- **Handler thinness** — parse → service → **transform**; flag fat handlers or SQL in route file unless STRUCTURE allows.
- **Transforms** — response mapping lives in dedicated modules; no duplicate field mapping across handlers.
- **Tagged unions / results** — new enum/variant covered in `switch` + exhaustiveness; error → status mapping consistent.
- **Authz** — deny cases tested.
- **Tenant / scope** — no cross-tenant leaks (if multi-tenant).
- **Versioning** — breaking changes behind version / deprecation policy in STRUCTURE.
- **Errors** — mapped statuses; no stack to client.
- **Result types** — all branches handled if STRUCTURE uses `Result`/either pattern.

**Output:** **exhaustive** `[SEV]` bullets + test ideas for worst-case payloads (no arbitrary cap). Optional **Prioritised quick wins**. Ambiguity → `/grill-me`.
