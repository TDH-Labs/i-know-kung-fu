# Practical Guide

## Step-by-Step Workflow

### 1. Frame the Problem

Understand the local context and the causality that led to the current situation. This involves identifying the objective and the environment within which the decision is being made.

### 2. Capture Context

Use short-term and long-term memory to capture relevant information. Short-term memory captures the immediate context, while long-term memory provides a broader overview.

### 3. Apply Reasoning

Use predefined policies and rules to determine the 'why' behind the decision. This involves analyzing the context and applying relevant rules to arrive at a decision.

### 4. Analyze Risks and Values

Perform a risk-value analysis to evaluate the potential outcomes of the decision. Consider factors such as reversibility, cost of being wrong, and the value of the decision.

### 5. Generate Alternatives

Propose multiple alternatives with pros and cons for each. This step involves brainstorming different options and evaluating their potential outcomes.

### 6. Make the Decision

Hand off the decision to an agent with the authority to act or escalate to a higher authority. Ensure that the decision is aligned with global rules and previous actions.

### 7. Record the Decision

Save the entire reasoning process and decision into the graph for future reference. This ensures traceability and accountability.

## Implementation Tips

- **Consistency**: Ensure that decisions are consistent with previous actions and global rules.
- **Explicitness**: Make implicit knowledge explicit by clearly defining policies and rules.
- **Traceability**: Record the entire reasoning process for accountability and future reference.

## Tools and Technologies

- **Neo4j**: A graph database that is ideal for capturing and managing contextual knowledge.
- **LangGraph**: A framework for building decision-aware AI agents.
- **Text to Cypher**: A tool that translates human text into Neo4j's query language, Cypher.

## Example Scenario

Consider a scenario where an AI agent needs to decide whether to approve a loan application. The agent would frame the problem, capture relevant context (e.g., applicant's credit history), apply reasoning (e.g., loan policies), analyze risks and values (e.g., potential default), generate alternatives (e.g., approve, reject, request more information), make the decision, and record the entire process.