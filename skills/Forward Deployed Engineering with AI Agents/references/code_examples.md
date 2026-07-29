# Code Examples
This document provides concrete code snippets and prompt templates for implementing Forward Deployed Engineering (FDE) with AI agents.

## Mapping a Workflow Using a Dependency Graph
```python
from graphlib import TopologicalSorter

tasks = {'A': {'B', 'C'}, 'B': {'D'}, 'C': {'D'}, 'D': set()}
ts = TopologicalSorter(tasks)
print(list(ts.static_order()))
```

## Prompt Template for Extracting Context
```plaintext
Extract the context from the following documentation:
1. Identify key process steps.
2. Highlight edge cases and failure modes.
3. Summarize the workflow in a dependency graph.
```

For more detailed steps and best practices, refer to the [Practical Guide](references/practical_guide.md).