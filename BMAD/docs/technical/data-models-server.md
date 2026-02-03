# Server Data Models

## Overview

The server uses **TypeORM** with a **PostgreSQL** database. The data model is centered around `Users`, `Organizations` (Workspaces), and `Apps`.

## Core Entities

### User (`users`)
Represents a platform user. Users can belong to multiple organizations.

- **id**: UUID (PK)
- **email**: String
- **first_name**: String
- **last_name**: String
- **password_digest**: String (Bcrypt hash)
- **source**: Enum (signup, invite, google, git, ldap, saml, etc.)
- **status**: Enum (invited, verified, active, archived)
- **organization_id**: UUID (FK -> Default Organization)

**Relationships:**
- One-to-Many `OrganizationUser` (Memberships)
- One-to-Many `App` (Created apps)
- One-to-Many `GroupPermissions` (RBAC)

### Organization (`organizations`)
Represents a workspace or tenant.

- **id**: UUID (PK)
- **name**: String (Unique)
- **slug**: String (Unique)
- **domain**: String
- **status**: Enum (active, archived)
- **inherit_sso**: Boolean

**Relationships:**
- One-to-Many `OrganizationUser`
- One-to-Many `App`
- One-to-Many `SSOConfigs`

### App (`apps`)
Represents a ToolJet application built by a user.

- **id**: UUID (PK)
- **name**: String
- **slug**: String (Unique)
- **organization_id**: UUID (FK -> Organization)
- **user_id**: UUID (FK -> Creator)
- **type**: Enum (front-end, etc.)
- **is_public**: Boolean

**Relationships:**
- Many-to-One `Organization`
- Many-to-One `User`
- One-to-Many `AppVersion`
- One-to-One `AppGitSync`

## Schema Migrations

Migrations are managed via TypeORM CLI.
- Location: `server/src/migration-helpers/`
- Command: `npm run db:migrate`
