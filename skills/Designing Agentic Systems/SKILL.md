---
description: A comprehensive skill for designing and implementing agentic systems,
  focusing on systems thinking, workflow design, decomposition, modularity, and algorithmic
  thinking.
name: Designing Agentic Systems
tags:
- agentic systems
- systems thinking
- workflow design
- decomposition
- modularity
- algorithmic thinking
---

# Designing Agentic Systems

> A comprehensive skill for designing and implementing agentic systems, focusing on systems thinking, workflow design, decomposition, modularity, and algorithmic thinking.

## Overview
Designing agentic systems involves more than just writing prompts or code; it requires a deep understanding of systems thinking, workflow design, decomposition, modularity, and algorithmic thinking. This skill will guide you through the process of designing robust, maintainable, and efficient agentic systems.

## Core Concepts
Before diving into the workflow, it's essential to understand the core concepts that underpin agentic system design. These include systems thinking, workflow design, decomposition, modularity, and algorithmic thinking. For a detailed explanation, refer to [Core Concepts](references/core_concepts.md).

## Step-by-Step Workflow
1. **Systems Thinking**: Identify the entire system in which the agent operates. This includes files, tools, humans, and other agents. Define the agent's job, dependencies, and failure modes.
2. **Workflow Design**: Design the workflow that the agent will follow. This includes defining the path from goal to action, considering retries, escalations, and idempotency.
3. **Decomposition**: Break down the agent's tasks into distinct jobs. Separate these jobs into reusable components.
4. **Modularity**: Create reusable modules such as skills and sub-agents. Ensure these modules can be reused across different agents and workflows.
5. **Algorithmic Thinking**: Determine which tasks are best handled by code and which require the agent's judgment. Use code for deterministic tasks and agents for tasks requiring judgment.

## Code Snippets and Prompt Templates
For concrete examples of code snippets and prompt templates, refer to [Code Examples](references/code_examples.md).

## Best Practices and Common Pitfalls
Best practices include designing for idempotency, using structured outputs, and maintaining clear contracts between system components. Common pitfalls include creating monolithic prompts and ignoring the distinction between tasks best handled by code and those requiring agent judgment. For more detailed guidelines, refer to [Practical Guide](references/practical_guide.md).

## Validation and Testing Steps
Validate your agentic system by ensuring it can handle retries, maintain state, and produce consistent outputs. Test the system by simulating various scenarios and checking for idempotency and consistency. For a detailed validation process, refer to [Validation Steps](references/validation_steps.md).

## 📺 Source Videos

- [Build Systems, Not Code - Angie Jones, Agentic AI Foundation](https://www.youtube.com/watch?v=ZD9-4fW2HhM) — AI Engineer

**Difficulty**: Advanced

## Prerequisites

- basic programming
- software engineering principles
- understanding of AI agents
