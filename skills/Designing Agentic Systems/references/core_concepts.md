## Core Concepts
### Systems Thinking
Systems thinking involves understanding the entire system in which the agent operates. This includes identifying all components such as files, tools, humans, and other agents. Define the agent's job, dependencies, and failure modes.

### Workflow Design
Workflow design is crucial for defining the path from goal to action. Consider retries, escalations, and idempotency to ensure the agent can handle various scenarios.

### Decomposition
Decomposition involves breaking down the agent's tasks into distinct jobs. Separate these jobs into reusable components to improve maintainability and efficiency.

### Modularity
Modularity is about creating reusable modules such as skills and sub-agents. Ensure these modules can be reused across different agents and workflows.

### Algorithmic Thinking
Algorithmic thinking involves determining which tasks are best handled by code and which require the agent's judgment. Use code for deterministic tasks and agents for tasks requiring judgment.