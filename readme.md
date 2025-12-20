# Onboarding Checklist

Welcome to the common project starting point! Follow this checklist to get up and running quickly and ensure consistency across all derived projects.

# Start here

## 1. Initial Setup

- [ ] Review the [folder structure](/.github/copilot-instructions.md#folder-structure) and familiarize yourself with `/docs/`, `/refs/`, and `/specs/`.
- [ ] Read the `README.md` files in each major folder for context.
- [ ] Review the [tooling](/specs/technical-specs/tooling.md) for recommended tools and extensions.
- [ ] Install and configure required tools before starting work.

## 2. Project Kickoff

- [ ] Create your working directory for your project and init your git repository
- [ ] Copy the content of the `common` folder to your working directory
- [ ] Choose the right config for your project under `/refs/configuration/`

## 3. Specification Process

- [ ] Initialize `/docs/lexicon.md` for terminology and update as you go.
- [ ] Write your current (and future) ideas in `/docs/ideas.md` for potential improvements or inspiration. don't worry about structure so much.
- [ ] Use the templates in `/refs/` to create new epics, features, and data models.
  - Place new epics/features in `/specs/epics/` following the [naming conventions](/.github/copilot-instructions.md#folder-structure).
  - Write user stories from the user’s perspective, focusing on outcomes.
- [ ] Update `/specs/data-models/` for any new entities.

## 4. Prototyping

Steps for setting up the development environment and start prototyping

- [ ] When starting a new project, copy the relevant configuration templates from the `refs/configuration/{language}` folder:
  - `.editorconfig` for code style
  - `.prettierrc` for code formatting
  - `.env.example` for environment variables
- [ ] Review the technical stack in `/specs/technical-specs/` (frontend, backend, API).
- [ ] Follow the tech stack and standards in `/specs/technical-specs/`.

## 6. Changes instructions

- Propose changes via pull request or tracked document.
- Request peer review for any updates to instructions or templates.
- Summarize major changes in `CHANGELOG.md` (create if missing).

## 8. Questions & Support

- If unsure about any process, consult the instructions in `.github/` or ask a maintainer.
- Suggest improvements in `/docs/ideas.md`.

---

**Start here for every new project. Keep this checklist up to date as the common project evolves.**
