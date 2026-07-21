# Core Concepts

## Execution Layer

The Execution layer is the brain of your AI agent architecture. It manages the flow, state, durability, and retries of your system. This layer is designed to remain stable even as other components evolve. Key responsibilities include:

- **Flow Management**: Coordinating the sequence of tasks, such as planning, model calls, and tool invocations.
- **State Durability**: Ensuring that state is stored externally and can be resumed after failures.
- **Retries**: Handling retries for failed LLM calls, tool calls, and other operations.

## Context Layer

The Context layer is the knowledge hub of your architecture. It includes models, prompts, tools, and memory. This layer changes frequently as new models and tools emerge. Key responsibilities include:

- **Model Management**: Swapping models without affecting the Execution layer.
- **Prompt Engineering**: Designing and updating prompts to improve agent performance.
- **Tool Integration**: Integrating new tools and APIs as needed.

## Compute Layer

The Compute layer is the hands of your architecture. It includes sandboxes, runtimes, and browsers that your agent automates. This layer is ephemeral and stateless by design. Key responsibilities include:

- **Sandbox Execution**: Running code in isolated environments.
- **Browser Automation**: Automating web interactions.
- **File Manipulation**: Handling file operations within the sandbox.

By decoupling these layers, you can build a flexible and durable AI agent architecture that evolves with the rapidly changing landscape of AI tools and models.