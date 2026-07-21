# Practical Guide to Implementing Generative UI
This guide provides step-by-step instructions for implementing Generative UI layers in AI applications.

### Step 1: Define the Rendering Contract
Establish a contract between the AI model and the client that specifies UI components and layout rules. Ensure the model outputs structured UI intent rather than raw text.

### Step 2: Implement Streaming
Use streaming to deliver UI components in chunks, reducing perceived latency. Start with a skeleton UI, progressively fill it, and complete it as data arrives.

### Step 3: Build the BFF
Create a Backend for Frontend (BFF) that handles platform-specific rendering rules, hydrates UI components, and attaches actions to elements.

### Example Workflow
1. **Define the Contract**: Specify components and layout rules.
2. **Stream UI Components**: Deliver components in chunks.
3. **Render with BFF**: Use the BFF to handle platform-specific rendering.

### Best Practices
- **Version Awareness**: Ensure the model is aware of client capabilities by maintaining a version map.
- **Progressive Rendering**: Use streaming to show partial results and keep users engaged.
- **Platform-Specific Rules**: Let the BFF handle platform differences (e.g., Android vs. iOS).

For more examples, see [Code Examples](references/code_examples.md).