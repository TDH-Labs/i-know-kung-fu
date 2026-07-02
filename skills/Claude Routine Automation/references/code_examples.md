# Code Examples
This document provides concrete code snippets and prompt templates for setting up and managing Claude routines.

## Prompt Template for Routine
```
Use the [Skill Name] for this [Task].
```

## Example Prompt for Churn Recovery
```
Use the churn recovery skill for this churned client.
```

## Setting Up API Trigger
To set up an API trigger, use the following cURL command:
```bash
curl -X POST https://api.claude.com/routines/trigger \
-H "Authorization: Bearer YOUR_TOKEN" \
-H "Content-Type: application/json" \
-d '{"event": "customer_subscription_updated"}'
```

## Uploading Skill to GitHub
To upload a skill to GitHub, use the following command:
```bash
git add .
git commit -m "Add churn recovery skill"
git push origin main
```

For more detailed guidance, refer to the [Practical Guide](references/practical_guide.md).