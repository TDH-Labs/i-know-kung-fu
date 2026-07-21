### Core Concepts

#### Semantic Tool Selection
Semantic tool selection involves filtering tools based on their relevance to a specific query. This reduces token usage by sending only the most relevant tools to the model. For example, a travel agent with 29 tools can reduce token usage from thousands to fewer than 300 by filtering tools.

#### GraphRAG
GraphRAG replaces text retrieval with structured graph queries. Instead of retrieving text chunks, it builds a knowledge graph from documents and uses Cypher queries to retrieve precise answers. This is especially useful for aggregations, counts, and multi-hop reasoning.

#### Multi-Agent Validation
Multi-agent validation adds a validation layer to catch errors before responses reach users. A swarm of agents (executor, validator, and critic) ensures that responses are accurate and free from hallucinations.

#### Neuro-Symbolic Guardians
Neuro-symbolic guardians enforce rules in code, not in prompts. This ensures that agents cannot bypass constraints. Rules are enforced using hooks that intercept tool calls before they execute.

#### Runtime Guardians
Runtime guardians allow agents to self-correct and complete tasks without hard stops. Steering rules enable agents to adjust and keep going, improving user experience.

For detailed code examples, refer to [Code Examples](references/code_examples.md).