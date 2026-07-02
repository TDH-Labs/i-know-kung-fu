---
description: A comprehensive skill for AI agents to perform agentic development tasks
  including brainstorming, planning, implementation, and review using skills-based
  workflows.
name: Agentic Development with Skills
tags:
- agentic
- skills
- development
- workflow
- orchestration
---

# Agentic Development with Skills

> A comprehensive skill for AI agents to perform agentic development tasks including brainstorming, planning, implementation, and review using skills-based workflows.

## Overview
Agentic development uses structured skills and orchestrated sub-agents to perform software development tasks. This skill combines methodologies from both transcripts into a comprehensive workflow covering brainstorming, planning, implementation, and review. Key concepts are explained in [Core Concepts](references/core_concepts.md).

## Step-by-Step Workflow
1. **Brainstorming**
   - Use psychological techniques to extract clear requirements
   - Document the actual problem, not just perceived solutions

2. **Planning**
   - Break the task into tiny, testable steps
   - Specify files, success criteria, and likely code
   - Create a plan file with context blocks for each task

3. **Implementation**
   - Orchestrator spawns implementer sub-agents for each task
   - Each implementer gets only its specific context block
   - Implementers return results to orchestrator

4. **Review**
   - Fresh spec compliance reviewer checks each implementation
   - Fresh code quality reviewer evaluates style and standards
   - Any issues are sent back to the implementer

5. **Handoff** (when needed)
   - Compact current context into a handoff document
   - Include skill suggestions for next session
   - Reference artifacts by path, don't duplicate content

For detailed instructions, see [Practical Guide](references/practical_guide.md).

## Code/Prompt Templates
```markdown
# Implementation Task

## Context
We're implementing [specific feature] in [file].

## Success Criteria
- [Testable condition 1]
- [Testable condition 2]

## Likely Code
```[language]
[probable code snippet]
```

## Rationalization Table
If you think... | Then...
---------------|-------
This is too small for tests| Write tests anyway - they help catch edge cases
This approach seems faster| Verify it meets all success criteria first
```

More templates in [Code Examples](references/code_examples.md).

## Best Practices
1. **Single Responsibility**: Each sub-agent should have one clear mission
2. **Clean Context**: Always use fresh sub-agents for reviews
3. **Explain Why**: Include intent explanations in skills
4. **Pressure Test**: Validate skills with multiple agents in edge cases
5. **Handoff Wisely**: Use handoff documents to maintain focus

## Common Pitfalls
- Letting agents retain context between tasks
- Giving agents conflicting mandates
- Auto-updating skills without vetting
- Not pressure testing skills

Full pitfalls list in [Common Pitfalls](references/common_pitfalls.md).

## Validation Steps
1. **Skill Testing**
   - Have multiple agents attempt the skill
   - Look for rationalizations of deviations
   - Update skill to address common rationalizations

2. **Workflow Testing**
   - Run complete workflow on small tasks
   - Verify each sub-agent stays focused
   - Check that reviews catch intentional errors

3. **Performance Testing**
   - Measure time to complete representative tasks
   - Compare error rates before/after skill updates
   - Monitor context window usage

## Reconciling Differences
The transcripts emphasize slightly different aspects:
- The first focuses on the psychology behind skills and orchestration
- The second provides concrete skill examples (handoff, prototype)

This skill combines both:
- Uses psychological principles in skill design
- Incorporates concrete skills like handoff and review
- Maintains the strict separation of concerns from the first transcript

## 📺 Source Videos

- [The Creator of Superpowers: Why Real Agentic Engineering Beats Vibe Coding](https://www.youtube.com/watch?v=wtzzWyrEY_A) — MLOps.community
- [New Skills! /handoff, /prototype, /review and /writing-* | Skills Changelog](https://www.youtube.com/watch?v=DNqsMXH6Eog) — Matt Pocock

**Difficulty**: Intermediate

## Prerequisites

- basic_prompting.md
- llm_fundamentals.md
