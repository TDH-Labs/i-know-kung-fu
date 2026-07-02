# Core Concepts: RAG vs Fine-Tuning

## Retrieval-Augmented Generation (RAG)
RAG enables language models to access external knowledge at inference time. The system:
1. Maintains a document store (often as vector embeddings)
2. Retrieves relevant documents for each query
3. Passes these documents as context to the LLM
4. Generates responses grounded in the retrieved content

Key characteristics:
- Dynamic knowledge: Documents can be updated without model changes
- Factual grounding: Responses reference specific source material
- Lower risk: No model modifications required

## Fine-Tuning
Fine-tuning modifies the base model's weights through additional training to:
1. Adopt specific response patterns
2. Internalize consistent behaviors
3. Learn domain-specific language

Key characteristics:
- Behavioral control: Enforces tone, structure, and style
- Pattern learning: Captures implicit knowledge not easily prompted
- Higher commitment: Requires retraining for updates

## When to Combine Both
Many production systems use RAG for factual retrieval and fine-tuning for response style control, creating systems that are both knowledgeable and consistent with brand voice.