## Core Concepts

### Offline Evaluation
Offline evaluation involves simulating multi-turn conversations between the AI agent and a user LM. This is done using synthetic datasets that are representative of production traffic. The goal is to ensure the agent performs well before deployment.

### Online Evaluation
Online evaluation monitors the agent's performance in production. This includes tracing tools to track executions and context, as well as human-in-the-loop feedback to identify failure modes.

### LM Judge
An LM judge is a language model used to evaluate agent interactions. It grades the agent's responses based on predefined criteria, ensuring scores are actionable and tied to business outcomes.

### Continuous Learning
Continuous learning involves feeding evaluation insights back into the agent to improve its performance. This can include updating model weights, context, and harness.