# Core Concepts

## Retrieval-Augmented Generation (RAG)

RAG allows a language model to use external data at query time. When a user asks a question, the system retrieves relevant documents and passes them to the model as context. The model then generates an answer grounded in that data. This approach is particularly useful for factual, changing, or private information.

## Fine-Tuning

Fine-tuning changes the behavior of the model itself. The model is trained further so it consistently responds in a specific way. This is best for patterns, tone, and behavior. Fine-tuning is necessary when you need consistent behavior that retrieval and prompts cannot guarantee.

## Key Differences

- **RAG**: Best for factual, changing, or private information. Faster to implement and safer for production environments.
- **Fine-Tuning**: Best for patterns, tone, and behavior. Provides more control over the model's responses.

Understanding these core concepts is crucial for making informed decisions when building generative AI systems.
