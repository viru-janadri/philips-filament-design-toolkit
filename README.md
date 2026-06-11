# philips-filament-design-toolkit

Claude Code plugin for the **Philips Filament Design System** (`@filament/react`).

Provides component mapping, implementation guidance, icon lookup, prop discovery, and automated code review for React apps using Filament.

## Installation

```bash
claude plugin add viru-janadri/philips-filament-design-toolkit
```

## Skills

| Skill | Purpose | Trigger |
|---|---|---|
| `/filament-ui` | Map designs/screenshots to Filament components | Design image, "which component for X" |
| `/filament-implement` | Full production implementation with patterns | "implement", "build", "create this page" |
| `/filament-lookup` | Quick prop/icon/API lookup | "what props does X have", "find icon for" |
| `/filament-init` | Scaffold Filament into a new/existing project | "set up filament", "init filament" |
| `/filament-catalog` | Auto-generate component catalog from installed packages | "update catalog", "scan filament components" |

## Agent

| Agent | Purpose |
|---|---|
| `filament-reviewer` | Reviews TSX code for Filament anti-patterns |

## Automatic Hook

A **PostToolUse hook** runs after every Write/Edit to `.tsx`/`.jsx` files and checks:
1. Barrel imports from `@filament/react` (not individual packages)
2. PascalCase icon imports from `@filament-icons/react`
3. No generic HTML where Filament equivalents exist

## Core Rules

1. **Always barrel import**: `import { X } from '@filament/react'`
2. **Never generic HTML**: Use `Button` not `<button>`, `TextField` not `<input>`
3. **Always verify props**: Read `.d.ts` files from node_modules, never guess
4. **Match project patterns**: Search codebase before implementing
5. **PascalCase icons**: `WarningFill` not `warningFill`

## Filament Packages

```
node_modules/@filament/*-react/        — 72 component packages
node_modules/@filament-icons/react/    — 1066 icons
```

## NPM Registry Setup

Filament packages are hosted on the Philips HSDP Artifactory. Add this `.npmrc` to your project root:

```ini
@filament:registry=https://artifactory.hsdp.io/artifactory/api/npm/filament-npm/
@filament-icons:registry=https://artifactory.hsdp.io/artifactory/api/npm/filament-npm/
@filament-react:registry=https://artifactory.hsdp.io/artifactory/api/npm/filament-npm/
@filament-theme:registry=https://artifactory.hsdp.io/artifactory/api/npm/filament-npm/
always-auth=true
```

For local development, add your auth token (do not commit):
```ini
//artifactory.hsdp.io/artifactory/api/npm/filament-npm/:_authToken=${HSDP_TOKEN}
```

## License

Proprietary - Philips internal use only.
