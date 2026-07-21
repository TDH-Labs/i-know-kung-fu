---
description: Learn how to configure and use Claude Code for free to build modular,
  scalable applications. This skill covers setup, best practices, and workflow optimization
  for AI-assisted development.
name: Build Applications with Claude Code
tags:
- Claude Code
- AI-assisted development
- modular applications
- OpenRouter
- free AI models
---

# Build Applications with Claude Code

> Learn how to configure and use Claude Code for free to build modular, scalable applications. This skill covers setup, best practices, and workflow optimization for AI-assisted development.

## Overview
This skill teaches you how to configure Claude Code for free using OpenRouter and build modular, scalable applications. You'll learn to set up the environment, structure your projects effectively, and optimize your workflow for AI-assisted development.

## Step-by-Step Workflow
1. **Set Up Claude Code**: Create a `.claude` folder and a `settings.json.local` file. Paste the configuration provided in the transcript.
2. **Obtain API Key**: Sign up on OpenRouter.ai, create an API key, and paste it into your `settings.json.local` file.
3. **Select Free Model**: On OpenRouter, search for free models like Nvidia's or MiniMax M2.5, and configure them in your settings.
4. **Set Base URL**: Use the provided base URL in your configuration.
5. **Test Configuration**: Run Claude Code in your terminal and verify the setup by interacting with the model.

## Code Snippets
```json
{
  "api_key": "your_api_key_here",
  "model": "MiniMax M2.5",
  "base_url": "https://api.openrouter.ai"
}
```

## Best Practices
- **Modular Structure**: Keep files small and focused, ideally under 600 lines of code. This helps the AI maintain context and reduces errors.
- **Understand Building Blocks**: Before prompting the AI, understand the core concepts of your application to avoid issues like race conditions.
- **One Task Per Session**: Break down features into small tasks, test each one, and push to GitHub before moving to the next task.

## Common Pitfalls
- **Large Files**: Avoid dumping everything into one file. This can cause the AI to lose context and hallucinate.
- **Lack of Understanding**: Not understanding core concepts can lead to flawed applications. Always know what to ask the AI.
- **Skipping Tests**: Failing to test each task can result in broken features. Always test before pushing to GitHub.

## Validation and Testing
- **Manual Testing**: After completing each task, manually test the feature to ensure it works as expected.
- **GitHub Backup**: Push each tested feature to GitHub to maintain a backup of your progress.

For more detailed guidance, refer to the [Core Concepts](references/core_concepts.md), [Practical Guide](references/practical_guide.md), and [Code Examples](references/code_examples.md).

## 📺 Source Videos

- [Claude Code Is Now 100% Free - Here's How](https://www.youtube.com/watch?v=t0Mesp118l4) — Hasan Aboul Hasan

**Difficulty**: Intermediate

## Prerequisites

- basic programming knowledge
- familiarity with VS Code
- understanding of API keys
