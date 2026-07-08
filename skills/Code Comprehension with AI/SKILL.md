---
description: A systematic approach to using AI for understanding complex codebases,
  inspired by Priscila Andre de Oliveira's workflow at Sentry. Focuses on comprehension
  over generation, with structured exploration modes and prompt engineering techniques.
name: Code Comprehension with AI
tags:
- code comprehension
- prompt engineering
- large codebases
- AI-assisted development
- Claude
---

# Code Comprehension with AI

> A systematic approach to using AI for understanding complex codebases, inspired by Priscila Andre de Oliveira's workflow at Sentry. Focuses on comprehension over generation, with structured exploration modes and prompt engineering techniques.

## Overview

This skill transforms how you understand complex codebases by systemizing AI-assisted comprehension. Based on Priscila Andre de Oliveira's experience at Sentry (a 15+ year old codebase with 100 daily PRs), it focuses on structured exploration rather than just code generation. See [Core Concepts](references/core_concepts.md) for philosophical foundations.

## Step-by-Step Workflow

1. **Initialize Context**
   - Provide role, project, and specific needs
   - Example: "I'm a frontend engineer new to the checkout flow"

2. **Select Exploration Mode** (from [Core Concepts](references/core_concepts.md))
   - Architecture for system overview
   - Convention for style/patterns
   - Feature Trace for implementation details
   - History for change context

3. **Formulate Precise Prompt**
   - Use templates from [Prompt Examples](references/prompt_examples.md)
   - Include format preferences (tables, diagrams)

4. **Verify and Cross-Check**
   - Spot-check against actual code
   - Compare multiple AI responses
   - Consult documentation where available

5. **Iterate with Depth**
   - Drill down from architecture to specifics
   - Chain related questions for comprehensive understanding

6. **Document Insights**
   - Save effective prompts
   - Record learned concepts
   - Share with team members

## Best Practices

1. **Prioritize Comprehension**
   - Spend 70% effort understanding, 30% generating (per transcript findings)
   - Never implement without full comprehension

2. **Structure Your Approach**
   - Use the six exploration modes systematically
   - Follow the [Practical Guide](references/practical_guide.md) workflow

3. **Validate Rigorously**
   - Check AI outputs against:
     - Code comments
     - Commit messages
     - Team documentation

## Common Pitfalls

1. **Assuming AI Understands Context**
   - Pitfall: Asking vague questions without boundaries
   - Solution: Provide explicit constraints and examples

2. **Skipping Verification**
   - Pitfall: Trusting AI outputs without spot-checking
   - Solution: Always sample-check against actual code

3. **Generation Over Comprehension**
   - Pitfall: Jumping to code changes without deep understanding
   - Solution: Follow the 70/30 ratio from the transcript

## Validation Steps

1. **Cross-Reference Testing**
   - Ask the same question in different ways
   - Compare responses for consistency

2. **Real-World Verification**
   - Manually verify sample points in code
   - Check against recent PRs/commits

3. **Peer Review**
   - Share AI-generated understanding with teammates
   - Confirm accuracy with domain experts

## Implementation Examples

See [Prompt Examples](references/prompt_examples.md) for ready-to-use templates covering:
- New contributor onboarding
- PR review assistance
- Incident investigation
- Convention verification

## 📺 Source Videos

- [The AI Skill I Rely On Daily — Priscila Andre de Oliveira, Sentry](https://www.youtube.com/watch?v=li0SaBt9RDM) — AI Engineer

**Difficulty**: Intermediate

## Prerequisites

- Basic familiarity with codebases and version control
- Experience with AI chat interfaces
- Understanding of software architecture concepts
