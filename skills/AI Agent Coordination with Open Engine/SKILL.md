---
description: A skill for coordinating multiple AI agents (Claude, ChatGPT, Codex,
  etc.) using Open Engine's queue-based system to eliminate manual handoffs and context
  switching between tools.
name: AI Agent Coordination with Open Engine
tags:
- agent coordination
- workflow automation
- multi-agent systems
- task queues
- Open Engine
---

# AI Agent Coordination with Open Engine

> A skill for coordinating multiple AI agents (Claude, ChatGPT, Codex, etc.) using Open Engine's queue-based system to eliminate manual handoffs and context switching between tools.

## Overview
Open Engine solves the critical bottleneck in multi-agent workflows by implementing a queue-based coordination system. Instead of humans manually transferring context between Claude, ChatGPT, Codex, and other tools, work moves through a centralized ticketing system where:
- **Agents** can claim tasks
- **Context** stays attached
- **Statuses** are automatically updated
- **Handoffs** are auditable

Key benefits ([Core Concepts](references/core_concepts.md)):
- Eliminates copy-paste between tools
- Maintains full context chain
- Allows cross-agent delegation
- Provides visibility for humans

## Step-by-Step Workflow

### 1. System Setup
1. Choose a queue system ([Practical Guide](references/practical_guide.md)):
   - Recommended: Linear (free tier)
   - Alternatives: Jira, Trello, custom solution
2. Configure standard labels:
   - `agent-instructions`
   - `needs-input`
   - `agent-done`

### 2. Agent Onboarding
For each AI tool (Claude/Codex/etc.):
1. Install the [Agent Setup Prompt](references/code_examples.md)
2. Test with smoke test ticket
3. Verify can:
   - Claim tasks
   - Move statuses
   - Attach outputs

### 3. Task Creation
Use template ([Code Examples](references/code_examples.md)):
```markdown
**Title**: Draft client proposal

**Background**:
- Client needs e-commerce site
- Budget: $50K
- Timeline: 3 months

**Constraints**:
- Use brand guidelines (attached)
- No technical jargon

**Definition of Done**:
- 1-page summary
- 3 key deliverables listed
- Flagged for legal review
```

### 4. Execution Flow
1. Agent detects new `agent-instructions` task
2. Claims ticket (moves to 'Agent Working')
3. Completes work using attached context
4. If blocked:
   - Moves to 'needs-input'
   - Asks specific question
5. When done:
   - Attaches all outputs
   - Moves to 'Agent Done'
   - Notes next steps

### 5. Cross-Agent Handoff
Example: Codex → Claude
1. Codex creates new ticket:
   - Assigns to Claude
   - Includes design specs
   - Labels `agent-instructions`
2. Claude picks up automatically

## Best Practices
1. **Ticket Hygiene** ([Common Pitfalls](references/common_pitfalls.md)):
   - One discrete action per ticket
   - Always include "Definition of Done"
2. **Context Management**:
   - Attach ALL source files
   - Never reference external chats
3. **Status Discipline**:
   - Enforce state transitions
   - Timeout stale tickets

## Validation
1. **Smoke Test** ([Code Examples](references/code_examples.md)):
   - Create "Say hello" ticket
   - Verify full agent loop
2. **Audit Checks**:
   - No context missing between steps
   - All decisions traceable
   - No silent failures

## Advanced Patterns
1. **Household Mode**:
   - Coordinate family schedules
   - Shared task visibility
2. **Team Scale**:
   - Agent-to-agent delegation
   - Cross-team dependencies
3. **Automated Review**:
   - Second-opinion agents
   - Compliance checking

## 📺 Source Videos

- [I Was The Only Thing Connecting Claude, ChatGPT, and Codex. So I Built My Replacement.](https://www.youtube.com/watch?v=QSK4vf_ZTRA) — AI News & Strategy Daily | Nate B Jones

**Difficulty**: Intermediate

## Prerequisites

- Basic familiarity with AI tools (Claude, ChatGPT, Codex)
- Access to a task queue system (Linear, Jira, etc.)
- Ability to configure agent instructions
