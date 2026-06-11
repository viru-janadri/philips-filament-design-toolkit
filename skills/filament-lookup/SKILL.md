---
name: filament-lookup
description: "Quick lookup for Filament component props, icon names, or API details. Reads .d.ts files and icon directories to give authoritative answers. TRIGGERS: 'what props does X have', 'find me an icon for', 'how do I use Filament X', 'Filament API for', 'what icons match'."
---

# Filament Quick Lookup

Fast, authoritative lookup for Filament component APIs and icons. Reads directly from the installed packages — no guessing.

## Component Props Lookup

When asked about a component's props:

1. Find the declaration file:
   ```
   node_modules/@filament/<kebab-case-name>-react/dist/<kebab-case-name>.d.ts
   ```
   
2. Read and summarize the exported props interface

3. Show usage example from the codebase if available

### Naming conventions for packages:
- `Button` → `@filament/button-react`
- `DataGrid` → `@filament/data-grid-react`
- `TextField` → `@filament/text-field-react`
- `ToggleSwitch` → `@filament/toggle-switch-react`
- `DatePicker` → `@filament/date-picker-react`
- `TopBar` → `@filament/top-bar-react`
- `ViewContainer` → `@filament/view-container-react`
- `RichTextEditor` → `@filament/rich-text-editor-react`
- `DigitTextField` → `@filament/digit-text-field-react`
- `ModeTag` → `@filament/mode-tag-react`
- `SplitButton` → `@filament/split-button-react`
- `ToggleButton` → `@filament/toggle-button-react`
- `MenuButton` → `@filament/menu-button-react`
- `FileUploadArea` / `FileUploadButton` → `@filament/file-upload-react`
- `ProgressBar` → `@filament/progress-bar-react`
- `ColorPicker` → `@filament/color-picker-react`
- `ComboBox` → `@filament/combo-box-react`
- `RadioButton` → `@filament/radio-button-react`
- `PatientInfo` → `@filament/patient-info-react`
- `MovieBar` → `@filament/movie-bar-react`
- `PageIndicator` → `@filament/page-indicator-react`
- `NavLink` → `@filament/nav-link-react`
- `InputDecorator` → `@filament/input-decorator-react`
- `ListView` → `@filament/list-view-react`
- `ListBox` → `@filament/list-box-react`
- `TreeView` → `@filament/tree-view-react`
- `BottomBar` → `@filament/bottom-bar-react`

General rule: PascalCase component → kebab-case package name with `-react` suffix.

## Icon Lookup

When asked to find an icon:

1. Glob for candidates:
   ```
   node_modules/@filament-icons/react/dist/icons/<search-term>*.js
   ```

2. Return matches as PascalCase imports

3. Note `-fill` variants when available

## Hook Lookup

Common Filament hooks (from `@filament/react` or individual packages):
- `useFilter` — for ComboBox filtering
- `useMenuTrigger` — for Menu trigger management  
- `useOverlayTrigger` — for Popover/Dialog triggers
- `useAsyncList` — for async data loading in lists/tables

Read hook signatures from:
```
node_modules/@filament/common-react/dist/*.d.ts
```

## Output Format

```
## [ComponentName] Props

| Prop | Type | Default | Description |
|---|---|---|---|
| ... | ... | ... | ... |

Source: node_modules/@filament/[package]/dist/[file].d.ts
```
