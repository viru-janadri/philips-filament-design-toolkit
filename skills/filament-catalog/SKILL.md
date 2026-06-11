---
name: filament-catalog
description: "Auto-generate the Filament component catalog by scanning node_modules/@filament/*-react/ packages. Produces an up-to-date component-catalog.md from the actually installed packages. TRIGGERS: 'update filament catalog', 'regenerate catalog', 'refresh component list', 'scan filament components', 'what filament components are available'."
---

# Filament Catalog Generator

You generate an up-to-date component catalog by scanning the installed `@filament/*-react` packages in the current project's `node_modules`. This ensures the catalog matches the actual Filament version installed — no stale data.

## Workflow

### Step 1: Discover installed packages

Glob for all Filament component packages:
```
node_modules/@filament/*-react/
```

List all directories found. Each directory name follows the pattern `<component-name>-react`.

### Step 2: Extract exports from each package

For each package, read the main `.d.ts` file:
```
node_modules/@filament/<name>-react/dist/<name>.d.ts
```

If that doesn't exist, try:
```
node_modules/@filament/<name>-react/dist/index.d.ts
```

Extract all exported component names (look for `export declare` or `export { ... }`).

### Step 3: Categorize components

Group discovered components into these categories:
- **Navigation & Layout**: TopBar, Sidebar, Breadcrumbs, FlexBox, ViewContainer, Tabs, Wizard, etc.
- **Data Display**: DataGrid, Table, ListView, TreeView, Card, PatientInfo, etc.
- **Forms & Input**: TextField, Dropdown, ComboBox, Checkbox, DatePicker, Slider, etc.
- **Buttons & Actions**: Button, SplitButton, ToggleButton, Menu, Toolbar, etc.
- **Feedback & Status**: Notification, ProgressBar, Spinner, Badge, ModeTag, Tooltip, etc.
- **Overlays & Dialogs**: Dialog, Popover, Backdrop, etc.
- **Expandable**: Expander, Disclosure, etc.
- **Charts**: LineChart, BarChart, Gauge, Sparkline, etc.
- **Typography**: Heading, Paragraph, Text, etc.
- **Utility**: Avatar, Portal, I18nProvider, RouterProvider, etc.

Use the component name and package name to infer category. When ambiguous, check the `.d.ts` for prop types (e.g., `onPress` → Button, `columns` → DataGrid-related).

### Step 4: Count icons

```
Glob: node_modules/@filament-icons/react/dist/icons/*.js
```

Count total icons and report.

### Step 5: Detect Filament version

Read `node_modules/@filament/react/package.json` for the installed version.

### Step 6: Generate catalog

Output a markdown table grouped by category:

```markdown
# Filament Component Catalog (auto-generated)

**Version**: @filament/react X.Y.Z
**Packages**: N component packages
**Icons**: M icons available

## Navigation & Layout

| Package | Exported Components |
|---|---|
| @filament/top-bar-react | TopBar, TopBarTitle, TopBarMenu, TopBarUserInfo |
| ... | ... |

## Data Display
...
```

### Step 7: Write to references

Write the output to the project's local reference or display it to the user:
- If running inside a project with the filament-ds plugin, update `skills/filament-ui/references/component-catalog.md`
- If running in a user's project, display the catalog and offer to save it locally

### Step 8: Report differences

If an existing `component-catalog.md` exists, diff against it and report:
- New components added (not in old catalog)
- Components removed (in old catalog but no longer installed)
- Potential version upgrades

## Output format

```
## Catalog Regenerated

- Filament version: 3.20.2
- Packages scanned: 72
- Components found: 248
- Icons available: 1066
- New since last scan: DataGridV2, RangeSlider
- Removed since last scan: (none)

Catalog written to: skills/filament-ui/references/component-catalog.md
```
