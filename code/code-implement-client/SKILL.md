---
name: code-implement-client
description: "Implement or extend UI layer: components, state, styling per repo STRUCTURE."
agents:
  - cursor
---

/caveman full

**Repo cockpit:** `.cursor/STRUCTURE.md` + `.cursor/CONTEXT.md` first — framework, dirs, tokens, form libs, **Gates**, and rules load list live there only. Greenfield UI repo → copy this skill + add those two files naming your stack; STRUCTURE wins on conflict.

**Bind:** follow STRUCTURE paths for imports, generated client, and token sources.

- **Atomic file** — one file ≈ one component ≈ one user-visible concern; keep tree shallow; extract subviews only when reused or STRUCTURE already splits.
- **Single return** — prefer one `return (` … `);` at the bottom of the component function; hoist `const` data / handlers / small derived values above it; avoid multiple scattered returns unless early guard returns for auth / missing props (STRUCTURE may show local pattern).
- **Split** — container vs presentational; “presenter” split only if STRUCTURE / neighbours already use it.
- **States** — loading / error / empty / success explicit; no silent blank.
- **Style** — **Tailwind utility classNames only** in markup; **no** separate CSS modules / `.css` files for feature UI unless STRUCTURE explicitly allows a rare exception (e.g. third-party embed); no inline `style={}` except truly dynamic values STRUCTURE permits.
- **JS surface** — minimise client JS: prefer declarative props, composition, and framework-native patterns; new `useEffect` / `useMemo` / `useCallback` only with a one-line reason in code or STRUCTURE-mandated hook.
- **Validation** — single source (STRUCTURE: e.g. schema owns cross-field); no duplicate ad-hoc + schema drift.
- **Unions** — exhaustive `switch` + exhaustiveness helper if STRUCTURE exports one.

**Gates:** STRUCTURE **Gates**.

### Default layout (generic tree — rename to match STRUCTURE)

```text
src/
  components/          ← shared primitives only
  features/<Name>/     ← routes, forms, one-off views
    components/
    schemas.ts         ← feature-owned validation (example)
```

### Method / file shape (block-comment convention — paste above export)

```text
/*
 * <ComponentName> — <one line: what the user sees / does>.
 * Data: props | hooks named in STRUCTURE (no deep prop drilling if STRUCTURE forbids).
 * States: loading | error | empty | success — each branch returns explicit UI.
 * Style: Tailwind classes only; token classes from STRUCTURE config.
 */
```

### Optional examples (non-normative)

Sibling repo may host extra playbooks under its `.cursor/skills/` — only if your workspace layout includes that path.
