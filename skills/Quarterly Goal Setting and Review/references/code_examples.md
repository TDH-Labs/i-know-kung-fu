## Code Examples
This document provides practical code examples for implementing quarterly goal setting and tracking progress.

### Example: Setting Quarterly Goals
```python
# Example: Setting Quarterly Goals
def set_quarterly_goals(yearly_goals):
    quarterly_goals = {}
    for i, goal in enumerate(yearly_goals):
        quarterly_goals[f'Q{i+1}'] = goal
    return quarterly_goals
```

### Example: Weekly Review
```python
# Example: Weekly Review
def weekly_review(tasks):
    completed_tasks = [task for task in tasks if task['status'] == 'completed']
    return completed_tasks
```

### Example: Quarterly Review
```python
# Example: Quarterly Review
def quarterly_review(quarterly_goals):
    achieved_goals = [goal for goal in quarterly_goals if goal['status'] == 'achieved']
    return achieved_goals
```

For best practices and pitfalls, refer to [Common Pitfalls](references/common_pitfalls.md).