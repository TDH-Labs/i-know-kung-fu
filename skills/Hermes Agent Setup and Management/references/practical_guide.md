### Practical Guide to Setting Up Hermes Agent
This guide provides step-by-step instructions for setting up and managing Hermes Agent on a virtual private server (VPS).

1. **Choose a VPS Provider**: Select a provider like Hostinger and deploy a VPS. Choose a plan based on your CPU and RAM needs.

2. **Install Hermes Agent**:
   - **One-Click Docker Installation**: Use the Docker manager in your VPS dashboard to install Hermes Agent in a containerized environment.
   - **Root Installation**: Alternatively, install Hermes directly on the VPS root using terminal commands.

3. **Configure Hermes Agent**:
   - **Inference Providers**: Set up inference providers like OpenAI Codex for model usage.
   - **Messaging Channels**: Configure messaging platforms such as Telegram for interaction.
   - **API Keys**: Securely store API keys in `.env` files using commands like `HERMES_CONFIG_SET GITHUB_TOKEN=<your_token>`.

4. **Develop Skills**: Create and manage skills using `skill.md` files. Example skill template:
```yaml
---
name: Generate Image
description: Generates an image based on a description.
steps:
  - description: Describe the image
    command: generate_image --description "{{ description }}"
---
```

5. **Set Up Cron Jobs**: Schedule automations using natural language commands. Example:
```bash
hermes cron create --name "Daily AI News Briefing" --time "06:00" --command "generate_news_briefing"
```

6. **Connect to GitHub**: Sync Hermes Agent with a GitHub repo for backup and version control. Ensure proper permissions for GitHub tokens to avoid creation failures.

For more detailed examples and code snippets, refer to [Code Examples](references/code_examples.md).