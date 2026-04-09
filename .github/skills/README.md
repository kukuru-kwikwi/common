# Skills Folder

This folder contains reusable skills—domain knowledge, best practices, and logic—that can be referenced by agents, workflows, or instructions.

## When to Create a Skill

- **Create a skill when:**
  - You have reusable logic, best practices, or domain knowledge that should be shared across agents, workflows, or instructions.
  - You want to standardize how a specific process or artifact (e.g., epic writing, prioritization) is performed.
  - The guidance is too detailed or specialized to fit in a workflow or instruction, but not broad enough to be an agent.
  - The knowledge is likely to be referenced in multiple places over time, even if currently used by a single workflow.

- **Do not create a skill when:**
  - The content is a one-off, highly specific rule or checklist that will never be reused elsewhere (put it in the workflow or documentation instead).
  - The content is a rule or formatting requirement for a specific file/folder (use an instruction).
  - You need automation, orchestration, or step-by-step guidance (create an agent or workflow).

> **Note:** Skills are appropriate for reusable domain knowledge and best practices, even if they are currently referenced by a single workflow. The guideline is to avoid cluttering the skills folder with one-off, non-reusable logic.

## How to Use

- Add new skills as **subfolders**, each containing a `SKILL.md` file using the provided [template](SKILL-template.md) for consistency.
- Reference skills in agents and workflows to enforce standards and share expertise.
- Update skills as best practices evolve.

## Skill File Structure

Each skill should follow the [SKILL-template.md](SKILL-template.md) structure.

## Guidelines

- Keep skills focused and reusable.
- Reference templates in `/refs/` rather than duplicating them.
- Use clear, actionable language.

## Best Practices

- Organize skills by topic in subfolders.
- Update skills as your team’s standards evolve.
- Cross-link related skills for discoverability.

## Do’s and Don’ts

- **Do:** Use skills for reusable logic and best practices.
- **Do:** Reference skills in agents, workflows, and instructions.
- **Don’t:** Duplicate templates or standards—link to `/refs/`.
- **Don’t:** Use skills for one-off rules or project-specific instructions.

## References

- [Official VS Code Copilot Agent & Skills Documentation](https://code.visualstudio.com/docs/copilot/customization/agent-skills)
