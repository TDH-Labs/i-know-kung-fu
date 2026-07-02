---
description: Compact the current conversation into a handoff document for another
  agent to pick up, summarizing the conversation and suggesting next steps.
name: Handoff Skill
tags:
- handoff
- agent
- context
- summary
- transfer
---

# Handoff Skill

> Compact the current conversation into a handoff document for another agent to pick up, summarizing the conversation and suggesting next steps.

## Overview
The Handoff Skill enables smooth transitions between AI agents by creating a temporary summary document. This is particularly useful when:
- The current context window is becoming too large
- A different type of agent would be better suited for the next phase
- You need to parallelize work across multiple agents

For core concepts, see [Core Concepts](references/core_concepts.md).

## Step-by-Step Workflow
1. **Initiate Handoff**: Trigger the skill with `/handoff` or `/handoff "focus description"` if you want to specify the next session's focus.
2. **Document Creation**: The agent will:
   - Summarize the current conversation
   - Capture the current state of work
   - Suggest next steps and recommended skills
   - Reference relevant artifacts
3. **File Handling**: The document is saved to a temporary location (see [Practical Guide](references/practical_guide.md) for details).
4. **Transfer**: The path to the document is provided for use in a new agent session.
5. **Continuation**: The new agent loads the handoff document and continues the work.

## Best Practices
1. **Content Selection**:
   - Focus on key decisions and current state
   - Avoid duplicating content available in other artifacts
   - Include enough context for effective continuation
2. **Skill Suggestions**:
   - Recommend skills that match the next phase of work
   - Consider the 'vibe' of the current session
3. **Temporary Nature**:
   - Remember these are transitional documents
   - Important information should be saved elsewhere

## Common Pitfalls
1. **Over-summarizing**: Losing important nuances in the handoff
2. **Under-summarizing**: Creating documents that are too verbose
3. **Missing References**: Forgetting to link to relevant artifacts
4. **Skill Mismatch**: Suggesting inappropriate skills for continuation

## Validation Steps
1. **Content Check**: Verify the document contains:
   - Clear summary
   - Current state
   - Next steps
   - Skill suggestions
   - Artifact references
2. **File Check**: Confirm the file exists at the specified path
3. **Continuation Test**: Start a new agent with the document and verify it can continue the work effectively

For complete code examples and templates, see [Code Examples](references/code_examples.md).

## 📺 Source Videos

- [New Skills! /handoff, /prototype, /review and /writing-* | Skills Changelog](https://www.youtube.com/watch?v=DNqsMXH6Eog) — Matt Pocock

**Difficulty**: Intermediate

## Prerequisites

- basic understanding of agent workflows
- familiarity with temporary file handling
