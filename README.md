# I Know Kung Fu 🥋

> *"I know kung fu." — Neo, The Matrix*

AI skills distilled from expert video content, installable in any AI coding agent via the [skills CLI](https://skills.sh).

## Install a skill

```bash
# Install a specific skill
npx skills add TDH-Labs/i-know-kung-fu@claude-cowork-workflows

# Browse all available skills
npx skills find --owner TDH-Labs
```

## Available Skills

| Skill | Description | Difficulty |
|-------|-------------|------------|
| [claude-cowork-workflows](./skills/claude-cowork-workflows/SKILL.md) | Best practices for co-working with Claude to accelerate programming and system design | Beginner |
| [improve-codebase-architecture](./skills/improve-codebase-architecture/SKILL.md) | Techniques for refactoring and improving large codebase architecture with AI | Intermediate |

## How it works

Each skill is a `SKILL.md` file with YAML frontmatter that describes:
- **name** – unique identifier
- **description** – what the skill does and when agents should activate it
- **tags** – searchable keywords

Skills are automatically discovered and activated by AI agents based on the description and the user's current task. Think of them as on-demand expert knowledge modules — the agent reads the relevant skill and gains that expertise for the task at hand.

## Supported Agents

These skills work with any agent that supports the [open agent skills ecosystem](https://skills.sh), including:

- Antigravity / AGY
- Claude Code / Cursor / Windsurf / Copilot
- Gemini CLI / OpenCode
- And [many more](https://skills.sh)

## Adding skills

Skills are generated automatically from curated expert video content using an AI pipeline. New skills are added regularly as more content is processed.

## License

MIT — use these skills freely in your own agents and projects.
