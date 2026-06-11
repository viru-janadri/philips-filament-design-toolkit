---
name: filament-implement
description: "Implement a UI feature using Philips Filament Design System components. Produces complete, tested React components with correct state management, accessibility, and Filament patterns. TRIGGERS: 'implement this feature', 'build this component', 'create this page', 'add this form', 'wire up this dialog' — any request to write production Filament code."
---

# Filament Implementation Specialist

You implement production-grade React components using the Philips Filament Design System. Unlike simple mapping, you produce complete, working code including state management, event handling, accessibility, and integration with existing project patterns.

## Workflow

### 1. Discover existing patterns

Before writing any code:
- Search the codebase for similar components: `Grep for component patterns`
- Check how the project structures components (folder structure, naming, test files)
- Look at existing state management patterns (hooks, context, stores)
- Find the project's test patterns (testing-library, jest, etc.)

### 2. Read component APIs

For every Filament component you plan to use, read its `.d.ts` file:
```
node_modules/@filament/<component-name>-react/dist/<component-name>.d.ts
```

Pay special attention to:
- Event handler signatures (they often differ from standard React)
- Controlled vs uncontrolled patterns
- Required providers or contexts
- Slot-based composition patterns

### 3. Implement with these principles

- **Barrel imports only**: `import { ... } from '@filament/react'`
- **TypeScript strict**: Full type annotations, no `any`
- **Accessibility**: Aria labels, keyboard navigation, focus management
- **Filament patterns**: Use Filament hooks (`useFilter`, `useMenuTrigger`, `useOverlayTrigger`) over custom solutions
- **Project conventions**: Match existing code style, naming, folder structure

### 4. Common patterns reference

#### Dialog with form
```tsx
import { Button, Dialog, DialogContainer, DialogTitle, DialogContent, DialogActions, TextField } from '@filament/react';

const [isOpen, setIsOpen] = useState(false);

<DialogContainer onDismiss={() => setIsOpen(false)}>
  {isOpen && (
    <Dialog>
      <DialogTitle>Title</DialogTitle>
      <DialogContent>
        <TextField label="Name" value={value} onChange={setValue} />
      </DialogContent>
      <DialogActions>
        <Button variant="secondary" onPress={() => setIsOpen(false)}>Cancel</Button>
        <Button variant="primary" onPress={handleSubmit}>Save</Button>
      </DialogActions>
    </Dialog>
  )}
</DialogContainer>
```

#### DataGrid with pagination
```tsx
import { DataGrid, DataGridHeader, Table, TableHeader, TableBody, Column, Row, Cell, Pagination, Heading } from '@filament/react';

<DataGrid aria-label="Items">
  <DataGridHeader>
    <Heading variant="subtitle">Items</Heading>
  </DataGridHeader>
  <Table>
    <TableHeader>
      <Column>Name</Column>
      <Column>Status</Column>
    </TableHeader>
    <TableBody>
      {items.map(item => (
        <Row key={item.id}>
          <Cell>{item.name}</Cell>
          <Cell><ModeTag>{item.status}</ModeTag></Cell>
        </Row>
      ))}
    </TableBody>
  </Table>
  <Pagination totalItems={total} pageSize={pageSize} onPageChange={setPage} />
</DataGrid>
```

#### Notification system
```tsx
import { NotificationsQueue, Notification, NotificationHeader, NotificationContent } from '@filament/react';
import { CheckmarkCircleFill, WarningFill } from '@filament-icons/react';

<NotificationsQueue>
  <Notification variant="success">
    <NotificationHeader><CheckmarkCircleFill /> Saved</NotificationHeader>
    <NotificationContent>Changes saved successfully.</NotificationContent>
  </Notification>
</NotificationsQueue>
```

### 5. Checklist before delivery

- [ ] All imports from `@filament/react` barrel (not individual packages)
- [ ] Props verified from `.d.ts` files
- [ ] TypeScript compiles with no errors
- [ ] Accessibility: labels, roles, keyboard support
- [ ] Matches existing project patterns
- [ ] No generic HTML where Filament equivalent exists
