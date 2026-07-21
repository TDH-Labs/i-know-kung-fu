---
description: Learn how to effectively manage a fleet of AI agents across multiple
  machines by implementing a hierarchical structure, maintaining state in files, and
  using a centralized review gateway.
name: Managing a Fleet of AI Agents Across Multiple Machines
tags:
- AI agents
- multi-machine management
- hierarchical structure
- state management
- review gateway
---

# Managing a Fleet of AI Agents Across Multiple Machines

> Learn how to effectively manage a fleet of AI agents across multiple machines by implementing a hierarchical structure, maintaining state in files, and using a centralized review gateway.

## Overview
Managing a fleet of AI agents across multiple machines requires a structured approach to ensure scalability, consistency, and efficiency. This skill involves creating a hierarchical organization of agents, maintaining state in files, and using a centralized review gateway to manage tasks and approvals.

## Step-by-Step Workflow
1. **Create a Hierarchical Structure**: Implement a hierarchy of agents (CEO, VP, Manager, Worker) where each agent has a scoped context and approval boundary. Context flows down, and results flow back up.
2. **Maintain State in Files**: Move the state out of the model's context window and into files on disk. Each entity gets its own workspace with shared context, machine-bound state, and a handoff folder.
3. **Implement a Review Gateway**: Build a review gateway where any layer that wants to act submits its plan and waits for approval. Once approved, a hook fires the work off automatically.
4. **Handle Machine Failures**: Ensure that the state is preserved by committing context files to Git and pushing them to other machines. Use tmux send-keys over SSH to pull the context files and resume work.
5. **Centralize Control**: Collapse multiple gateways into one main gateway on an always-on machine. Use Discord as a single router with one bot per machine.

## Code Snippets
```bash
# Example CLI harness for dispatching tasks
function dispatch_task() {
  local task=$1
  local worker=$2
  tmux send-keys -t $worker "$task" C-m
}

# Example Git commit and push for context files
git add .
git commit -m "Update context files"
git push origin main

# Example tmux send-keys over SSH
ssh user@machine 'tmux send-keys -t session_name "git pull" C-m'
```

## Best Practices
- **Hierarchical Structure**: Ensure each agent has a clear role and scope to avoid context overload.
- **State Management**: Keep state in files to preserve work even if the context window is cleared or the machine crashes.
- **Review Gateway**: Use a centralized review gateway to manage approvals and avoid manual checks.

## Common Pitfalls
- **Context Overload**: Avoid holding multiple contexts in your head by delegating responsibilities to agents.
- **Memory Issues**: Monitor memory usage and avoid overloading a single machine with too many tasks.
- **Credential Collisions**: Use fully separated environments for each workspace to prevent credential collisions.

## Validation and Testing
- **Test Hierarchical Structure**: Ensure that tasks are correctly delegated and results flow back up the hierarchy.
- **Validate State Management**: Verify that state is preserved and can be resumed after a context reset or machine crash.
- **Check Review Gateway**: Confirm that the review gateway correctly manages approvals and triggers work automatically.

For more detailed information, refer to the following documents:
- [Core Concepts](references/core_concepts.md)
- [Practical Guide](references/practical_guide.md)
- [Code Examples](references/code_examples.md)

## 📺 Source Videos

- [I Run a Fleet of AI Agents Across Three Machines. Here's What Broke. - Kyle Jaejun Lee, KRAFTON](https://www.youtube.com/watch?v=4kYl2_mqmnQ) — AI Engineer

**Difficulty**: Advanced

## Prerequisites

- basic knowledge of AI agents
- familiarity with CLI tools
- understanding of file-based state management
