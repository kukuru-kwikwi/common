# Backend Technical Specification

## Overview

This document outlines the technical architecture and key decisions for the MVP backend of the Workshop app. The goal is to enable rapid prototyping and iteration, with a clear path to future scalability.

## Backend Stack

- **Runtime:** [Deno](https://deno.com/manual)
- **Framework:** [Hono](https://hono.dev/) (routing, middleware)
- **Validation/Models:** [Zod](https://zod.dev/)
- **Database:** [SQLite](https://www.sqlite.org/docs.html) (file-based, for MVP)
- **ORM/Query:** Direct SQL for MVP, consider Drizzle ORM or Kysely for future
- **Testing:** Deno built-in test runner
- **Logging:** Console for MVP, plan for OpenTelemetry
- **API Docs:** zod-to-openapi (planned)
- **Authentication:** API key/token for MVP, plan for OAuth or third-party
- **Error Handling:** Centralized middleware, standardized format
- **Environment Config:** Deno.env, .env files for secrets/config
- **Migrations:** SQL scripts, migration tool TBD
- **Types/Validation:** Zod schemas shared between backend and frontend (where possible)

## Key Components

### 1. API Structure

- see api [doc](api.md)

### 2. Data Models

- Define schemas with Zod for validation and type inference
- Map Zod schemas to SQLite tables
- Centralize model definitions for reuse in validation and API docs

### 3. Database

- Use SQLite for local development and MVP
- Simple migration scripts for schema changes
- Abstract DB access for future migration to Postgres or other RDBMS

### 4. Validation

- All incoming data validated with Zod
- Consistent error responses for validation failures

### 5. Error Handling

- Centralized error middleware in Hono
- Standardized error format (code, message, details)

### 6. Logging & Telemetry

- Console logging for MVP
- Add hooks for future integration with OpenTelemetry or external logging

### 7. Authentication (MVP)

- Start with simple API key or token-based auth
- Plan for future OAuth or third-party integration

## Future Considerations

- Swap SQLite for Postgres or SQL Server for production
- Add OpenAPI docs (can generate from Zod schemas)
- Integrate with frontend via REST or GraphQL
- Add real authentication/authorization
- Add structured logging and telemetry
