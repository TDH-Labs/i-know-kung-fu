# Core Concepts

## Observability
Observability in AI agents involves monitoring and understanding the internal state of the agent based on its external outputs. Traditional observability relies on metrics, logs, and traces, but for AI agents, logs are often sufficient. Logs provide detailed information about the agent's actions and can be used to reconstruct metrics and traces.

## Sandboxing
Sandboxing is the practice of running code in an isolated environment to prevent unintended interactions with the host system. This is crucial for AI agents that execute code or create files, ensuring safety and security.

## Agent-to-Agent Communication
The Agent-to-Agent (A2A) protocol facilitates communication between different agents. It defines a rigorous spec for agent interactions, ensuring alignment and consistency across the system.

## Effect Library
The Effect library for TypeScript provides structured concurrency, logging, and tracing capabilities. It helps in writing better TypeScript code and is particularly useful for designing the core agent loop.

## Rolling Summarization
Rolling summarization is a technique to manage long context in conversations. It involves summarizing the conversation periodically and using these summaries for recall, ensuring the agent remains contextually aware without being overwhelmed by too much information.
