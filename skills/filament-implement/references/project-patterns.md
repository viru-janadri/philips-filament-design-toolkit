# Filament Project Patterns

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

## Common Patterns

### Dialog pattern
```tsx
import { Button, Dialog, DialogContainer, DialogTitle, DialogContent, DialogActions, Heading, Text } from '@filament/react';
import { InformationCircle } from '@filament-icons/react';
```

### DataGrid pattern
```tsx
import { DataGrid, DataGridHeader, Heading, Pagination, Table, TableHeader, TableBody, Column, Row, Cell } from '@filament/react';
```

### Notification pattern
```tsx
import { NotificationsQueue, Notification, NotificationHeader, NotificationContent } from '@filament/react';
import { CheckmarkCircleFill, WarningFill } from '@filament-icons/react';
```

## Recommended Component Folder Structure

```
src/components/
  ComponentName/
    ComponentName.tsx          # Main component
    ComponentName.test.tsx     # Tests
    ComponentName.module.css   # CSS modules (if needed)
    index.ts                   # Re-export
```

## Testing Patterns

- React Testing Library
- `@testing-library/user-event` for interactions
- Test Filament components by their accessible roles and labels
- Don't test internal Filament component state

## CSS Approach

- Filament provides its own styling — avoid overriding with custom CSS
- Use Filament's `FlexBox` for layout rather than custom flexbox CSS
- CSS Modules for any component-specific styles beyond what Filament provides
- Theme via `@filament/react/themes` (blue, light, medium are common defaults)

## Before Implementing

Always check the current project for:
1. Existing wrappers around Filament components (e.g., a preconfigured `ConfirmDialog`, `FormField` wrapper)
2. How the project already uses the component you're about to add (grep for existing imports)
3. Project-specific state management patterns (Redux, Context, Zustand, etc.)
4. The project's folder/naming conventions
