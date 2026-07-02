## Code Examples for Vector Database Integration

### Embedding Conversion
```python
from sentence_transformers import SentenceTransformer

# Load pre-trained embedding model
model = SentenceTransformer('all-MiniLM-L6-v2')

# Convert text to vector
text = "User query here"
vector = model.encode(text)
print(vector)
```

### Vector Storage
```python
import pinecone

# Initialize Pinecone
pinecone.init(api_key="your-api-key", environment="us-west1-gcp")

# Create or connect to a vector database
index = pinecone.Index("example-index")

# Store vector
index.upsert([("vector-id", vector)])
```

### Semantic Search
```python
# Search for similar vectors
query_vector = model.encode("Search query here")
results = index.query(query_vector, top_k=5)
print(results)
```

### Context Retrieval
```python
# Retrieve top relevant documents
for match in results['matches']:
    print(f"Document ID: {match['id']}, Score: {match['score']}")
```

### Answer Generation
```python
from transformers import pipeline

# Initialize language model
qa_pipeline = pipeline("question-answering")

# Generate answer based on retrieved context
context = "Retrieved document content here"
answer = qa_pipeline(question="User query here", context=context)
print(answer)
```

These code examples provide a practical guide to integrating vector databases with Generative AI systems. By following these steps, you can effectively convert, store, search, and retrieve vectors to enhance semantic search and improve the accuracy of generated answers.