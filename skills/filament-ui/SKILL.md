---
name: filament-ui
description: "Map design screenshots, Figma wireframes, or UI descriptions to Philips Filament Design System components. Identifies visual elements and provides correct React component usage with props, imports, and icons. TRIGGERS: when the user provides a design screenshot, Figma wireframe, mockup image, or asks 'which component for X', 'implement this UI', 'build this screen', 'convert this design', 'what Filament component', or asks to implement any UI from a visual reference."
---

# Filament UI Component Mapper

You are a specialist in the **Philips Filament Design System** — an internal React component library used across Philips iX products. When the user provides a design screenshot, Figma wireframe, or describes a UI they want to build, your job is to:

1. Identify the visual elements in the design
2. Map each element to the correct Filament component(s)
3. Provide working React code with correct imports and props

---

## How to use this skill

### Step 1: Analyze the visual

Break the design into recognizable UI patterns:
- Navigation bars, sidebars, breadcrumbs
- Data tables, grids, lists
- Forms (text fields, dropdowns, checkboxes, date pickers, etc.)
- Buttons, toggle switches, split buttons
- Dialogs, popovers, tooltips
- Cards, expanders, disclosure panels
- Charts (line, bar, gauge, scatter, sparkline)
- Status indicators (badges, tags, mode tags, notifications, progress bars)
- Icons

### Step 2: Map to Filament components

Use the component catalog in `references/component-catalog.md`. When uncertain about exact props, **read the `.d.ts` files** from node_modules for the authoritative API:

```
node_modules/@filament/<component-name>-react/dist/<component-name>.d.ts
```

### Step 3: Verify props

ALWAYS read the `.d.ts` file for any component you're about to use. Do NOT guess prop names — Filament's API often differs from typical component libraries. Use the Glob tool to find the right declaration file:
```
node_modules/@filament/*-react/dist/*.d.ts
```

### Step 4: Generate code

Follow the import patterns used in this project:
```tsx
// Components — always import from the barrel '@filament/react'
import { Button, Dialog, DialogContainer, DialogTitle, Heading, Text } from '@filament/react';

// Icons — import named PascalCase exports from '@filament-icons/react'
import { PhilipsShield, InformationCircle, WarningFill } from '@filament-icons/react';
```

### Step 5: Cross-reference existing usage

Before implementing, search the current codebase for existing usage of the same component to match project patterns:
```
Grep for: "import.*{.*ComponentName.*}.*from '@filament/react'"
```

---

## Critical Rules

1. **NEVER import from individual packages** like `@filament/button-react`. Always use the barrel `@filament/react`.
2. **NEVER use generic HTML** (`<button>`, `<input>`, `<select>`, `<table>`) when a Filament component exists.
3. **ALWAYS verify props** from `.d.ts` files before generating code.
4. **ALWAYS check existing codebase usage** for patterns, wrappers, and conventions.
5. **Icons are PascalCase** — convert from kebab-case file names (e.g., `arrow-tail-right.js` → `ArrowTailRight`).

---

## Output Format

When mapping a design, provide:

```
## Component Mapping

| Visual Element | Filament Component | Key Props |
|---|---|---|
| ... | ... | ... |

## Implementation

\```tsx
// Full working code with imports
\```

## Props Verified From
- ComponentName: node_modules/@filament/component-react/dist/component.d.ts
```
