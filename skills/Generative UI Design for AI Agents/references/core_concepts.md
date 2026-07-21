# Core Concepts of Generative UI
Generative UI is the layer that transforms AI model outputs into human-friendly interfaces. It ensures that the output is not just accurate but also interactive and scalable. This layer is crucial for delivering a seamless user experience.

### Key Components
1. **Rendering Contracts**: These define the UI components and layout rules that the AI model can output. They ensure that the model outputs structured UI intent rather than raw text.
2. **Streaming**: This technique delivers UI components in chunks, reducing perceived latency and keeping users engaged.
3. **Backend for Frontend (BFF)**: This handles platform-specific rendering rules, hydrates UI components, and attaches actions to elements.

### Importance
Generative UI is essential for creating user-centric AI applications. It bridges the gap between AI capabilities and human interaction, ensuring that the output is not just accurate but also user-friendly.

### Examples
- **Rendering Contracts**: A contract might specify that the model can output components like `date_field`, `time_field`, and `submit_button`.
- **Streaming**: A skeleton UI is shown first, then progressively filled as data arrives.
- **BFF**: The BFF handles platform differences and ensures that UI components are rendered correctly.

For more details, see [Practical Guide](references/practical_guide.md).