# Frontend Component Inventory

## Overview
The frontend is built with React and uses a component-based architecture. Components are organized by feature (within `AppBuilder` or `Editor`) and generic reusable UI elements.

## AppBuilder Components
Located in `src/AppBuilder/`.

### Core Layout
- **AppBuilder**: Main container (`AppBuilder.jsx`). Handles layout and providers.
- **LeftSidebar**: Navigation and tool selection.
- **RightSideBar**: Property inspector and configuration.
- **Header**: Application header and actions.
- **AppCanvas**: The main drag-and-drop area for building apps.

### Widgets (`src/AppBuilder/Widgets`)
These are the building blocks available to users in the App Builder.
- **Base**: `Text`, `Button`, `Image`, `Container`
- **Forms**: `TextInput`, `NumberInput`, `Checkbox`, `RadioButton`, `Datepicker`, `PasswordInput`
- **Data**: `Table`, `Listview`, `Chart`, `Statistics`, `Kanban`
- **Media**: `Video`, `Audio`, `PDF`
- **Advanced**: `CodeEditor`, `Map`, `IFrame`, `RichTextEditor`

## Shared UI (`src/_ui`)
Reusable low-level components used across the application to maintain design consistency.
- **TJLoader**: Loading spinner.
- **ErrorBoundary**: Error catching wrapper.
- **Modal**: Dialog components.
- **Button**: Standard button styles.

## Third-Party Libraries
- **Drag & Drop**: `react-dnd`
- **Code Editor**: `codemirror`
- **Charts**: `plotly.js`
- **Icons**: `tabler-icons`
