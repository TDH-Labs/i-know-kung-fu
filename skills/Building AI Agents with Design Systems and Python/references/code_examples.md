# Code Examples

## Tool Creation
Create tools with docstrings and type hints.

```python
from agentspan import tool

@tool
def get_weather(city: str) -> str:
    """Returns the weather for a given city."""
    return f"Sunny in {city}"
```

## Agent Configuration
Define the agent with a name, model, and tool list.

```python
agent = Agent(
    name="WeatherBot",
    model="openai/gpt-4-mini",
    tools=[get_weather]
)
```

## Running the Agent
Start the Agentspan server and execute the agent.

```bash
uv run agentspan server start
uv run main.py
```

## Crash Resilience
Implement idempotent tool calls and use execution IDs to resume tasks.

```python
if execution_id:
    runtime.resume(execution_id)
else:
    runtime.run(agent)
```

For a practical guide, see [Practical Guide](references/practical_guide.md).