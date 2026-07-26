## Code Examples

### Guardrail Prompt Template

```python
# Example of a guardrail prompt template
guardrail_prompt = """
Analyze the following user message for any signs of immediate danger or need for clinical intervention:

User Message: {user_message}

Provide a response indicating whether the message requires immediate intervention or can proceed to the core AI.
"""
```

### Eval Annotation Script

```python
# Example of an eval annotation script
def annotate_conversation(trace, rubric):
    # Logic to annotate conversation traces based on clinical rubric
    pass
```

### Conclusion

These code examples provide a starting point for implementing guardrails and evals-driven development in your mental health AI coach. By using these templates and scripts, you can ensure that your system is clinically grounded and continuously improving.