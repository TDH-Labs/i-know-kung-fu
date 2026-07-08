# Code and Prompt Examples for Gemini Agents

## Basic Spark Agent Initialization
```python
# Example API call to initialize a Spark agent
def create_spark_agent(task_description, schedule=None):
    agent_config = {
        "task": task_description,
        "subtasks": "auto",  # Allow agent to determine subtasks
        "output_format": "concise_report",
    }
    if schedule:
        agent_config["schedule"] = {
            "frequency": schedule["frequency"],
            "time": schedule["time"]
        }
    # This would call Gemini's API in practice
    return agent_config

# Example usage:
daily_brief_agent = create_spark_agent(
    "Prepare my daily briefing including calendar, emails, and pending tasks",
    schedule={"frequency": "daily", "time": "08:00"}
)
```

## Multimodal Processing Prompt
```
PROMPT TEMPLATE:
Combine these inputs to create a [DESIRED OUTPUT]:
1. [MEDIA TYPE 1]: [DESCRIPTION/PATH]
2. [MEDIA TYPE 2]: [DESCRIPTION/PATH]
3. [TEXT INSTRUCTIONS]: [SPECIFIC REQUIREMENTS]

EXAMPLE:
Combine these inputs to create a marketing poster:
1. Video: /content/product_demo.mp4
2. Images: /brand/logo.png, /photos/team.jpg
3. Text instructions: Use the logo in top right, extract key frames from video to show product features, include team photo with caption 'Meet the makers', use brand colors #FF5733 and #333333
```

## Voice Command Patterns
```
Effective voice command structure:
1. [Action verb] + [object] + [parameters]
   Example: "Schedule meeting with engineering team tomorrow at 2pm for 1 hour"

2. [Context] + [request]
   Example: "Regarding the quarterly report draft, add charts from these figures"

3. [Multi-step instruction]
   Example: "First analyze this spreadsheet for trends, then create a summary presentation with 3 slides"
```

## Scheduled Task Configuration
```json
{
  "agent_type": "recurring",
  "name": "Morning Briefing",
  "trigger": {
    "type": "scheduled",
    "time": "08:00",
    "days": ["mon", "tue", "wed", "thu", "fri"]
  },
  "tasks": [
    "Check calendar for today's appointments",
    "Scan unread emails for urgent items",
    "Review pending tasks from yesterday"
  ],
  "output": {
    "format": "bulleted_list",
    "delivery": "app_notification"
  }
}
```