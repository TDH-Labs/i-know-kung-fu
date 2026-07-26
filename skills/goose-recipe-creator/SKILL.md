---
name: goose-recipe-creator
description: Create, validate, and install Goose recipes — reusable YAML workflows (instructions, parameters, extensions) run via `goose run --recipe` or a deeplink. Use when the user wants to author a new recipe, turn a repeated prompt/workflow/SOP into a recipe, or fix an existing recipe file.
---

# Goose Recipe Creator

A Goose **recipe** is a YAML file that packages a workflow: system `instructions`, an optional initial `prompt`, `parameters`, and `extensions`. Users run recipes from Goose Desktop or CLI (`goose run --recipe <name>`) and share them via deeplinks.

## Where recipes live

- Personal: `~/.config/goose/recipes/<kebab-case-name>.yaml`
- Project-scoped: `.goose/recipes/` in the project root
- `goose recipe list` shows what Goose sees — use it to confirm a recipe landed.

## Workflow

1. **Gather requirements.** Pin down: the goal ("done" state), inputs/triggers, tools or extensions needed, constraints ("never X", "always Y first"), and any loops (define the termination condition). Given an SOP or rough prompt, extract these before writing YAML.

2. **Draft from the template.** Copy `assets/recipe-template.yaml`. Required fields: `version`, `title`, `description`, `instructions`. Everything else is optional — full field reference: `references/recipe-schema.md`.

3. **Write good instructions.** Instructions are the system prompt for the run:
   - Numbered phases/steps, one action per step.
   - Name tools explicitly ("use the `shell` tool to run …") and give exact commands where determinism matters.
   - State guardrails as imperatives ("STOP if …", "Never …").
   - Reference parameters with `{{ parameter_key }}` placeholders.
   - If a step needs a skill, say so ("load the X skill first").
   - Keep recipes single-purpose; split big SOPs into multiple recipes.

4. **Validate — always.**
   ```bash
   goose recipe validate <file>.yaml
   ```
   Fix and re-run until it passes. Never install an unvalidated recipe.

5. **Install.** Copy the validated file to `~/.config/goose/recipes/` (or `.goose/recipes/` for project scope). Confirm with `goose recipe list`.

6. **Smoke-test (preferred).** `goose run --recipe <name> --params key=value` for a non-destructive pass, or `goose recipe deeplink <file>` for a share link.

## Rules

- Secrets never go in the YAML — use extension `envs` referencing the environment, or tell the user what must be set.
- Filename kebab-case; `title` human-readable; `description` one sentence covering what + when.
- On a Harbor-managed machine: if the recipe needs a skill or MCP server that isn't installed, flag the gap — don't silently assume it exists.
