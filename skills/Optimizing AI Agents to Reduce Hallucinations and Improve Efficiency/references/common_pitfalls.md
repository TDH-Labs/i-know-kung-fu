### Common Pitfalls

#### Semantic Tool Selection
- **Pitfall**: Sending all tools in every query wastes tokens and increases costs.
- **Solution**: Filter tools based on relevance using semantic search.

#### GraphRAG
- **Pitfall**: Relying on text retrieval for structured queries leads to inaccurate answers.
- **Solution**: Use structured graph queries for precise answers.

#### Multi-Agent Validation
- **Pitfall**: Single agents may generate false success responses without validation.
- **Solution**: Implement a swarm of agents to validate responses.

#### Neuro-Symbolic Guardians
- **Pitfall**: Rules in prompts are suggestions, not constraints.
- **Solution**: Enforce rules in code using hooks.

#### Runtime Guardians
- **Pitfall**: Hard stops can frustrate users.
- **Solution**: Use steering rules to allow agents to self-correct and complete tasks.

For practical examples of how to avoid these pitfalls, refer to [Practical Guide](references/practical_guide.md).