# Project-Specific Filament Patterns

## NPM Registry

Filament packages are hosted on Philips HSDP Artifactory. Required `.npmrc` scopes:

```ini
@filament:registry=https://artifactory.hsdp.io/artifactory/api/npm/filament-npm/
@filament-icons:registry=https://artifactory.hsdp.io/artifactory/api/npm/filament-npm/
@filament-react:registry=https://artifactory.hsdp.io/artifactory/api/npm/filament-npm/
@filament-theme:registry=https://artifactory.hsdp.io/artifactory/api/npm/filament-npm/
always-auth=true
```

Auth token (local dev only, never commit): `//artifactory.hsdp.io/artifactory/api/npm/filament-npm/:_authToken=${HSDP_TOKEN}`

## ix-sdc-simulator patterns

Based on how this codebase uses Filament:

### Dialog pattern
```tsx
// See src/components/AboutDialog/AboutDialog.tsx
import { Button, Dialog, DialogContainer, DialogTitle, Heading, Paragraph, Text, Link } from '@filament/react';
import { PhilipsShield, InformationCircle } from '@filament-icons/react';
```

### DataGrid pattern
```tsx
// See src/components/Logs/LogsDashboard.tsx
import { DataGrid, DataGridHeader, Heading, Pagination, Table, TableHeader, TableBody, Column, Row, Cell } from '@filament/react';
```

### Component folder structure
```
src/components/
  ComponentName/
    ComponentName.tsx          # Main component
    ComponentName.test.tsx     # Tests
    ComponentName.module.css   # CSS modules (if needed)
    index.ts                   # Re-export
```

### State management
- Local state with `useState` / `useReducer` for component-level state
- React Context for cross-component state (e.g., simulator configuration)
- No external state library

### Testing patterns
- React Testing Library
- `@testing-library/user-event` for interactions
- Test Filament components by their accessible roles and labels
- Don't test internal Filament component state

### CSS approach
- CSS Modules for component-specific styles
- Filament provides its own styling — avoid overriding with custom CSS
- Use Filament's `FlexBox` for layout rather than custom flexbox CSS
- Theme comes from Filament's `@filament/themes`

### Common wrappers
Check if the project has common wrappers around Filament components (e.g., a preconfigured `ConfirmDialog`, `FormField` wrapper, etc.) before creating new ones.
