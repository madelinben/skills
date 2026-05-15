---
name: code-implement-server
description: "Implement or extend server-side code (PHP, etc.): layers, validation, DB, compat."
agents:
  - cursor
---

/caveman full

**Repo cockpit:** `.cursor/STRUCTURE.md` + `.cursor/CONTEXT.md` + `.cursorrules` / `.cursor/rules/*.mdc` only what STRUCTURE names. Greenfield server repo → define Manager/factory/store naming and **Gates** in STRUCTURE; this skill stays portable.

**Bind:** follow STRUCTURE for layer names (often **Manager** = orchestration + transactions; **Factory** = construction / wiring; **Repository** / gateway = persistence or remote API).

- **Shape** — thin entry (route / controller / script) → **Manager** (or domain service) coordinating use-cases → **Factory** / builder when object graphs are non-trivial → persistence or HTTP client abstraction the project uses; **no** fat controllers.
- **Managers** — own transaction boundaries, orchestration, and “application service” rules; keep **thin**: delegate repeated SQL / HTTP to dedicated store/client modules STRUCTURE names.
- **Input** — validate all external input at the edge; typed value objects if STRUCTURE mandates; never pass raw superglobals deep.
- **Authz** — server-side only; never trust UI visibility.
- **SQL / store** — parameterised APIs project uses; iteration + transaction rules per STRUCTURE / rules.
- **Compat** — additive behaviour; deprecation path in STRUCTURE.
- **Secrets** — never logs / responses.

**Gates:** STRUCTURE **Gates** (often PHPUnit / phpstan — copy verbatim).

### Default layout (generic tree — adapt to STRUCTURE)

```text
httpdocs/ or src/
  Controllers/ or Routes/     ← HTTP or CLI edge: parse, respond, no business rules
  Managers/                   ← use-cases, transactions, orchestration
  Factories/                  ← object construction, wiring
  Repositories/ or Data/      ← SQL / driver calls only here unless STRUCTURE says otherwise
```

### Class / method shape (block-comment convention)

```text
/*
 * <ThingManager>
 * Responsibility: one cohesive use-case area (STRUCTURE lists examples).
 * Depends: factories + repositories injected or constructed per project DI style.
 * Public methods: verb phrases; each method = one transaction or clearly documented sub-call.
 * Does not: emit HTML for non-template stacks; log secrets; read superglobals.
 */
```

### Optional examples (non-normative)

Legacy PHP monoliths: project-specific error DTO, logging helper, DB result iteration — always follow **that repo’s** `.cursor/rules` + STRUCTURE pointers, not generic memory.
