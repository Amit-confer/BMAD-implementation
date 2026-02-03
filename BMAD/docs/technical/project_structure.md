# Project Structure

**Repository Type:** Monorepo containing 5 distinct parts.

## Parts

### 1. Server
- **Path:** `server/`
- **Type:** Backend (NestJS)
- **Key Technologies:** NestJS 11, TypeORM, Postgres, BullMQ, Passport, Socket.io
- **Role:** Main API backend and orchestration layer.

### 2. Frontend
- **Path:** `frontend/`
- **Type:** Web (React)
- **Key Technologies:** React 18, Webpack 5, TanStack Table, CodeMirror, TailwindCSS, Bootstrap
- **Role:** Main user interface (App Builder).

### 3. CLI
- **Path:** `cli/`
- **Type:** CLI (Oclif)
- **Key Technologies:** Oclif, TypeScript
- **Role:** Command line interface for ToolJet management.

### 4. Plugins
- **Path:** `plugins/`
- **Type:** Extension (Plugin System)
- **Key Technologies:** TypeScript, Local Packages
- **Role:** Collection of integrations (Databases, APIs) for ToolJet.

### 5. Marketplace
- **Path:** `marketplace/`
- **Type:** Extension (Marketplace)
- **Key Technologies:** Lerna, AWS SDK
- **Role:** Plugin marketplace ecosystem.
