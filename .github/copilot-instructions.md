---
applyTo: "**"
---

# General guidelines

- Read the latest version of the files included in the context before generating code or answering questions.

## Markdown Guidelines

- Use headings to organize content.
- Use `-` bullet points for lists.
- Uppercase the first letter of each bullet point.
- Include links to related resources.
- Use code blocks for code snippets.
- When using quotes, use double quotes (" ") instead of single quotes (' ') or (“ ”).
- Use backticks (`) for inline code references and paths.
- Use bold (\*\* \*\*) for emphasis on lexicon or important terms.

## Folder and File Naming Conventions

- Use `kebab-case` for file and folder names.

# Methodology

We use a hierarchical approach inspired by Agile and Azure DevOps:

### Epics

- **Purpose:** Define major functional areas of the app (the big picture).
- **Detail:** High-level description of what the area covers and why it matters.

### Features

- **Purpose:** Describe distinct capabilities within each epic.
- **Detail:** Include context, goals, user types, scenarios, requirements, data, UI, edge cases, and dependencies. Explain what the feature is, who it is for, and how it should behave.

### User Stories

- **Purpose:** Capture specific user needs or actions in a testable format.
- **Detail:** Written from the user’s perspective, focusing on desired outcomes. Each story answers: "As a [user type], I want to [do something] so that [goal]."

## Folder Structure

- `/docs/`: Project-level documentation for onboarding, usage, high-level architecture, and glossary.
- `/docs/ideas.md`: Contains ideas and future improvements for the project.
  - Use this file to capture potential future improvement ideas without cluttering current specifications.
- `/docs/lexicon.md`: Contains the lexicon of terms used in the specifications.
  - Use this file to ensure terminological consistency across specifications.
- `/refs/`: Master templates, reusable standards, and technical reference materials for use across projects.
  - Use this folder to store materials that can be referenced or copied for new projects to maintain consistency.
- `/specs/`: All technical specifications, requirements, data models, epics, features, user stories, and project-specific tech specs.
- `/specs/data-models/`: Contains all data model definitions used throughout the project.
  - Data-models should be user readable and explain what the entity does and how it is structured.
- `/specs/epics/`: Contains folders for each epic in the project.
- `/specs/epics/1-{epic-name}/`: Each epic has its own folder (e.g., `1-configuration/`, `2-paie/`).
  - `0-{epic-name}.md`: The high-level specification of the epic
  - `1-{feature}.md`: The high-level specification of a feature.
    - Each feature has its own markdown file.
    - User stories are detailed in the feature markdown files.
- `/specs/technical-specs/`: Contains all project-specific technical specifications (e.g., API, integrations, frontend-stack, backend-stack, etc.).
- `/specs/technical-specs/general.md`: Contains global project standards and guidelines (validation, localization, error handling, etc.).
  - Avoid duplicating content between `general.md` and epic/feature specifications.
