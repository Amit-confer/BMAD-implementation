# Server API Contracts

## Overview
The backend provides a REST API built with **NestJS**. Authentication is handled via JWT and Passport.

**Base URL:** `/api` (Configured in main.ts/Global Prefix)

## Authentication (`/api`)

| Method | Endpoint | Description | Auth Required |
| :--- | :--- | :--- | :--- |
| `POST` | `/authenticate` | Login with email/password | No |
| `POST` | `/authenticate/organization-login/{organizationId}` | Login to specific org | Yes |
| `GET` | `/authorize` | Authorize current session/user | Yes |
| `POST` | `/forgot-password` | Request password reset | No |

## Apps (`/api/apps`)

| Method | Endpoint | Description | Auth Required |
| :--- | :--- | :--- | :--- |
| `POST` | `/` | Create a new app | Yes (JwtAuth) |
| `GET` | `/` | List apps (with filtering) | Yes (JwtAuth) |
| `GET` | `/{id}` | Get app details | Yes (JwtAuth) |
| `PUT` | `/{id}` | Update app | Yes (JwtAuth) |
| `DELETE` | `/{id}` | Delete app | Yes (JwtAuth) |
| `GET` | `/slugs/{slug}` | Get app by slug | Public/Auth |

## Organizations (`/api/organizations`)

| Method | Endpoint | Description | Auth Required |
| :--- | :--- | :--- | :--- |
| `GET` | `/` | List user organizations | Yes |
| `PATCH` | `/` | Update org name/slug | Yes |
| `PATCH` | `/{id}/set-default` | Set default org for user | Yes |
| `GET` | `/is-unique` | Check name/slug uniqueness | Yes |

## Error Handling
Standard HTTP status codes are used.
- `401 Unauthorized`: Invalid/Missing Token
- `403 Forbidden`: Insufficient permissions (Guard failure)
- `404 Not Found`: Resource not found
- `400 Bad Request`: Validation failure (DTO)
