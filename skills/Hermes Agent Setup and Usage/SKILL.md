---
description: A comprehensive guide to setting up and using the Hermes AI Agent locally
  on your machine, including Telegram integration, skill management, and cron job
  setup.
name: Hermes Agent Setup and Usage
tags:
- Hermes Agent
- AI Agent
- Telegram Integration
- Cron Jobs
- Local Setup
---

# Hermes Agent Setup and Usage

> A comprehensive guide to setting up and using the Hermes AI Agent locally on your machine, including Telegram integration, skill management, and cron job setup.

## Overview
Hermes Agent is a powerful, open-source AI agent that runs locally on your machine. It features a curator for self-improvement, bounded memory for consistent performance, and integrates with Telegram for easy interaction. For a detailed breakdown of its core concepts, see [Core Concepts](references/core_concepts.md).

## Step-by-Step Workflow
1. **Download and Install**:
   - Visit hermesagent.newsresearch.com and download the app for your OS.
   - Install it by dragging to Applications (Mac) or running the installer (Windows).

2. **Initial Setup**:
   - Launch Hermes and click "Install Hermes" to download dependencies.
   - Configure the AI model using a free Google AI Studio API key. See [Practical Guide](references/practical_guide.md) for details.

3. **Telegram Integration**:
   - Create a bot via @BotFather in Telegram.
   - Paste the bot token and your user ID into Hermes. Restart the messaging gateway.

4. **Agent Context**:
   - Start a chat session and provide context about yourself. Example prompts are in [Code Examples](references/code_examples.md).

5. **Cron Jobs and Skills**:
   - Set up cron jobs for automated tasks like morning news briefs.
   - Manage skills via the Skills section in the sidebar.

6. **Maintenance**:
   - Regularly run the curator (`Hermes curator run`) to optimize skills.
   - Use `Hermes doctor` for diagnostics.

## Best Practices
- **Calibration**: Regularly check and update your agent's knowledge about you.
- **Security**: Only whitelist trusted Telegram IDs.
- **Memory Management**: Avoid overloading the agent with redundant skills.

For common pitfalls and how to avoid them, see [Common Pitfalls](references/common_pitfalls.md).

## Validation Steps
1. **Telegram Test**: Send a message to your bot to ensure it responds.
2. **Cron Job Test**: Verify that scheduled tasks execute as expected.
3. **Curator Test**: Run the curator and check the skill library for optimizations.

By following this guide, you'll have a fully functional Hermes Agent tailored to your needs.

## 📺 Source Videos

- [Hermes Agent Tutorial: How to Setup & Use Open Source AI Agent for Beginners](https://www.youtube.com/watch?v=uSdVgSY7ryU) — AI Master

**Difficulty**: Beginner

## Prerequisites

- Basic understanding of AI agents
- Telegram account
- Google account for API key
