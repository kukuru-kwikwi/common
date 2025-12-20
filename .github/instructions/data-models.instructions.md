---
applyTo: "**/specs/data-models/**"
---

# Data Model Documentation Guidelines

- Use markdown tables to define data models.
- Include the following columns in the table:
  - Field: The name of the field.
  - Type: The data type of the field (e.g., string, number, UUID, date, datetime, boolean, array).
  - Nullable: Indicate if the field can be null ("X" if it is, otherwise leave blank).
  - Default: The default value of the field (if any).
  - System : Indicate if the field is system-managed ("X" if it is, otherwise leave blank).
  - Relationships: Indicate foreign key relationships (e.g., FK to User, FK to Status Enum) and the plurality (one-to-one, one-to-many, many-to-many).
  - System notes: important notes about the field (e.g., whether it is system-managed, required, optional, foreign key references).
  - Notes : additional notes about the field.(e.g. purpose, usage)
  - ResourceKey : standardized resource key for the field (e.g., bike.id, user.uuid).
  - Format : (optional) specify format details for certain types (e.g., datetime format).
- Provide a brief description of the data model at the top of the file.
- Use integer identity columns (e.g., id as INT/AUTO_INCREMENT) for primary keys to optimize joins and indexing.
- Add a separate uuid field (type UUID) for global uniqueness and external references.
- Foreign keys should reference the integer identity column, not the UUID.
- Use UUIDs only where cross-system uniqueness is required (e.g., sharing, external APIs).
- Clearly indicate which fields are managed by the system and should not be set during creation.
- Use camelCase for field names.
- Primary keys should be named "id"
- Foreign keys should be named with the suffix "Id" (e.g., userId, statusId).

# Audit Fields

- Include standard audit fields at the end of the markdown table in each data model:
  - createdAt (datetime, system-managed)
  - updatedAt (datetime, system-managed)
  - deletedAt (datetime, system-managed)
  - createdBy (FK, system-managed)
  - updatedBy (FK, system-managed)
  - deletedBy (FK, system-managed)

# Indexing and Performance

- Identify fields that require indexing for performance optimization.
- Use Identity type IDs for user-specific unique identifiers for indexing and performance purposes.
