# Goose Recipe Schema Reference

Full field reference for recipe YAML. `goose recipe validate <file>` is the authority — if this file and the validator disagree, the validator wins.

## Minimal recipe

```yaml
version: 1.0.0
title: My Recipe
description: One sentence — what it does and when to use it.
instructions: |
  Step 1. …
  Step 2. …
```

## Top-level fields

| Field | Required | Purpose |
|---|---|---|
| `version` | yes | Recipe format version — use `1.0.0` |
| `title` | yes | Display name |
| `description` | yes | Shown in the recipe picker; say what + when |
| `instructions` | yes¹ | System prompt for the run (multi-line YAML block) |
| `prompt` | no | Initial user message sent when the recipe starts |
| `parameters` | no | Typed inputs the user provides at launch |
| `extensions` | no | MCP servers/tools to enable for the run |
| `settings` | no | `goose_provider`, `goose_model`, `temperature` |
| `activities` | no | Status strings shown in the Desktop UI while running |
| `response` | no | `json_schema` forcing structured output |
| `retry` | no | Validation-check + retry loop config |
| `author` | no | e.g. `contact:` |

¹ At least one of `instructions` / `prompt` must be present; providing both is best practice.

## Parameters

```yaml
parameters:
  - key: environment            # referenced as {{ environment }}
    input_type: string          # string | number | boolean | date | file | select
    requirement: required       # required | optional | user_prompt
    description: Deploy target.
    default: staging            # only for optional params
```

- `user_prompt` requirement: the run pauses and asks the user for the value at runtime.
- `select` input_type takes a list of allowed values.

## Extensions

```yaml
extensions:
  - type: builtin
    name: developer
  - type: stdio
    name: github
    description: GitHub MCP server
    cmd: npx
    args: [-y, "@modelcontextprotocol/server-github"]
    envs:
      GITHUB_PERSONAL_ACCESS_TOKEN: "${GITHUB_TOKEN}"   # env reference, never a literal secret
    timeout: 300
  - type: streamable_http
    name: remote-api
    uri: https://example.com/mcp
```

Types: `builtin`, `stdio`, `sse`, `streamable_http`, `inline_python`.

## Settings, activities, structured output

```yaml
settings:
  goose_provider: anthropic
  goose_model: claude-sonnet-4-5
  temperature: 0.3

activities:
  - "Scanning inbox…"
  - "Drafting summary…"

response:
  json_schema:
    type: object
    properties:
      summary: { type: string }
    required: [summary]
```

## Retry loop

Runs the recipe, then shell `checks`; retries up to `max_retries` until checks pass.

```yaml
retry:
  max_retries: 3
  timeout_seconds: 60
  checks:
    - type: shell
      command: ./scripts/check_output.sh
  on_failure: "Explain what the check rejected and fix it."
  on_success: "Checks passed — summarize the result."
```

## Templating

- `{{ parameter_key }}` in `instructions`/`prompt` is substituted at launch.
- Every `{{ variable }}` in the file — **including inside YAML comments** — must match a defined parameter, or validation fails with "Missing definitions for parameters". Mention placeholder syntax in comments without using literal braces.
- Missing values for `required` params block the run; `user_prompt` params are asked interactively.

## CLI

```bash
goose recipe validate <file>          # schema check — always run before installing
goose recipe list                     # what Goose sees
goose run --recipe <name-or-path>     # execute
goose run --recipe <name> --params key=value
goose recipe deeplink <file>          # share link for Desktop
goose recipe open <file>              # open in Desktop
```
