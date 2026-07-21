## Code Examples

This document provides code snippets and prompt templates for configuring an AI phone agent.

### Prompt Template

```python
# Example prompt template for AI phone agent
prompt_template = """
You are an AI phone agent for {event_name}. Answer the following questions:
1. Where can I park?
2. What time is the event?
3. How do I contact support?
"""
```

### Call Forwarding Configuration

```bash
# Example call forwarding configuration
call_forwarding_config = {
    "source_number": "+1234567890",
    "destination_number": "+0987654321",
    "enabled": True
}
```

### Monitoring Script

```python
# Example monitoring script
import requests

def monitor_agent_performance(agent_id):
    response = requests.get(f"https://api.example.com/agents/{agent_id}/performance")
    return response.json()
```

For a comprehensive guide on setting up and deploying an AI phone agent, refer to [Practical Guide](references/practical_guide.md).