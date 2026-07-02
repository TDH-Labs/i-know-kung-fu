# Core Concepts

An AI Agent Operating System (Agent OS) is crucial for managing multiple AI agents efficiently. It ensures that agents can perform tasks without chaos, remember past interactions, and operate within defined boundaries. Key components include the scheduler, memory manager, tool manager, identity manager, observability, and guardrails.

## Scheduler

The scheduler, also known as the orchestrator, manages task priorities and resource allocation. It ensures that critical tasks, such as live customer interactions, are prioritized over background tasks like summarizing tickets.

## Memory Manager

Memory management involves short-term, long-term, and episodic memory systems. Short-term memory handles the current conversation, long-term memory stores past interactions, and episodic memory remembers specific approaches and their outcomes.

## Tool Manager

The tool manager organizes tools in a sandbox environment to prevent unauthorized access. It ensures that agents can only access specific tools and resources, such as restricting coding agents to certain folders.

## Identity Manager

Identity management uses short-lived tokens and permissions to control agent access. It ensures that agents have the necessary credentials to perform tasks and maintains an audit trail of their actions.

## Observability

Observability involves logging all agent decisions and tool calls for traceability. It allows you to trace back through the decision chain to identify errors or unauthorized actions.

## Guardrails

Guardrails define input and output checks and set governance policies. They ensure that agents operate within defined boundaries, such as requiring human approval for certain actions.