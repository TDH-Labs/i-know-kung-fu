---
description: A strict, ambitious code review skill focused on structural improvements,
  maintainability, and eliminating complexity through aggressive refactoring and code
  judo moves.
name: Thermonuclear Code Quality Review
tags:
- code review
- refactoring
- maintainability
- code quality
- TypeScript
---

# Thermonuclear Code Quality Review

> A strict, ambitious code review skill focused on structural improvements, maintainability, and eliminating complexity through aggressive refactoring and code judo moves.

## Overview
This skill implements an extremely rigorous code review process focused on structural quality and maintainability. Key aspects:
- **Ambitious refactoring** ("code judo" moves)
- **Strict size limits** (1K lines/file maximum)
- **Type safety enforcement** (no any/unknown)

See [Core Concepts](references/core_concepts.md) for philosophical foundations.

## Workflow
1. **Initial Scan**
   - Run size analysis on all changed files
   - Flag any type safety violations immediately

2. **Deep Review**
   - For each file, apply the [Workflow Guide](references/workflow_guide.md)
   - Generate specific refactor proposals

3. **Decision Making**
   - Use severity-based prioritization
   - Reject PRs that degrade codebase health

## Best Practices
- **Be aggressive** with structural suggestions (transcript example: deleting 20+ lines via abstraction)
- **Focus on types** (transcript example: converting scattered if-checks to type-driven design)
- **Keep files small** (1K line absolute maximum)

## Pitfalls
1. **False positives** (transcript example: misunderstanding template args system)
   - Mitigation: Include domain context in review

2. **Over-optimization**
   - Rule: "Don't micro-optimize unless proven bottleneck"

3. **Test blindness**
   - Always verify test coverage for new abstractions

## Validation
1. For each recommendation:
   - Verify behavior preservation
   - Check actual reduction in complexity metrics
   - Confirm type safety improvements

2. Sample validation questions:
   - Did we eliminate any `any` types?
   - Is the file structure now flatter?
   - Are there fewer concepts per function?

Use [Prompt Templates](references/prompt_templates.md) for consistent review language.

## 📺 Source Videos

- [Can Cursor's HARDCORE Review Skill Stop The Slop?](https://www.youtube.com/watch?v=mh5XZ-L5SFQ) — Matt Pocock

**Difficulty**: Advanced

## Prerequisites

- Understanding of code architecture
- Familiarity with TypeScript/JavaScript
- Experience with code review processes
