# Core Concepts
Managing a fleet of AI agents across multiple machines involves several core concepts that ensure scalability, consistency, and efficiency.

## Hierarchical Structure
Implementing a hierarchical structure of agents (CEO, VP, Manager, Worker) helps in delegating tasks and managing context effectively. Each agent has a scoped context and approval boundary, ensuring that context flows down and results flow back up.

## State Management
Moving the state out of the model's context window and into files on disk ensures that the state is preserved even if the context window is cleared or the machine crashes. Each entity gets its own workspace with shared context, machine-bound state, and a handoff folder.

## Review Gateway
A centralized review gateway manages task approvals and triggers work automatically. Any layer that wants to act submits its plan and waits for approval. Once approved, a hook fires the work off automatically.

## Handling Machine Failures
Ensuring that the state is preserved involves committing context files to Git and pushing them to other machines. Using tmux send-keys over SSH pulls the context files and resumes work.

## Centralized Control
Collapsing multiple gateways into one main gateway on an always-on machine and using Discord as a single router with one bot per machine centralizes control and simplifies management.

For more detailed information, refer to the Practical Guide and Code Examples.