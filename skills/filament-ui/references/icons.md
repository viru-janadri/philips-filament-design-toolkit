# Filament Icons Reference

Package: `@filament-icons/react`
Total icons: ~1066 (6396 files including variants and types)

## Naming Convention

- **File names**: kebab-case (e.g., `checkmark-circle-fill.js`)
- **Export names**: PascalCase (e.g., `CheckmarkCircleFill`)

## Icon Naming Patterns

| Concept | Icon name examples |
|---|---|
| States | `*-fill` (filled variant), `*-off` (disabled), `*-color` (brand colors) |
| Actions | `add-*`, `edit`, `cancel`, `checkmark`, `download`, `upload`, `refresh`, `search` |
| Arrows | `arrow-tail-*`, `arrow-rotate-*`, `arrow-trend-*`, `chevron-*` |
| Status | `warning`, `warning-fill`, `error`, `error-fill`, `information-circle`, `checkmark-circle` |
| Medical | `anatomical-*`, `ecg`, `stethoscope`, `syringe`, `patient-*`, `person-*` |
| Navigation | `hamburger-menu`, `chevron-*`, `home`, `settings`, `search` |
| Media | `media-play`, `media-pause`, `media-stop`, etc. (all have `-fill` variants) |
| Documents | `document-*`, `folder-*`, `report-*` |
| Communication | `envelope-*`, `balloon-speech-*`, `call`, `phone` |

## How to Find the Right Icon

1. Think of the concept in kebab-case
2. Use Glob to check: `node_modules/@filament-icons/react/dist/icons/<concept>*.js`
3. Convert to PascalCase for the import

## Usage in Components

```tsx
import { WarningFill, InformationCircle, Settings } from '@filament-icons/react';

// In a button
<Button variant="primary">
  <PhilipsShield /> Click me
</Button>

// Icon-only button
<Button isIconOnly aria-label="Settings">
  <Settings />
</Button>

// In notifications
<StaticNotification>
  <NotificationHeader>
    <WarningFill /> Warning title
  </NotificationHeader>
</StaticNotification>
```

## Common Icons Quick Reference

| Use Case | Import |
|---|---|
| Close/dismiss | `Cancel` |
| Confirm/success | `CheckmarkCircleFill` |
| Warning | `WarningFill` |
| Error | `ErrorFill` |
| Info | `InformationCircle` |
| Add/create | `AddCircle` or `Add` |
| Delete | `Delete` |
| Edit | `Edit` |
| Search | `Search` |
| Settings | `Settings` |
| Home | `Home` |
| User/person | `Person` |
| Menu | `HamburgerMenu` |
| More options | `MoreVertical` or `MoreHorizontal` |
| Expand | `ChevronDown` |
| Collapse | `ChevronUp` |
| Next | `ChevronRight` |
| Previous | `ChevronLeft` |
| Refresh | `Refresh` |
| Download | `Download` |
| Upload | `Upload` |
| Filter | `Filter` |
| Sort | `Sort` |
| Philips brand | `PhilipsShield` |
