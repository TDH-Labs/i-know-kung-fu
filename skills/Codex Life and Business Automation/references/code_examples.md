# Code Examples

This document provides code snippets and prompt templates for automating tasks with Codex and GPT 5.6.

## Email Summarization

```python
# Example: Automating Email Summarization
prompt = "Summarize the following email and draft a reply:"
email_content = "Dear Team, Please find attached the report for Q2. Best regards, John"
response = codex.generate(prompt + email_content)
print(response)
```

## SaaS App Development

```python
# Example: Building a SaaS App
app_name = "Turnaround"
prompt = f"Create a SaaS app called {app_name} that displays maintenance activities."
response = codex.generate(prompt)
print(response)
```

## Custom Model Training

```python
# Example: Fine-Tuning a Custom Model
prompt = "Fine-tune a model for copy editing using the following dataset:"
dataset = "path/to/dataset.csv"
response = codex.generate(prompt + dataset)
print(response)
```

For more detailed instructions, see [Practical Guide](references/practical_guide.md).