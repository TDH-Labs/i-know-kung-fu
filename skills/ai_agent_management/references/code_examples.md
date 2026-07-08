## Code Examples
This document provides code snippets and prompt templates for managing AI agents.

### Setting up Observability with OpenTelemetry
```python
from opentelemetry import trace
from opentelemetry.sdk.trace import TracerProvider
from opentelemetry.sdk.trace.export import ConsoleSpanExporter

trace.set_tracer_provider(TracerProvider())
trace.get_tracer_provider().add_span_processor(ConsoleSpanExporter())
```

### Prompt Template for Agent Evaluation
```python
prompt_template = "Evaluate the performance of agent {agent_name} based on {criteria}."
```

### Example: Policy Enforcement
```python
# Example: Enforcing a policy to limit agent resource usage
policy = {
    "max_cpu_usage": "80%",
    "max_memory_usage": "1GB"
}

# Apply policy to agent
agent.apply_policy(policy)
```

For best practices and common pitfalls, refer to [Common Pitfalls](references/common_pitfalls.md).