## Practical Guide
This guide provides step-by-step instructions on how to integrate and use GLM 5.2 with tools like Cursor, OpenRouter, and Codex.

### Step-by-Step Instructions
1. **Obtain API Key**: Visit Z AI, the provider of GLM 5.2, and obtain an API key.
2. **Setup in Cursor**:
   - Open Cursor settings.
   - Paste the GLM API key into the OpenAI field.
   - Override the OpenAI endpoint with the GLM endpoint.
   - Add GLM 5.2 as a custom model.
3. **Setup in OpenRouter**:
   - Obtain an OpenRouter API key.
   - Configure OpenRouter to use GLM 5.2.
4. **Model Chaining**: Use Opus 4.8 for tasks requiring vision capabilities and GLM 5.2 for execution-based tasks.
5. **Run Tasks**: Execute tasks using GLM 5.2 through Cursor or OpenRouter.

### Best Practices
- **Cost Efficiency**: Use GLM 5.2 for tasks where token cost is a concern.
- **Model Chaining**: Combine GLM 5.2 with other models for tasks requiring different capabilities.
- **Local Execution**: Run GLM 5.2 locally to save on cloud token costs.

### Common Pitfalls
- **Resource Intensive**: Ensure your machine has sufficient GPU RAM to run GLM 5.2 locally.
- **Benchmark Misinterpretation**: Focus on practical performance rather than benchmark scores.

For more detailed information, refer to [Core Concepts](references/core_concepts.md) and [Code Examples](references/code_examples.md).