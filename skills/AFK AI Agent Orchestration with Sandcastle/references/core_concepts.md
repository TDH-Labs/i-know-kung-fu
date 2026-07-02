# Core Concepts of AFK Agent Orchestration

## Sandboxing
Sandboxing is crucial for running AI agents autonomously without risking system damage or data exfiltration. Sandcastle provides isolated environments where agents can execute code safely. The transcript emphasizes Docker as the primary sandbox solution, though you can implement custom sandboxes.

## Parallel Processing
Multiple agents can run simultaneously to handle different tasks. The example shows planner, implementer, reviewer, and merger agents working in parallel. This requires careful orchestration to manage context and avoid conflicts.

## Backlog Management
GitHub Issues serve as the task queue with a dedicated 'Sandcastle' label filtering work items. Each issue becomes an atomic unit of work that agents process independently.

## Review Workflow
The transcript highlights a red-green-refactor pattern where:
1. Implementer creates initial code
2. Reviewer analyzes quality
3. Merger handles integration
This creates a safety net against faulty implementations.

## Prompt Engineering
Prompts use special syntax like exclamation-mark-prefixed code blocks that execute during resolution (e.g., !```git diff```). This enables dynamic prompt content based on repository state.