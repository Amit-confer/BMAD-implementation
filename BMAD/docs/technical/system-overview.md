# System Overview

![System Diagram](integration-architecture.md#system-diagram)

## Introduction
ToolJet is an open-source low-code framework to build and deploy internal tools with minimal engineering effort. This technical documentation covers the internal architecture of the ToolJet platform.

## Project Structure
The repository is a **monorepo** containing the following key components:

- **[Project Structure](project_structure.md)**: Detailed breakdown of the repository layout.

## Backend (Server)
The backend is a NestJS application providing the core API, data persistence, and business logic.
- **[Architecture](architecture-server.md)**: Modular Monolith design pattern.
- **[Data Models](data-models-server.md)**: Database schema (TypeORM entities).
- **[API Contracts](api-contracts-server.md)**: REST API endpoints.

## Frontend (Client)
The frontend is a React-based Single Page Application (SPA) that includes the visual App Builder.
- **[Architecture](architecture-frontend.md)**: Component-tree and State Management (Zustand).
- **[UI Component Inventory](ui-component-inventory-frontend.md)**: Reusable widgets and UI elements.

## CLI
The Command Line Interface helps manage ToolJet installations and the plugin ecosystem.
- **[Command Reference](cli-commands.md)**: Available Oclif commands.

## Architecture & Integration
How the pieces fit together.
- **[Integration Architecture](integration-architecture.md)**: Data flow, authentication, and plugin system details.
