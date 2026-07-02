# Common Pitfalls

Implementing an AI Agent Operating System can be challenging, and there are several common pitfalls to avoid.

## Overlooking Sandboxing

One of the most critical aspects of tool management is sandboxing. Without proper sandboxing, agents can access unauthorized resources, leading to security breaches. For example, a coding agent might accidentally delete a production database if it has unrestricted access.

## Inadequate Observability

Observability is crucial for tracing agent actions and identifying errors. Without comprehensive logging, it can be difficult to trace back through the decision chain to understand why an agent made a particular decision. For instance, if an agent approves a refund incorrectly, observability allows you to identify the root cause.

## Ignoring Memory Management

Memory management ensures that agents can recall past interactions and learn from them. Ignoring memory management can lead to agents starting from scratch in every interaction, reducing their efficiency and effectiveness. For example, an HR agent that doesn't remember past inquiries will need to ask the same questions repeatedly.

## Weak Identity Management

Identity management controls agent access and ensures that agents have the necessary credentials to perform tasks. Weak identity management can lead to unauthorized actions and security vulnerabilities. For example, a travel agent might book flights using unauthorized credit cards if identity management is not enforced.

## Lack of Guardrails

Guardrails define the boundaries within which agents can operate. Without guardrails, agents might perform actions that are inappropriate or incorrect. For example, an agent might approve refunds over $50 without human approval if guardrails are not in place.

## Poor Scheduler Design

The scheduler manages task priorities and resource allocation. Poor scheduler design can lead to critical tasks being delayed or overlooked. For example, live customer interactions might be deprioritized in favor of background tasks, leading to poor customer service.