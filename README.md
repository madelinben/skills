# Eden Cursor skills

Agent skills. Each project still needs `.cursor/CONTEXT.md` and `.cursor/STRUCTURE.md` — skills read those for gates and conventions.

## Recommended (install first)

```bash
npx skills@latest add mattpocock/skills -a cursor --global
npx skills@latest add JuliusBrussee/caveman -a cursor --global
```

## Install Eden skills

```bash
npx skills@latest add madelinben/skills -a cursor --global --skill '*' -y
```

Or one skill by name:

```bash
npx skills@latest add madelinben/skills --skill implement -a cursor --global -y
```

**Always choose Global** when prompted for installation scope.

## Setup (Windows)

1. Open **Git Bash**
2. Run the commands above
3. Confirm skills exist under `C:\Users\<USERNAME>\.agents\skills\` (and/or `C:\Users\<USERNAME>\.cursor\skills\`)
4. **Restart Cursor** — `Ctrl+Shift+P` → **Developer: Reload Window**
5. **Cursor Settings** — `Ctrl+Shift+J` → **Rules and Skills**

**Not showing in Cursor?** Run the same `npx skills add` from **WSL** and check `~/.agents/skills/` and `~/.cursor/skills/` in your WSL home.

## Skills

| Skill | What it does |
|-------|----------------|
| **implement** | Start here: read STRUCTURE/CONTEXT, plan, delegate, run gates, hand off |
| **code-implement-client** | Build UI (Tailwind, atomic components, loading/error/empty states) |
| **code-implement-api** | Build HTTP API (thin handlers, transforms, authz, contracts) |
| **code-implement-server** | Build server code (Managers, validation, DB, compat) |
| **code-review-client** | Review UI changes |
| **code-review-api** | Review API changes |
| **code-review-server** | Review server changes |
| **design-review-ui-ux** | Review layout, tokens, empty vs error |
| **design-review-accessibility** | Review keyboard, semantics, contrast |
| **design-review-sync** | Compare code tokens vs Figma (report only) |
| **test-plan** | Write a manual QA checklist |
| **test-ui-ux** | Responsive / theme / overflow checks |
| **test-flow** | Run a plan in the browser (step-by-step) |
| **document-database** | ER diagram from code + approved DB commands |
| **document-flow** | Control-flow / sequence diagram from code |
| **document-current-state** | PM/sales “what we ship today” page |

## Links

- [skills CLI](https://github.com/vercel-labs/skills)
- [Cursor skills docs](https://cursor.com/docs/context/skills)
- [This repository](https://github.com/madelinben/skills)
