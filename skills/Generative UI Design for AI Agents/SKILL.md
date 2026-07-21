---
description: A skill for designing and implementing Generative UI layers that bridge
  AI model outputs and human-friendly interfaces, ensuring seamless, scalable, and
  user-centric experiences.
name: Generative UI Design for AI Agents
tags:
- Generative UI
- UX Design
- AI Agents
- Streaming
- BFF
---

# Generative UI Design for AI Agents

> A skill for designing and implementing Generative UI layers that bridge AI model outputs and human-friendly interfaces, ensuring seamless, scalable, and user-centric experiences.

### Overview
Generative UI is the layer between AI model outputs and the user interface that ensures the output is rendered in a human-friendly, interactive, and scalable way. This skill focuses on three core patterns: **Rendering Contracts**, **Streaming**, and **Backend for Frontend (BFF)**. Learn how to design these layers effectively to create seamless user experiences.

For a deeper dive into the concepts, see [Core Concepts](references/core_concepts.md).

### Step-by-Step Workflow
1. **Define the Rendering Contract**: Establish a contract between the AI model and the client that specifies UI components and layout rules. Ensure the model outputs structured UI intent rather than raw text.
2. **Implement Streaming**: Use streaming to deliver UI components in chunks, reducing perceived latency. Start with a skeleton UI, progressively fill it, and complete it as data arrives.
3. **Build the BFF**: Create a Backend for Frontend (BFF) that handles platform-specific rendering rules, hydrates UI components, and attaches actions to elements.

For detailed implementation steps, refer to [Practical Guide](references/practical_guide.md).

### Code Snippets
```python
# Example of a Rendering Contract
contract = {
  "components": ["date_field", "time_field", "submit_button"],
  "layout_rules": {
    "flights": {
      "1-3": "swipable_carousel",
      "4+": "vertical_list"
    }
  }
}
```

For more examples, see [Code Examples](references/code_examples.md).

### Best Practices
- **Version Awareness**: Ensure the model is aware of client capabilities by maintaining a version map.
- **Progressive Rendering**: Use streaming to show partial results and keep users engaged.
- **Platform-Specific Rules**: Let the BFF handle platform differences (e.g., Android vs. iOS).

### Common Pitfalls
- **Ignoring Client Capabilities**: Failing to account for client versions can lead to crashes.
- **Overloading the Client**: Avoid making the client infer UI from raw token outputs.
- **Excessive Latency**: Not using streaming can result in poor user experiences.

For more pitfalls and how to avoid them, see [Common Pitfalls](references/common_pitfalls.md).

### Validation and Testing
1. **Test Rendering Contracts**: Ensure the model outputs structured UI intent and adheres to layout rules.
2. **Simulate Streaming**: Verify that UI components are delivered in chunks and rendered progressively.
3. **Validate BFF Outputs**: Check that the BFF correctly hydrates UI components and attaches actions.

### References

## 📺 Source Videos

- [Agent Output Is Not UX: Rendering Layer Your LLM Pipeline Is Missing - Bala Ramdoss, Amazon Lens](https://www.youtube.com/watch?v=maTp79FD9gI) — AI Engineer

**Difficulty**: Intermediate

## Prerequisites

- Basic understanding of AI models
- Familiarity with UI/UX design principles
