# Core Concepts of LLM Ops

LLM Ops extends traditional MLOps to address the unique challenges posed by large language models (LLMs) in production environments. Unlike traditional machine learning models, LLMs generate open-ended text, which introduces new operational complexities.

## Key Differences from MLOps
1. **Prompt Management**: Prompts are integral to the logic of LLM-based systems. Small changes in prompts can significantly alter outputs, necessitating versioning, testing, and monitoring.
2. **Data Flow**: LLM-based systems often use external context through retrieval-augmented (RA) pipelines, involving embeddings, vector databases, and retrieval logic.
3. **Evaluation**: Traditional metrics like accuracy and precision are insufficient for evaluating unstructured and subjective outputs. New strategies such as human feedback and quality scoring are required.
4. **Monitoring**: Beyond latency and errors, monitoring must include hallucinations, harmful outputs, drift in responses, and user feedback.
5. **Cost Management**: Token usage, prompt length, and retrieval size directly affect operational costs, making cost a first-class metric.
6. **Security and Compliance**: Sensitive data flowing through prompts, retrieved documents, and model outputs necessitate stricter controls and auditing.

Understanding these core concepts is essential for effectively managing LLMs in production environments.