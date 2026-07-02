---
description: A skill for AI-assisted development that combines the Grill Me technique
  with domain-driven design principles to establish and maintain a shared language
  between the developer and the AI. This skill leverages a context.md file to document
  shared language and an architectural decision record (ADR) to capture non-obvious
  decisions, ensuring concise and aligned communication.
name: Grill with Docs
tags:
- AI-assisted development
- domain-driven design
- shared language
- context.md
- ADR
---

# Grill with Docs

> A skill for AI-assisted development that combines the Grill Me technique with domain-driven design principles to establish and maintain a shared language between the developer and the AI. This skill leverages a context.md file to document shared language and an architectural decision record (ADR) to capture non-obvious decisions, ensuring concise and aligned communication.

## Overview

The Grill with Docs skill is designed to enhance AI-assisted development by establishing a shared language between the developer and the AI. This skill builds on the Grill Me technique, which involves the AI interviewing the developer to resolve ambiguities and dependencies. Grill with Docs extends this by incorporating domain-driven design principles, specifically the concept of ubiquitous language, to create a context.md file that documents the shared language used in the codebase. Additionally, it uses architectural decision records (ADRs) to capture non-obvious decisions that are hard to reverse.

## Step-by-Step Workflow

1. **Initialize the Session**: Start a grilling session with the AI, ensuring that the context.md file is present in the repository root.
2. **Define Shared Language**: During the session, the AI will challenge fuzzy language and ask for definitions of terms. Document these definitions in the context.md file.
3. **Capture Non-Obvious Decisions**: When encountering decisions that are hard to reverse, create an ADR to document the rationale and consequences.
4. **Update Context.md**: Continuously update the context.md file as new terms and definitions are agreed upon.
5. **Review and Refine**: Periodically review the context.md and ADRs to ensure they remain accurate and useful.

## Code Snippets and Prompt Templates

### Context.md Template
```markdown
# Context Documentation

## Entities
- **Course**: A structured series of lessons.
- **Lesson**: A single unit of instruction within a course.
- **Standalone Video**: A video not connected to a lesson or course.

## Relationships
- **Course** has many **Lessons**.
- **Standalone Video** can be associated with a **Pitch**.
```

### ADR Template
```markdown
# Architectural Decision Record

## Title
Use of Standalone Videos

## Status
Proposed

## Context
We need to define how standalone videos interact with pitches.

## Decision
Standalone videos can be associated with multiple pitches.

## Consequences
This allows for flexible video packaging but may complicate the UI.
```

## Best Practices and Common Pitfalls

### Best Practices
- **Consistent Language**: Ensure that all terms used in the codebase are defined in the context.md file.
- **Document Early**: Start documenting shared language and decisions early in the project to avoid confusion later.
- **Regular Reviews**: Periodically review and update the context.md and ADRs to keep them relevant.

### Common Pitfalls
- **Verbose Definitions**: Avoid overly verbose definitions that can confuse rather than clarify.
- **Undocumented Decisions**: Failing to document non-obvious decisions can lead to misunderstandings and technical debt.
- **Over-Documentation**: While documentation is important, avoid creating unnecessary documents that can clutter the repository.

## Validation and Testing Steps

1. **Check Context.md**: Verify that all terms used in the codebase are defined in the context.md file.
2. **Review ADRs**: Ensure that all non-obvious decisions are documented in ADRs.
3. **AI Alignment**: Test the AI's responses to ensure they align with the definitions in the context.md file.
4. **Code Consistency**: Check that variable names and file names in the codebase align with the shared language documented in context.md.

## References

- [Core Concepts](references/core_concepts.md)
- [Practical Guide](references/practical_guide.md)
- [Code Examples](references/code_examples.md)
- [Common Pitfalls](references/common_pitfalls.md)

## 📺 Source Videos

- [I stopped using /grill-me for coding. Here’s what I use instead:](https://www.youtube.com/watch?v=6BB6exR8Zd8) — Matt Pocock

**Difficulty**: Intermediate

## Prerequisites

- Basic understanding of domain-driven design
- Familiarity with markdown files
- Experience with AI-assisted coding
