# Core Concepts of Agentic Development

Agentic development is a methodology where AI agents are orchestrated to perform software development tasks through a structured workflow. The core concepts include:

1. **Skills**: Modular, reusable instructions that agents follow to perform specific tasks. Skills are typically stored in markdown files and contain both mechanical processes and explanations of intent.
2. **Orchestration**: The process of managing multiple agents or sub-agents to complete complex tasks by breaking them down into smaller, manageable steps.
3. **Separation of Concerns**: Each agent should have a single, clear mission (e.g., implementation, review) to avoid conflicting priorities.
4. **Pressure Testing**: A method to validate skills by putting agents in high-pressure situations and observing their behavior, then updating the skill based on their rationalizations.
5. **Handoff**: The process of transferring context and tasks between agents to maintain clean context windows and focus.

## Why Skills Work
Skills leverage the fact that agents, like humans, respond to structured instructions and psychological principles. By providing clear, modular instructions, agents can perform tasks more reliably and with better outcomes. The use of sub-agents for specific tasks (e.g., implementation, review) ensures that each step is performed with a narrow, focused intent, reducing errors and improving quality.

## Key Principles
- **Explain the Why**: Agents perform better when they understand the intent behind tasks, allowing them to handle exceptions and generalize.
- **Disposable Agents**: Sub-agents should be created and discarded as needed to avoid context pollution and ensure fresh perspectives.
- **Rationalization Tables**: Skills should include tables of common rationalizations to preemptively address potential deviations from the intended behavior.

For more details on implementing these concepts, see [Practical Guide](references/practical_guide.md).