---
name: code-implement-api
description: "Implement or extend typed HTTP API in this repo: validation, authz, stable contracts."
agents:
  - cursor
---

/caveman full

**Repo cockpit:** `.cursor/STRUCTURE.md` + `.cursor/CONTEXT.md` + API rules files STRUCTURE lists (often `.cursor/rules/*.mdc`). Greenfield API repo → document in STRUCTURE: framework (e.g. Fastify), `src/` layout, Zod/OpenAPI conventions, **transform** folder naming, and **Gates**; CONTEXT holds tenant/auth language.

**Bind:** follow STRUCTURE for route registration, schema types, service folders, and error DTO helpers.

- **Boundary** — validate request/response at edge (schema types STRUCTURE names: Zod, io-ts, OpenAPI codegen, etc.).
- **Authz** — tenant / user / role checks on every mutating path; deny-path tests if STRUCTURE requires.
- **Handler** — thin: parse → service → **response transform**; no business SQL in handler unless STRUCTURE already allows.
- **Transforms** — map domain / DB shapes → wire DTOs in dedicated `*Transform` / `*Mapper` modules (STRUCTURE path); **handlers import transforms**, not inline 40-field spreads.
- **Discriminated unions / results** — `switch` on tagged kinds; **extendable case lists**: add new variant → compiler forces new branch (exhaustiveness helper STRUCTURE exports, e.g. `assertNever`); map domain `Result` / `Either` to HTTP status in one place per project pattern.
- **Errors** — stable client-facing shape per project rules; no raw stack traces.
- **Contracts** — backward compatible by default (additive fields, versioning policy in STRUCTURE).

**Gates:** STRUCTURE **Gates** (+ tests line if present).

### Default layout (generic tree — adapt to STRUCTURE)

```text
src/
  routes/ or modules/<domain>/
    <resource>.ts        ← register route; schema refs only
  services/              ← business rules, Prisma/HTTP
  transforms/            ← entity → response DTO (pure functions)
  schemas/               ← Zod / input-output types shared with handlers
```

### Handler / transform shape (block-comment convention)

```text
/*
 * POST /things — HTTP edge only.
 * Flow: parseBody(ThingCreateSchema) → thingService.create(dto) → mapThingToResponse(result)
 * Errors: neverthrow / project helper → status + stable JSON body (STRUCTURE).
 */
/*
 * mapThingToResponse(domain: Thing) : ThingWire
 * Pure: no IO; add fields only in backward-compatible ways.
 */
```

### Optional examples (non-normative)

Codegen / contract regen commands live in **STRUCTURE** + `package.json` — never guess script names from another repo.
