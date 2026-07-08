---
description: A comprehensive skill for AI agents to perform complex tasks by perceiving,
  reasoning, acting, and learning in iterative cycles with optional human oversight.
name: AI Agent Workflow Execution
tags:
- agentic AI
- workflow execution
- task decomposition
- academic research
- iterative refinement
---

# AI Agent Workflow Execution

> A comprehensive skill for AI agents to perform complex tasks by perceiving, reasoning, acting, and learning in iterative cycles with optional human oversight.

## Overview
This skill enables you to perform complex academic and research tasks through iterative perception-reasoning-action-learning cycles. Unlike single-query responses, you'll decompose tasks, utilize specialized tools, and refine outputs through multiple iterations - functioning more like a research assistant than a simple chatbot. See [Core Concepts](references/core_concepts.md) for foundational principles.

## Step-by-Step Workflow
1. **Task Reception**
   - Parse the user request for key components (topic, scope, deliverables)
   - Example: "Create literature review on perovskite solar cells focusing on stability studies from 2018-2023"

2. **Plan Formulation**
   - Break into subtasks (literature search, analysis, synthesis)
   - Allocate sub-agents if needed
   - Present plan for approval ("I'll search 50 papers, identify top 20, then create tables comparing degradation rates")

3. **Execution with Tools**
   - Use connected APIs (Consensus, Zotero)
   - Apply prompt templates from [Prompt Templates](references/prompt_templates.md)
   - Maintain audit trail of sources

4. **Quality Control**
   - Cross-verify 20% of references
   - Check for hallucination using fact-verification tools
   - Format according to academic standards

5. **Iterative Refinement**
   - Incorporate user feedback
   - Limit to 3-5 refinement cycles
   - Finalize when all quality metrics pass

## Best Practices
1. **Clear Scope Definition**
   - Bad: "Find some papers about batteries"
   - Good: "Find 10 peer-reviewed papers about solid-state battery interfaces published in Nature journals since 2020"

2. **Controlled Automation**
   - Set runtime limits (max 60 minutes for complex tasks)
   - Implement mandatory checkpoints for human review

3. **Academic Rigor**
   - Always trace claims to verifiable sources
   - Use academic formatting (APA/MLA)
   - Disclose search methodology

## Common Pitfalls
1. **Unbounded Research**
   - Without clear limits: "The agent searched 500 papers when 50 would suffice"
   - Solution: Set explicit bounds ("Include maximum 30 references")

2. **Format Inconsistency**
   - Mixing citation styles in one document
   - Solution: Specify style upfront and validate before delivery

3. **Over-automation**
   - Making significant research decisions without human input
   - Solution: Build in approval steps for hypothesis generation or gap analysis

## Validation Protocol
1. **Source Verification**
   - Randomly check 20% of citations exist and support claims
2. **Logical Flow Check**
   - Ensure arguments follow coherent structure
3. **Originality Assessment**
   - Compare against source materials for proper synthesis
4. **User Acceptance Testing**
   - Confirm output meets intended use case

For complete workflow details, consult the [Practical Guide](references/workflow_guide.md). Always use the structured [Prompt Templates](references/prompt_templates.md) for consistent results.

## 📺 Source Videos

- [What Is Agentic AI? AI Agents and the Revolution That Changes Everything](https://www.youtube.com/watch?v=fOfy-OsKWf4) — Andy Stapleton

**Difficulty**: Intermediate

## Prerequisites

- basic prompt engineering
- API integration knowledge
- task decomposition understanding
