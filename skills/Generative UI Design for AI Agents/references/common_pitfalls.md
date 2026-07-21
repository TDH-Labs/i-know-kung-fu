# Common Pitfalls in Generative UI Design
This document outlines common pitfalls and how to avoid them when designing Generative UI layers.

### Pitfall 1: Ignoring Client Capabilities
Failing to account for client versions can lead to crashes. Always maintain a version map and ensure the model is aware of client capabilities.

### Pitfall 2: Overloading the Client
Avoid making the client infer UI from raw token outputs. Use structured UI intent and rendering contracts.

### Pitfall 3: Excessive Latency
Not using streaming can result in poor user experiences. Use streaming to deliver UI components in chunks and reduce perceived latency.

### Examples
- **Ignoring Client Capabilities**: A new UI component introduced in version 2.0 crashes older clients.
- **Overloading the Client**: The client tries to infer UI from raw token outputs, leading to incorrect rendering.
- **Excessive Latency**: Users experience long wait times because the UI is not streamed.

### Best Practices
- **Version Awareness**: Maintain a version map and ensure the model is aware of client capabilities.
- **Structured UI Intent**: Use rendering contracts to define UI components and layout rules.
- **Streaming**: Deliver UI components in chunks to reduce perceived latency.

For more details, see [Practical Guide](references/practical_guide.md).