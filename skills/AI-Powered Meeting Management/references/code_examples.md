# Code Examples for Meeting Management AI

## Agenda Generation Prompt Template
```
Given the following meeting context:
- Participants: [list names and roles]
- Previous meetings: [summary of past discussions]
- Organizational priorities: [current focus areas]

Generate a ranked list of agenda items that:
1. Addresses unfinished business from past meetings
2. Aligns with participants' roles and responsibilities
3. Advances organizational priorities
4. Balances strategic and tactical discussions

Format as:
1. [Topic] - [Suggested duration] - [Reason for inclusion]
2. [Topic] - [Suggested duration] - [Reason for inclusion]
...
```

## Debate Assistant API Call
```python
def get_counterpoints(main_argument):
    response = ai_api.query(
        prompt=f"Generate strong counterarguments to: {main_argument}",
        parameters={
            "max_points": 3,
            "style": "professional",
            "perspective": "critical"
        }
    )
    return response.formatted_points()
```

## Follow-up Email Generator
```
Template: "Post-Meeting Follow-up"
Variables:
- {meeting_date}
- {participants}
- {key_decisions}
- {action_items}
- {next_steps}

Default structure:
"Dear {participants},\n\nFollowing our meeting on {meeting_date}, here are the key outcomes:\n\nDecisions:\n{key_decisions}\n\nAction Items:\n{action_items}\n\nNext Steps:\n{next_steps}\n\nPlease let me know if you have any questions or need clarification on any points.\n\nBest regards,\n{your_name}"
```