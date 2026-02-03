# Server Architecture

## Executive Summary
The Server part is a **NestJS** application facilitating the backend logic for ToolJet. It follows a modular architecture, leveraging **TypeORM** for data persistence and **BullMQ** for background job processing.

## Technology Stack

| Category | Technology | Version | Justification |
| :--- | :--- | :--- | :--- |
| Framework | NestJS | 11.x | Modular, scalable, TypeScript-first framework. |
| Language | TypeScript | 5.x | Type safety and modern JS features. |
| Database | PostgreSQL | - | Relational data integrity and complex querying. |
| ORM | TypeORM | 0.3.x | Object-Relational Mapping for DB interactions. |
| Queue | BullMQ | 5.x | Reliable background job processing (emails, etc.). |
| Auth | Passport / JWT | - | Standard authentication strategies. |

## Architecture Pattern
**Modular Monolith**: The application is structured into domain-specific modules (Apps, Auth, Organizations, etc.), each containing its own:
- **Controllers**: Handle HTTP requests.
- **Services**: Business logic.
- **Entities**: Database models.
- **DTOs**: Data Transfer Objects for validation.

## Key Modules

### `src/modules/`
- **Auth**: Authentication and session management.
- **Apps**: Application CRUD and logic.
- **Organizations**: Workspace management.
- **DataSources**: Connection to external databases/APIs.
- **Plugins**: Integration with the plugin system.

## Data Flow
1.  **Request**: Client (Frontend) sends HTTP request.
2.  **Guard**: Authentication/Authorization guards (JwtAuthGuard, ACL) verify access.
3.  **Controller**: Routes request to service.
4.  **Service**: Executes business logic, calls Repository.
5.  **Repository/TypeORM**: Queries PostgreSQL database.
6.  **Response**: Data returned to client.

## Background Jobs
BullMQ is used for async tasks like sending emails, processing long-running data queries, and plugin operations.

## Security
- **JWT**: Stateless authentication tokens.
- **Guards**: Role-Based Access Control (RBAC) via `FeatureAbilityGuard`.
- **Validation**: `class-validator` ensures payload integrity.
