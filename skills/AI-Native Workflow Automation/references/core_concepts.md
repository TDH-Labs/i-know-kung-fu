# Core Concepts of AI-Native Workflow Automation

## Skill Files as Employees
A skill file is a markdown document that defines a single capability or job clearly enough for an AI agent to execute it. Think of each skill file as an employee with one specific role. For example, a skill file might define how to process an invoice or how to respond to a customer support ticket.

## Resolver Tables as Org Charts
A resolver table acts as an organizational chart for your AI workforce. When a task comes in, the resolver table determines which skill file (employee) should handle it. This is similar to how a traditional org chart routes work to different departments or individuals.

## Company Brains as Memory Layers
A company brain serves as the memory and knowledge base for your organization. It combines retrieval mechanisms with curation to ensure agents have the right context (the right three books open) for any given task. This is more than just RAG (Retrieval-Augmented Generation) - it includes provenance tracking, contradiction checks, and active pruning of stale information.

## Latent vs Deterministic Space
Understanding where computation happens is critical:
- **Latent space**: The LLM handles tasks requiring human-like judgment, taste, or understanding of vague requests
- **Deterministic space**: Traditional code handles precise, repeatable operations like data processing or calculations

## Working Memory Scale
While humans can hold about 7 items in working memory, AI agents can manage about a million tokens (roughly three Harry Potter books worth of information). This massive scale difference enables entirely new organizational structures.