## Practical Guide
### Setting Up Knowledge Grounding
1. **Create a Knowledge Base**: Use Microsoft Foundry to create a knowledge base that includes unstructured, structured, and web data.
2. **Configure Data Sources**: Specify the sources of data (e.g., blob storage for PDFs, parquet tables for structured data).
3. **Save and Connect**: Save the knowledge base and connect it to your agents.

### Configuring Retrieval Systems
1. **Choose Retrieval Methods**: Decide between simple vector search and combined methods for better retrieval performance.
2. **Balance Latency and Quality**: Configure the retrieval system to balance between response time and the quality of retrieved information.
3. **Evaluate Performance**: Use metrics like recall and answer completeness to assess retrieval effectiveness.

### Optimizing Agents
1. **Generate Evaluation Tasks**: Create tasks to evaluate agent performance based on traces and instructions.
2. **Run Optimization**: Use the agent optimizer to generate and evaluate candidate configurations.
3. **Apply Best Configuration**: Deploy the optimized configuration to improve agent performance.

### Best Practices
- **Diverse Data Sources**: Ensure your knowledge base includes a variety of data sources for comprehensive grounding.
- **Combined Retrieval Methods**: Use a combination of retrieval techniques for better results.
- **Regular Optimization**: Continuously evaluate and optimize agents to capture learned knowledge and improve performance.