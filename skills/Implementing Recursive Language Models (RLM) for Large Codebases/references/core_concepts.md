# Core Concepts of Recursive Language Models (RLM)

Recursive Language Models (RLM) are designed to handle large codebases by externalizing context management into a programmable execution environment. This approach allows the model to operate on the entire repository as data, curating relevant chunks and feeding them into the main context window. The core thesis of RLM is to avoid overloading the model's context by creating a separate environment where the model can write code to inspect, slice, and compute relevant chunks.

### Key Components
- **Externalized Context Management**: A dedicated environment for the model to operate on the codebase.
- **Curated Context**: Relevant chunks of code identified and fed into the main context window.
- **Recursive Queries**: Additional queries to other language models or systems to gather more information.

### Benefits
- **Improved Performance**: By externalizing context management, the model's performance does not degrade with larger codebases.
- **Enhanced Understanding**: Curated context and recursive queries enhance the model's understanding and reasoning over structured code data.

For practical implementation guidelines, refer to [Practical Guide](references/practical_guide.md).