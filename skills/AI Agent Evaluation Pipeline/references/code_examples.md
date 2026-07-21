## Code Examples

### Synthetic Dataset Creation
```python
# Sample code to create synthetic dataset
from langchain import LLMChain

# Define user personas
user_personas = {
    'loyal_customer': 'A long-time Lyft customer frustrated with earnings.',
    'refund_seeker': 'A customer seeking a refund for a recent ride.'
}

# Generate synthetic queries
for persona, description in user_personas.items():
    prompt = f"Generate a customer support query for a {persona}: {description}"
    query = LLMChain.run(prompt)
    print(query)
```

### LM Judge Prompt Template
```markdown
You are an evaluator for a customer support AI agent. Your task is to grade the agent's response based on the following criteria:
1. **Helpfulness**: Did the agent resolve the customer's issue?
2. **Appropriateness**: Was the agent's response appropriate for the situation?
3. **Completeness**: Did the agent provide a complete response?

Please provide a score from 1 to 5 for each criterion and a brief explanation.
```