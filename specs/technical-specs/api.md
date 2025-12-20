# API Technical Specification

## API Design Guidelines

### 1. URL Structure

- RESTful endpoints for core resources (bikes, users, assignments, etc.)
- Organized by resource (e.g., `/api/users`, `/api/employees`)
- Use plural nouns for resource names (e.g., `/bikes`, `/users`).
- Use kebab-case for multi-word resource names (e.g., `/proof-of-purchase`).
- Nest resources to express relationships (e.g., `/bikes/{bikeId}/pictures`).
- Prefix all endpoints with `/api/v1/` for versioning.

### 2. HTTP Methods

- `GET`: Retrieve resources or resource collections.
- `POST`: Create new resources.
- `PUT`: Replace an existing resource.
- `PATCH`: Partially update an existing resource.
- `DELETE`: Remove a resource.

### 3. Request & Response Format

- Use JSON for all request and response bodies.
- Standardize response envelopes:
  - Success: `{ "data": <payload>, "message": "<optional message>" }`
  - Error: `{ "error": { "code": <status>, "message": "<error message>" } }`
- Use appropriate HTTP status codes (e.g., 200, 201, 400, 401, 404, 500).

### 4. Authentication & Authorization

#### Supported Authentication Methods

- **Microsoft Account (OAuth/OpenID Connect)**: Users can authenticate using their Microsoft account. After successful authentication, the backend issues a signed JWT for API access.
- **Email/Password Credentials**: Users can register and log in with an email and password. Upon successful login, the backend issues a signed JWT for API access.

#### JWT Usage

- All authenticated API requests must include the JWT in the `Authorization: Bearer <token>` header.
- JWTs should encode user ID, roles, and other relevant claims.
- Tokens must be signed and have an expiration time.

#### Authentication Flows

**Microsoft Account Login:**

1. User is redirected to Microsoft login and grants permissions.
2. Microsoft returns an authorization code to the backend.
3. Backend exchanges the code for user info, creates/updates the user, and issues a JWT.
4. Client stores the JWT and uses it for subsequent API requests.

**Email/Password Login:**

1. User submits email and password to the backend.
2. Backend verifies credentials.
3. On success, backend issues a JWT.
4. Client stores the JWT and uses it for subsequent API requests.

#### Token Refresh & Expiry

- JWTs should have a reasonable expiration (e.g., 1 hour).
- Support refresh tokens or re-authentication as needed.

#### Authorization

- Protect sensitive endpoints by requiring a valid JWT.
- Use claims in the JWT to enforce role-based access control (RBAC) where needed.

### 5. Pagination, Filtering, and Sorting

- Support pagination via `?page=` and `?limit=` query parameters.
- Support filtering and sorting via query parameters (e.g., `?status=active`, `?sort=name`).

### 6. Error Handling

- Return meaningful error messages and codes.
- Use consistent error response structure as above.

### 7. Naming Conventions

- Use camelCase for JSON keys.
- Use lowercase and hyphens for URL paths.

### 8. Versioning

- All endpoints must be versioned using the URL prefix (e.g., `/api/v1/`).

---

Additions and changes to these guidelines should be discussed and agreed upon by the team.

## API Stack

- **Runtime:** [Deno](https://deno.com/manual)
- **Framework:** [Hono](https://hono.dev/) (routing, middleware)
- **API Contract:** [OpenAPI](https://www.openapis.org/) (specification compliance is required)
- **API Documentation Generation:** [zod-to-openapi](https://github.com/asteasolutions/zod-to-openapi) (OpenAPI schemas are generated from Zod models)
- **Authentication & Authorization:**
  - [OAuth](https://oauth.net/) (with third-party provider, e.g., Microsoft, Google) for user authentication
  - Backend exchanges OAuth code/token for user info and issues a [JWT](https://jwt.io/) to the client
  - Client uses JWT in `Authorization: Bearer <token>` header for all API requests
  - JWT encodes user ID, roles, and claims for stateless, role-based access control
- **Error Handling:**
  - Centralized error-handling middleware catches and processes all errors in one place
  - All error responses use a standardized JSON structure, e.g.:
    ```json
    {
      "error": {
        "code": 400,
        "message": "Validation failed",
        "details": { "field": "email", "issue": "required" }
      }
    }
    ```
  - This approach ensures consistency, simplifies maintenance, and improves client integration
- **Request/Response Validation:**
  - All incoming requests and outgoing responses are validated using [Zod](https://zod.dev/)
  - Zod schemas ensure type safety, data integrity, and power OpenAPI documentation generation
- **Versioning Strategy:**
  - All endpoints are versioned using a URL prefix (e.g., `/api/v1/`)
  - This approach ensures version visibility, clarity, and easy client integration
- **Testing:**
  - Use Deno's built-in test runner ([docs](https://deno.com/manual@v1.41.0/testing))
- **Environment/Configuration Management:**
  - Use environment variables for configuration (e.g., secrets, API keys, DB connection strings)
  - Supports `.env` files for local development and Deno.env for runtime access
- **Logging & Telemetry:**
  - Support [OpenTelemetry](https://opentelemetry.io/) out of the box for distributed tracing, metrics, and logs
  - Error logging can use [logtape](https://github.com/denosaurs/logtape) (Deno) or [Serilog](https://serilog.net/) (if integrating with .NET services)
  - Error logs and traces are compatible with OTLP (OpenTelemetry Protocol) for export to observability platforms
