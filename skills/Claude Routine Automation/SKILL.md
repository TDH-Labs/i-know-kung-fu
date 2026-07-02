---
description: Automate recurring tasks and event-triggered workflows using Claude's
  routines, skills, and connectors. This skill enables you to build reliable, autonomous
  workflows for tasks like payment recovery, churn management, and personalized proposal
  generation.
name: Claude Routine Automation
tags:
- Claude
- routines
- automation
- skills
- connectors
- event-triggered
- scheduled tasks
---

# Claude Routine Automation

> Automate recurring tasks and event-triggered workflows using Claude's routines, skills, and connectors. This skill enables you to build reliable, autonomous workflows for tasks like payment recovery, churn management, and personalized proposal generation.

## Overview
Claude routines allow you to automate recurring tasks and event-triggered workflows using skills and connectors. Unlike traditional automation platforms, Claude leverages AI agents to handle complex, non-deterministic tasks. Learn more about the core concepts in [Core Concepts](references/core_concepts.md).

## Step-by-Step Workflow
1. **Define the Task**: Identify the task you want to automate (e.g., payment recovery, churn management).
2. **Build a Skill**: Create a skill that outlines the Standard Operating Procedure (SOP) for the task. Use the Process Interviewer Skill to ensure clarity and reliability.
3. **Test the Skill**: Use Claude's Skill Eval feature to test the skill. Run multiple tests to ensure reliability.
4. **Set Up Routine**: Create a new routine in Claude Code. Choose between local (scheduled tasks) and remote (event-triggered) routines.
5. **Configure Connectors**: Select the necessary connectors (e.g., Stripe, Gmail, Circle) for the routine.
6. **Upload Skill to GitHub**: Upload the skill to a GitHub repository to make it accessible to the routine.
7. **Set Trigger**: Define the trigger for the routine (e.g., schedule, API, GitHub).
8. **Validate Routine**: Test the routine to ensure it works as expected.

## Code/Prompt Templates
### Prompt Template for Routine
```
Use the [Skill Name] for this [Task].
```
### Example Prompt for Churn Recovery
```
Use the churn recovery skill for this churned client.
```

## Best Practices
- **Use Skills**: Always use skills in routines to make workflows deterministic and reliable.
- **Test Thoroughly**: Use Skill Eval to test skills before integrating them into routines.
- **Optimize Skills**: Use Auto Research Loop to optimize skills for specific criteria.

## Common Pitfalls
- **Non-Deterministic Workflows**: Avoid relying solely on prompts; use skills to ensure reliability.
- **Overloading Context Window**: Run bulk automations in separate sessions to avoid overloading the context window.

## Validation and Testing
- **Skill Eval**: Run multiple tests using Skill Eval to ensure the skill works reliably.
- **Routine Testing**: Test the routine with real data to ensure it performs as expected.

For more detailed guidance, refer to the [Practical Guide](references/practical_guide.md) and [Code Examples](references/code_examples.md).

## 📺 Source Videos

- [How to Use Claude Routines Better than 99% of People](https://www.youtube.com/watch?v=LLE6oMh7SxE) — Ben AI

**Difficulty**: Intermediate

## Prerequisites

- basic understanding of Claude
- familiarity with APIs and webhooks
