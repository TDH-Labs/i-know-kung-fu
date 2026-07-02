---
description: A comprehensive skill for setting up and managing autonomous AI coding
  agents using Sandcastle, a TypeScript library for orchestrating AI agents in isolated
  sandboxes.
name: AFK AI Agent Orchestration with Sandcastle
tags:
- ai-agent
- orchestration
- sandbox
- typescript
- autonomous-coding
---

# AFK AI Agent Orchestration with Sandcastle

> A comprehensive skill for setting up and managing autonomous AI coding agents using Sandcastle, a TypeScript library for orchestrating AI agents in isolated sandboxes.

## Overview
This skill enables you to setup autonomous AI coding agents that work in parallel while maintaining safety through sandboxing. Key components include:
- Isolated execution via Docker ([Core Concepts](references/core_concepts.md))
- GitHub issue-driven workflow
- Multi-stage review process

## Step-by-Step Workflow
1. **Initialize Environment**
   - Follow the [Practical Guide](references/practical_guide.md) to install and configure Sandcastle
   - Set up authentication tokens

2. **Create Work Items**
   - Add GitHub issues with the 'Sandcastle' label
   - Example: "Implement TypeScript CLI with Vitest"

3. **Run Orchestration**
   ```bash
   npm run sandcastle
   ```
   This triggers:
   - Planner agent scans issues
   - Implementers work in parallel branches
   - Reviewers validate changes
   - Merger handles final integration

4. **Monitor Progress**
   - Check agent-specific logs via control-click
   - Verify intermediate branches

## Code Templates
See [Code Examples](references/code_examples.md) for:
- Main orchestration logic
- Dynamic prompt templates
- Parallel execution patterns

## Best Practices
1. Always use sandboxes - unsandboxed agents can cause catastrophic damage
2. Implement the review workflow - catches 80% of implementation errors
3. Monitor context window usage - prevents incomplete task processing
4. Use constrained output formats (XML/JSON) for reliable parsing

## Validation
1. Check final merged code:
   - Tests pass
   - Type checking succeeds
   - Meets coding standards
2. Review GitHub issue closure comments
3. Verify no residual branches or sandbox artifacts

For complete troubleshooting, see [Common Pitfalls](references/pitfalls.md).

## 📺 Source Videos

- [I Open-Sourced My Own AFK Software Factory](https://www.youtube.com/watch?v=E5-QK3CDVQM) — Matt Pocock

**Difficulty**: Intermediate

## Prerequisites

- basic TypeScript knowledge
- familiarity with Docker
- GitHub account with repo access
- Anthropic API key or Claude subscription
