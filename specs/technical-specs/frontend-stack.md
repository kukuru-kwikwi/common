# Frontend Technical Specification

## Overview

This document outlines the technical architecture and key decisions for the MVP frontend of the Workshop app. The goal is to enable rapid prototyping and iteration, with a clear path to future scalability.

## Frontend Stack

- **Language:** TypeScript
- **Framework:** [React](https://react.dev/)
- **Builder/Bundler:** [Vite](https://vitejs.dev/)
- **Validation/Models:** [Zod](https://zod.dev/)
- **UI Library:** [Tabler](https://tabler.io/) (planned), [TanStack Table](https://tanstack.com/table/v8)
- **Router:** [TanStack Router](https://tanstack.com/router/v1)
- **Form/Validation:** [TanStack Form](https://tanstack.com/form/v1), [Zod](https://zod.dev/)
- **State Management:** React Context for MVP, consider Zustand or Redux for scale
- **Testing:** Vitest, React Testing Library
- **Linting/Formatting:** ESLint, Prettier
- **Types/Validation:** Zod schemas shared between backend and frontend (where possible)

## Key Components

### 1. App Structure

- Modular folder structure by feature or domain
- Use TanStack Router for navigation and route-based code splitting
- Shared components and utilities in a common folder

### 2. UI & Styling

- Use Tabler for base UI components (planned)
- Use TanStack Table for data tables
- Custom components as needed for app-specific UI

### 3. Forms & Validation

- Use TanStack Form for form state management
- Use Zod for schema validation and type inference
- Centralize form schemas for reuse and consistency

### 4. State Management

- Use React Context for global state in MVP
- Consider Zustand or Redux for more complex state as app grows

### 5. API Integration

- Use fetch or a lightweight HTTP client for API calls
- Centralize API logic in a service layer
- Handle errors and loading states consistently

### 6. Testing

- Use deno test for unit and integration tests
- Use React Testing Library for component tests
- Organize tests alongside components or in a dedicated **tests** folder

### 7. Linting & Formatting

- Use ESLint for code quality
- Use Prettier for consistent formatting
- Enforce standards with pre-commit hooks (optional)

## Future Considerations

- Add PWA support for offline access
- Add i18n for localization
- Integrate analytics and telemetry
- Add E2E testing with Playwright

---

This spec provides a foundation for building and iterating on the MVP frontend quickly, with clear upgrade paths as the project grows.
