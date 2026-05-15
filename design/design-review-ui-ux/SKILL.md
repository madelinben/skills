---
name: design-review-ui-ux
description: "UI/UX pass: hierarchy, spacing scale, tokens, empty vs error, density per product type."
agents:
  - cursor
---

/caveman full

**Repo cockpit:** `.cursor/STRUCTURE.md` (tokens, spacing rhythm, product posture) + `.cursor/CONTEXT.md` (personas, tone). Greenfield → define token source + posture there first.

**Bind:** STRUCTURE for design tokens, spacing rhythm, tenant theming, product posture (consumer vs admin).

- **Scale** — use project spacing scale only (STRUCTURE names step, e.g. 2/4/8).
- **Colour** — semantic tokens; light/dark if product supports.
- **Empty vs error** — never same silent blank.
- **Copy** — specific CTAs; avoid “Submit” / “More” alone when better label exists.
- **Density** — match product (STRUCTURE: marketing vs sovereign admin).

**Output:** **exhaustive** area — issue — fix (token/class pattern) for each problem spotted. Optional ranked “ship blockers vs nice-to-haves”.
