# Filament Component Catalog

## Navigation & Layout

| Visual Pattern | Component | Key Props |
|---|---|---|
| Top navigation bar | `TopBar`, `TopBarTitle`, `TopBarMenu`, `TopBarUserInfo` | `background`, `hasBorder` |
| Side navigation | `Sidebar`, `SidebarHeader` | — |
| Breadcrumb trail | `Breadcrumbs`, `Breadcrumb` | — |
| Nav links | `NavLink` | — |
| Bottom action bar | `BottomBar` | — |
| Flex layout container | `FlexBox` | — |
| Content container with header | `ViewContainer`, `ViewContainerHeader`, `ViewContainerContent`, `ViewContainerActions` | — |
| Tabbed content | `Tabs`, `TabPanels` (with `Item` from common) | `iconPosition`, `orientation`, `alignment`, `isFullWidth`, `overflowBehavior` |
| Step wizard | `Wizard`, `WizardStep`, `WizardActions` | — |
| Stepper indicator | `Stepper` | — |

## Data Display

| Visual Pattern | Component | Key Props |
|---|---|---|
| Data table | `DataGrid`, `DataGridHeader`, `Table`, `TableHeader`, `TableBody`, `Column`, `Row`, `Cell` | — |
| Paginated table | Add `Pagination` | `PaginationLabelsProviderOptions` |
| Sortable columns | `Column` with sort definitions | — |
| List of items | `ListView`, `ListItem` | — |
| Selection list | `ListBox` with `Item` | — |
| Tree structure | `TreeView`, `TreeViewItem` | — |
| Card content block | `Card`, `CardHeader`, `CardBody`, `CardFooter`, `CardTitle`, `CardSubtitle` | — |
| Patient info display | `PatientInfo`, `PatientInfoHeader`, `PatientInfoGroup`, `PatientInfoItem`, `PatientInfoLine` | — |

## Forms & Input

| Visual Pattern | Component | Key Props |
|---|---|---|
| Text input | `TextField` | `label`, `placeholder`, `isRequired`, `isDisabled` |
| Password input | `Password` | — |
| Multi-line text | `TextArea` | — |
| Numeric input | `DigitTextField` | — |
| Dropdown select | `Dropdown` | — |
| Searchable select | `ComboBox` (use with `useFilter`) | — |
| Checkbox | `Checkbox`, `CheckboxGroup` | — |
| Radio buttons | `RadioButton`, `RadioGroup` | — |
| Toggle on/off | `ToggleSwitch` | — |
| Date picker | `DatePicker`, `DateRangePicker` | — |
| Time picker | `TimePicker`, `TimeRangePicker` | — |
| Calendar | `Calendar`, `RangeCalendar` | — |
| Color picker | `ColorPicker` | — |
| Slider | `Slider`, `RangeSlider` | — |
| File upload | `FileUploadArea`, `FileUploadButton` | — |
| Search box | `Search` | — |
| Tag input | `TagBox`, `TagBoxItem` | — |
| Rich text editor | `RichTextEditor` | — |
| Field error | `FieldError` | — |
| Input wrapper | `InputDecorator` | — |
| Label | `Label` | — |

## Buttons & Actions

| Visual Pattern | Component | Key Props |
|---|---|---|
| Standard button | `Button` | `variant` (`primary`, `secondary`), `signal` (`confirm`, `caution`, `warning`), `shape`, `isIconOnly`, `isFullWidth`, `iconPosition` |
| Button with dropdown | `SplitButton`, `MenuButton` | — |
| Toggle button | `ToggleButton`, `ToggleButtonGroup` | — |
| Link styled as text | `Link` | — |
| Toolbar of actions | `Toolbar`, `ToolbarGroup` | — |
| Menu | `Menu` (with `useMenuTrigger`) | — |

## Feedback & Status

| Visual Pattern | Component | Key Props |
|---|---|---|
| Toast / notification | `Notification`, `NotificationHeader`, `NotificationContent`, `NotificationActions`, `StaticNotification` | `NotificationVariant`, `SignalVariant` |
| Notifications queue | `NotificationsQueue`, `NotificationsList` | — |
| Progress bar | `ProgressBar` | — |
| Loading spinner | `Spinner` | — |
| Skeleton loader | `Skeleton` | — |
| Badge count | `Badge` | — |
| Tag / chip | `Tag` | — |
| Mode indicator | `ModeTag` | `ModeTagVariant`, `ModeTagSignal` |
| Tooltip | `Tooltip`, `TooltipAnchor` | — |
| Rating stars | `Rating` | — |

## Overlays & Dialogs

| Visual Pattern | Component | Key Props |
|---|---|---|
| Modal dialog | `Dialog`, `DialogContainer`, `DialogTitle`, `DialogContent`, `DialogActions` | `DialogSignal` |
| Popover | `Popover`, `PopoverBase` (with `useOverlayTrigger`) | — |
| Backdrop | `Backdrop` | — |
| Movie bar overlay | `MovieBar`, `MovieBarActions` | — |

## Expandable & Collapsible

| Visual Pattern | Component | Key Props |
|---|---|---|
| Accordion | `Expander`, `ExpanderGroup`, `ExpanderHeader`, `ExpanderContent` | — |
| Disclosure panel | `Disclosure`, `DisclosureGroup`, `DisclosureHeader`, `DisclosurePanel` | — |

## Charts & Visualization

| Visual Pattern | Component | Key Props |
|---|---|---|
| Line chart | `LineChart` | — |
| Bar chart | `BarChart` | — |
| Scatter plot | `ScatterPlot` | — |
| Gauge meter | `Gauge` | `GaugeVariant`, `GaugeSignal` |
| Sparkline | `Sparkline` | — |
| Hypnogram | `Hypnogram` | — |
| Pictorial / diagram | `Pictorial`, `Pictorials` | — |

## Typography

| Visual Pattern | Component | Key Props |
|---|---|---|
| Page heading | `Heading` (or `H1`–`H6`) | `variant` (`display-large` through `label`) |
| Body text | `Paragraph` | `variant` |
| Inline text | `Text` | `variant`, `color`, `weight` |

## Utility

| Visual Pattern | Component |
|---|---|
| Avatar / user image | `Avatar` |
| Page indicator / dots | `PageIndicator` |
| Gripper / drag handle | `Gripper` |
| Visually hidden text | `VisuallyHidden` |
| Portal (render to body) | `Portal`, `PortalOverlay` |
| I18n provider | `I18nProvider` |
| Router provider | `RouterProvider` |
