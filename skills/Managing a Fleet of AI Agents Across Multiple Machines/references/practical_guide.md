# Practical Guide
This guide provides practical steps to manage a fleet of AI agents across multiple machines.

## Creating a Hierarchical Structure
1. **Define Roles**: Assign roles (CEO, VP, Manager, Worker) to each agent with clear responsibilities.
2. **Scope Context**: Ensure each agent has a scoped context and approval boundary.
3. **Delegate Tasks**: Delegate tasks down the hierarchy and ensure results flow back up.

## Maintaining State in Files
1. **Create Workspaces**: Each entity gets its own workspace on disk.
2. **Shared Context**: Store shared context that everyone has to honor in a shared directory.
3. **Machine-Bound State**: Store machine-specific state under machine directories.
4. **Handoff Folder**: Maintain a handoff folder for the actual work product that gets passed along.

## Implementing a Review Gateway
1. **Submit Plans**: Any layer that wants to act submits its plan to the review gateway.
2. **Wait for Approval**: The layer blocks and waits for approval.
3. **Trigger Work**: Once approved, a hook fires the work off automatically.

## Handling Machine Failures
1. **Commit Context Files**: Commit context files to Git and push them to other machines.
2. **Pull Context Files**: Use tmux send-keys over SSH to pull the context files and resume work.

## Centralizing Control
1. **Collapse Gateways**: Collapse multiple gateways into one main gateway on an always-on machine.
2. **Use Discord**: Use Discord as a single router with one bot per machine.

For more detailed information, refer to the Core Concepts and Code Examples.