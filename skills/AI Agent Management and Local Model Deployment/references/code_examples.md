# Code Examples

## Setting Up a Local AI Model
```python
import ollama

# Initialize the model
model = ollama.Model('gpt-4')

# Define the agent's task
task = "Summarize today's meeting notes and highlight action items."

# Run the model locally
response = model.generate(task)
print(response)
```

## Prompt Template for Customer Support
```
You are a customer support agent. Your task is to respond to customer inquiries promptly and accurately. Use the following guidelines:
1. Be polite and professional.
2. Provide accurate information.
3. Escalate complex issues to a human supervisor.
```

For more detailed guidance, refer to the practical guide and core concepts.