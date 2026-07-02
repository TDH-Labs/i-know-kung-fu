# Core Concepts of Agentic Experimentation

Agentic experimentation refers to the process where AI agents autonomously modify and improve high-stakes machine learning systems while maintaining safety, reproducibility, and reviewability. Key concepts include:

1. **Infrastructure Automation**: The agent interacts with a semantic API (like Chronon) that abstracts away complex pipeline management. The API handles training data generation, model serving pipelines, and ensures consistency between training and inference environments.

2. **Resource Isolation**: Experiments run in isolated branches with dedicated compute/storage resources. This prevents interference with production systems while allowing controlled access to production data.

3. **Compute Reuse**: The system intelligently reuses precomputed features and partial aggregates from production to minimize redundant computations during experimentation.

4. **Reviewable Outputs**: All agent-generated changes must be production-ready and understandable by human reviewers before promotion to production.

5. **Safety Mechanisms**: Branch-based isolation, versioned outputs, and semantic hashing ensure experiments can't accidentally modify production data or pipelines.

These concepts work together to enable rapid iteration on critical systems like fraud detection, trust & safety models, and personalization systems where mistakes can have serious business consequences.