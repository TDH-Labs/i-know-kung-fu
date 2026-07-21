### Code Examples for Hermes Agent
This document provides concrete code snippets and prompt templates for managing Hermes Agent.

1. **Setting API Keys**: Securely store API keys in `.env` files.
```bash
HERMES_CONFIG_SET GITHUB_TOKEN=<your_token>
```

2. **Skill Development**: Create reusable playbooks for tasks.
```yaml
---
name: Generate Image
description: Generates an image based on a description.
steps:
  - description: Describe the image
    command: generate_image --description "{{ description }}"
---
```

3. **Cron Jobs**: Schedule automations using natural language commands.
```bash
hermes cron create --name "Daily AI News Briefing" --time "06:00" --command "generate_news_briefing"
```

4. **GitHub Sync**: Sync Hermes Agent with a GitHub repo.
```bash
hermes github sync --repo <repo_name> --token <github_token>
```

5. **Terminal Commands**: Manage Hermes Agent via terminal.
```bash
hermes start
hermes stop
hermes status
```

These examples provide a foundation for managing Hermes Agent effectively. For a deeper understanding of core concepts, refer to [Core Concepts](references/core_concepts.md).