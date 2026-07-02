---
description: A systematic approach to evaluate whether a product claiming to be an
  AI agent is truly agentic or just using basic AI/ML capabilities.
name: AI Agent Authenticity Evaluation
tags:
- AI agent evaluation
- agent authenticity
- generative AI
- autonomous systems
- AI classification
---

# AI Agent Authenticity Evaluation

> A systematic approach to evaluate whether a product claiming to be an AI agent is truly agentic or just using basic AI/ML capabilities.

## Overview
This skill enables you to systematically evaluate whether a system marketed as an AI agent truly meets the criteria for agentic behavior as defined in [Core Concepts](references/core_concepts.md). The methodology helps distinguish between simple AI/ML systems (Level 1), generative AI (Level 2), and true autonomous agents (Level 3).

## Step-by-Step Workflow
1. **Documentation Review**
   - Collect all available technical specifications
   - Map claimed capabilities to our three-tier framework

2. **Capability Testing**
   - Execute the test cases outlined in [Evaluation Workflow](references/evaluation_workflow.md)
   - Record responses and system behaviors

3. **Process Analysis**
   - Request execution traces or reasoning logs
   - Score against autonomy and iteration criteria

4. **Validation**
   - Repeat tests with novel inputs
   - Check for consistency across multiple trials

## Prompt Templates
```python
# Agent Capability Test
prompt = """
Please complete this multi-step task:
1. Analyze this business requirement: {requirement}
2. Generate a solution approach
3. Implement a prototype
4. Refine based on these constraints: {constraints}

Show your work at each step and explain any iterations.
"""
```

## Best Practices
1. Always test with unseen requirements
2. Verify process transparency
3. Measure time-to-solution for complex tasks
4. Check for adaptive behavior across sessions

## Common Pitfalls
Be aware of the evaluation mistakes documented in [Common Pitfalls](references/pitfalls.md), particularly:
- Accepting pre-canned demonstrations as proof of agency
- Not verifying the absence of human intervention
- Overlooking the difference between generation and true autonomy

## Validation Steps
1. **Reproducibility**: Can the agent handle similar but distinct tasks?
2. **Novelty Test**: Does it adapt to completely new domains?
3. **Stress Test**: How does it handle ambiguous or conflicting requirements?
4. **Process Audit**: Are intermediate steps truly automated?

## Final Assessment
Combine all observations using the scoring rubric from [Evaluation Workflow](references/evaluation_workflow.md) to determine the true agent level.

## 📺 Source Videos

- [Most AI agents are fake (here's a 10-second test)](https://www.youtube.com/watch?v=p1ak5NfWuEA) — Jeff Su

**Difficulty**: Intermediate

## Prerequisites

- understanding of AI fundamentals
- basic knowledge of machine learning
- familiarity with generative AI
