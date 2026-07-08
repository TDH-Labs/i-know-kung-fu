## Practical Guide
### Best Practices
1. **Design for Idempotency**: Ensure that retries do not cause unintended side effects.
2. **Use Structured Outputs**: Define clear contracts for the agent's output to ensure consistency.
3. **Maintain Clear Contracts**: Ensure that all system components have agreed-upon shapes for communication.

### Common Pitfalls
1. **Monolithic Prompts**: Avoid creating large, monolithic prompts that handle multiple tasks. Decompose them into smaller, manageable components.
2. **Ignoring Task Distinction**: Do not ignore the distinction between tasks best handled by code and those requiring agent judgment. Use code for deterministic tasks and agents for tasks requiring judgment.