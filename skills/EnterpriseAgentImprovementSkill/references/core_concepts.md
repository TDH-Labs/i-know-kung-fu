# Core Concepts
Enterprise AI agents face three main problems: ambiguity, staleness, and preference. Ambiguity arises when the agent doesn't know which data source or knowledge base to use. Staleness occurs when the context becomes outdated. Preference issues emerge when different teams or individuals have varying definitions or metrics.

## Ambiguity
Ambiguity is addressed by dividing knowledge bases into three layers: semantic layer, canonical tables, and database graph. The semantic layer is the cleanest source of truth, containing curated queries, KPI definitions, and business definitions. Canonical tables provide parametric queries, offering flexibility. The database graph connects tables and columns, allowing for complex queries.

## Staleness
Staleness is managed through a context lifecycle, which includes embedding live data sources and establishing a feedback loop. Live data sources are regularly updated and reviewed. The feedback loop captures events that indicate changes in context or preference.

## Preference
Preference issues are addressed by storing individual or team preferences in a semantic layer or agent memory. This allows the agent to route to the right metric based on who is using it.

For more detailed information, refer to the [Practical Guide](references/practical_guide.md) and [Code Examples](references/code_examples.md).