# Practical Guide

## Setting Up Claude Code
1. **Create Configuration Folder**: Start by creating a `.claude` folder in your project directory.
2. **Configuration File**: Inside the `.claude` folder, create a `settings.json.local` file and paste the provided configuration.
3. **API Key**: Sign up on OpenRouter.ai, generate an API key, and add it to your `settings.json.local` file.
4. **Select Model**: Choose a free model from OpenRouter, such as Nvidia's or MiniMax M2.5, and configure it in your settings.
5. **Base URL**: Set the base URL to `https://api.openrouter.ai`.

## Building Modular Applications
- **File Structure**: Organize your project into small, focused files, each handling a single responsibility.
- **Prompting**: When prompting the AI, specify the modular structure to ensure the generated code aligns with your project's architecture.

## Testing and Validation
- **Manual Testing**: After completing each task, manually test the feature to ensure it functions correctly.
- **GitHub Backup**: Push each tested feature to GitHub to maintain a backup of your progress.

## Common Pitfalls
- **Large Files**: Avoid creating large files that exceed the AI's context window.
- **Lack of Understanding**: Ensure you understand the core concepts of your application before prompting the AI.
- **Skipping Tests**: Always test each task before moving on to the next one.