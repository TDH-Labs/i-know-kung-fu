# Decision Framework: RAG or Fine-Tuning?

## Decision Tree
Start by answering:
1. Is the primary need accessing specific documents or data? → RAG
2. Is the primary need consistent response style/behavior? → Fine-tuning
3. Do requirements change frequently? → RAG
4. Is the knowledge proprietary or sensitive? → RAG
5. Are you enforcing strict dialogue patterns? → Fine-tuning

## Common Patterns
- Company knowledge bases: RAG
- Policy chatbots: RAG
- Branded customer service: Fine-tuning + RAG
- Creative writing assistants: Fine-tuning
- Legal/medical applications: RAG with verification

## Implementation Timeline
RAG projects typically reach production 2-3x faster than fine-tuning solutions. Always:
1. Prototype with RAG first
2. Measure gaps in behavior control
3. Only then consider fine-tuning

## Cost Considerations
- RAG: Ongoing embedding/retrieval costs
- Fine-tuning: Upfront training costs + version management
- Hybrid: Both cost profiles apply