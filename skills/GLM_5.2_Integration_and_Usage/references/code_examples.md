## Code Examples
This document provides concrete code snippets and prompt templates for integrating and using GLM 5.2 with tools like Cursor, OpenRouter, and Codex.

### Code Snippets
```python
# Example of setting up GLM 5.2 in Cursor
import cursor

cursor.set_api_key('your_glm_api_key')
cursor.set_endpoint('https://api.zai.com/glm5.2')
cursor.add_model('GLM 5.2', 'glm5.2')
```

### Prompt Templates
```python
# Example prompt for model chaining
prompt = "Use Opus 4.8 to analyze the image and describe it. Then, use GLM 5.2 to execute the task based on the description."
```

### Best Practices
- **Cost Efficiency**: Use GLM 5.2 for tasks where token cost is a concern.
- **Model Chaining**: Combine GLM 5.2 with other models for tasks requiring different capabilities.
- **Local Execution**: Run GLM 5.2 locally to save on cloud token costs.

### Common Pitfalls
- **Resource Intensive**: Ensure your machine has sufficient GPU RAM to run GLM 5.2 locally.
- **Benchmark Misinterpretation**: Focus on practical performance rather than benchmark scores.

For more detailed information, refer to [Core Concepts](references/core_concepts.md) and [Practical Guide](references/practical_guide.md).