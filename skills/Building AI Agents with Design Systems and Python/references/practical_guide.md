# Practical Guide

## Setting Up
1. **Install Python 3.10+**: Ensure you have the correct Python version.
2. **Install JDK**: Necessary for running Agentspan.
3. **Install uv**: A package manager for Python dependencies.

## Creating Tools
Tools are Python functions that the agent can call. They must include docstrings and type hints to guide the agent.

```python
from agentspan import tool

@tool
def get_weather(city: str) -> str:
    """Returns the weather for a given city."""
    return f"Sunny in {city}"
```

## Configuring the Agent
Define the agent's name, model, and tool list. The model string should follow the format `provider/model_name`.

```python
agent = Agent(
    name="WeatherBot",
    model="openai/gpt-4-mini",
    tools=[get_weather]
)
```

## Running the Agent
Start the Agentspan server and run the agent. Use the dashboard to monitor executions.

```bash
uv run agentspan server start
uv run main.py
```

## Ensuring Resilience
Implement idempotent tool calls to handle crashes gracefully. Use execution IDs to resume interrupted tasks.

For code examples, see [Code Examples](references/code_examples.md).