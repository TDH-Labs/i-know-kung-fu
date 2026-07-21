# Practical Guide
This guide provides practical steps to improve enterprise AI agents by addressing ambiguity, staleness, and preference issues.

## Step-by-Step Workflow
1. **Identify Sources of Truth**: Divide knowledge bases into three layers: semantic layer, canonical tables, and database graph. Start from the cleanest source and move to the most dynamic one.
2. **Create a Context Lifecycle**: Embed live data sources and establish a feedback loop to keep the context updated.
3. **Capture Preferences**: Store individual or team preferences in a semantic layer or agent memory.
4. **Evaluate and Update**: Regularly evaluate the agent's performance and update the context based on feedback.

## Best Practices
- **Hierarchical Knowledge Bases**: Always start from the cleanest source of truth and move to the most dynamic one.
- **Regular Updates**: Ensure that live data sources are regularly updated and reviewed.
- **Feedback Loop**: Capture and log every event that indicates a change in context or preference.

## Common Pitfalls
- **Equal Weighting of Knowledge Bases**: Avoid treating all knowledge bases equally. Use a hierarchical approach.
- **Outdated Context**: Regularly update the context to avoid staleness.
- **Ignoring Preferences**: Capture and store individual or team preferences to avoid ambiguity.

For more detailed information, refer to the [Core Concepts](references/core_concepts.md) and [Code Examples](references/code_examples.md).