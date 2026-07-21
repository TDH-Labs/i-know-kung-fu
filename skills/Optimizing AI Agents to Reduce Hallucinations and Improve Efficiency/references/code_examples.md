### Code Examples

#### Semantic Tool Selection
```python
from sentence_transformers import SentenceTransformer
from faiss import IndexFlatL2

# Create embeddings for tools
tool_embeddings = SentenceTransformer('all-MiniLM-L6-v2').encode(tool_descriptions)

# Build a vector index
index = IndexFlatL2(tool_embeddings.shape[1])
index.add(tool_embeddings)

# Search for relevant tools
query_embedding = SentenceTransformer('all-MiniLM-L6-v2').encode(query)
_, indices = index.search(query_embedding, k=3)
relevant_tools = [tools[i] for i in indices[0]]
```

#### GraphRAG
```python
from neo4j import GraphDatabase

driver = GraphDatabase.driver("bolt://localhost:7687", auth=("neo4j", "password"))

# Execute a Cypher query
with driver.session() as session:
    result = session.run("MATCH (h:Hotel) WHERE h.city = 'Paris' RETURN AVG(h.rating) AS avg_rating")
    avg_rating = result.single()['avg_rating']
```

#### Multi-Agent Validation
```python
from swarms import Swarm

# Create a swarm of agents
swarm = Swarm([executor_agent, validator_agent, critic_agent])

# Execute a query
response = swarm.execute("Book a hotel in Paris")
```

#### Neuro-Symbolic Guardians
```python
from strands import Agent, Hook

# Define a rule hook
def booking_rule_hook(params):
    if params['guests'] > 10:
        raise ValueError("Maximum guest limit exceeded")

# Register the hook
agent = Agent()
agent.register_hook(Hook.BEFORE_TOOL_CALL, booking_rule_hook)
```

#### Runtime Guardians
```python
from agent_control import AgentControl

# Define steering rules
rules = [
    {"name": "steer_max_guests", "action": "reduce_guests", "condition": "guests > 10"},
    {"name": "deny_no_payment", "action": "block", "condition": "payment is None"}
]

# Register rules
agent_control = AgentControl(rules)
agent_control.register()
```

For more detailed explanations, refer to [Core Concepts](references/core_concepts.md).