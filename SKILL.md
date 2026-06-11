---
name: filament-ds
description: "Philips Filament Design System plugin — maps designs to components, implements production React code, looks up props/icons, scaffolds new projects, auto-generates component catalogs, and reviews code for correct Filament usage. Contains skills: filament-ui, filament-implement, filament-lookup, filament-init, filament-catalog. Contains agent: filament-reviewer."
---

# Philips Filament Design System Plugin

This plugin provides comprehensive support for building UIs with the Philips Filament Design System (`@filament/react`).

## Available Skills

| Skill | Purpose | Trigger |
|---|---|---|
| `/filament-ui` | Map designs/screenshots to Filament components | Design image, "which component", "convert this design" |
| `/filament-implement` | Full production implementation with patterns | "implement", "build", "create this page" |
| `/filament-lookup` | Quick prop/icon/API lookup | "what props", "find icon", "how to use" |
| `/filament-init` | Scaffold Filament into a new/existing project | "set up filament", "init filament", "add filament" |
| `/filament-catalog` | Auto-generate component catalog from installed packages | "update catalog", "refresh components", "scan filament" |

## Available Agents

| Agent | Purpose |
|---|---|
| `filament-reviewer` | Reviews TSX code for Filament anti-patterns |

## Hook (automatic)

A **PostToolUse hook** runs after every Write/Edit to `.tsx`/`.jsx` files and checks:
1. Barrel imports from `@filament/react` (not individual packages)
2. PascalCase icon imports from `@filament-icons/react`
3. No generic HTML where Filament equivalents exist

## Core Rules (enforced across all skills)

1. **Always barrel import**: `import { X } from '@filament/react'`
2. **Never generic HTML**: Use `Button` not `<button>`, `TextField` not `<input>`
3. **Always verify props**: Read `.d.ts` files, never guess
4. **Match project patterns**: Search codebase before implementing
5. **PascalCase icons**: `WarningFill` not `warningFill`

## Package Location

```
node_modules/@filament/*-react/        — 72 component packages
node_modules/@filament-icons/react/    — 1066 icons
```
