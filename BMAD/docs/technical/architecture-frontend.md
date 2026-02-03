# Frontend Architecture

## Executive Summary
The Frontend is a Single Page Application (SPA) built with **React**. It serves as the visual builder and runtime for ToolJet applications. It relies heavily on global state management to handle the complex interactions of an app builder.

## Technology Stack

| Category | Technology | Version | Justification |
| :--- | :--- | :--- | :--- |
| Framework | React | 18.x | Component-based UI library. |
| Build Tool | Webpack | 5.x | Asset bundling and transformation. |
| State Management | Zustand | 4.x | Lightweight, scalable global state management. |
| Styling | SCSS / Tailwind | - | Flexible styling options. |
| Drag & Drop | React DnD | - | Complex drag-and-drop interactions for builder. |

## Architecture Pattern
**Component-Based SPA**: The application is structured as a tree of components. State is managed globally via **Zustand** stores to avoid prop drilling, which is critical for the complex state of a visual builder.

## Key Directories

### `src/AppBuilder/`
Contains the core logic for the Application Builder interface.
- **Widgets/**: The library of drag-and-drop components available to users.
- **QueryManager/**: UI for managing data queries.
- **_stores/**: Zustand stores specific to the App Builder context.

### `src/_stores/`
Global state definitions.
- `appDataStore.js`: Manages the data of the app being built/viewed (components, queries, globals).
- `editorStore.js`: Manages the state of the editor UI (panels open/closed, selections).
- `userStore.js`: Current user session data.

## State Management Strategy
**Zustand** is used for global state. Stores are often split by domain (`appData`, `editor`, `user`).
- **Selectors**: Components select only the slice of state they need to minimize re-renders (using `shallow` comparison).
- **Actions**: State mutations are defined as actions within the store.

## Data Flow
1.  **User Action**: User interacts with UI (e.g., drags a widget).
2.  **Action Dispatch**: Component calls a store action (e.g., `updateComponents`).
3.  **State Update**: Store updates the state immutably.
4.  **Re-render**: Subscribed components re-render with new data.
5.  **Persistence**: `appDataStore` handles auto-saving changes to the backend via `appVersionService`.

## Performance
- **React.lazy**: Used for route-based code splitting.
- **Memoization**: `useMemo` and `useCallback` used extensively in the builder to prevent lag during drag operations.
