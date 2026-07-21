## Code Examples
### Creating a Knowledge Base
```python
from foundry import KnowledgeBase

kb = KnowledgeBase(name='MovieData', unstructured_data='blob://movies.pdf', structured_data='parquet://movie_stats.parquet', web_data=True)
kb.save()
```

### Configuring Retrieval Systems
```python
from foundry import RetrievalSystem

rs = RetrievalSystem(knowledge_base='MovieData', methods=['vector_search', 'lexical_retrieval'], latency_quality_balance='medium')
rs.configure()
```

### Optimizing Agents
```python
from foundry import AgentOptimizer

optimizer = AgentOptimizer(agent='MovieAgent')
optimizer.generate_evaluation_tasks()
optimizer.run_optimization()
optimizer.apply_best_configuration()
```

### Best Practices
- **Code Readability**: Ensure your code is well-commented and easy to understand.
- **Modular Design**: Use modular design to make your code reusable and maintainable.
- **Error Handling**: Implement robust error handling to manage unexpected issues.