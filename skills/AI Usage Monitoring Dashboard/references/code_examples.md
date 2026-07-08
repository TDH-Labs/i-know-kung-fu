# Code Examples and Prompt Templates

## Basic Dashboard Prompt
```
Create a Tufte-style dashboard showing my AI token usage with:
1. GitHub-style bar chart at top showing daily token burn
2. Logarithmic Y-axis to handle large value ranges
3. Color-coded by model (Codex=blue, Claude=green, ChatGPT=purple)
4. Top 10 highest usage days called out with activity notes
5. Same-day usage correlation showing what tasks drove spikes
```

## Claude Usage Estimator Prompt
```
Analyze these Claude chat logs and estimate token usage:
[PASTE LOGS]

Consider:
- Average tokens per character is 0.25
- System messages add 15% overhead
- Long context windows multiply base count by 1.5

Provide:
1. Total estimated tokens
2. Confidence interval
3. Breakdown by conversation
```

## Deployment Script
```python
# Sample Python script to collect Codex usage via API
import openai
from datetime import datetime, timedelta

def get_daily_usage(days_back=30):
    usage = []
    for i in range(days_back):
        date = (datetime.now() - timedelta(days=i)).strftime('%Y-%m-%d')
        response = openai.Usage.retrieve(date=date)
        usage.append({
            'date': date,
            'tokens': response['usage']['total_tokens'],
            'model': 'codex'
        })
    return usage
```