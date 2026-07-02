---
description: A systematic approach to refactoring and improving codebase architecture
  by identifying and deepening shallow modules, improving locality and leverage, and
  establishing clear seams and interfaces.
name: Improve Codebase Architecture
tags:
- refactoring
- codebase architecture
- deep modules
- interfaces
- seams
- adapters
---

# Improve Codebase Architecture

> A systematic approach to refactoring and improving codebase architecture by identifying and deepening shallow modules, improving locality and leverage, and establishing clear seams and interfaces.

## Overview
This skill enables you to systematically improve codebase architecture by identifying and refactoring shallow modules into deep modules with clear interfaces. The process increases locality (changes concentrate in one place) and leverage (more capability per interface). Learn the core concepts in [Core Concepts](references/core_concepts.md).

## Step-by-Step Workflow

1. **Codebase Exploration**
   - Have AI scan the codebase to identify architectural issues
   - Look for shallow modules, duplicate implementations, and poor interfaces
   - Document findings (see [Practical Guide](references/practical_guide.md) for patterns)

2. **Candidate Selection**
   - Review identified candidates with strategic perspective
   - Prioritize based on impact and effort
   - Example: Choose duplicate implementations first

3. **Solution Design**
   - For each candidate:
     a. Define a clear module interface
     b. Consolidate implementations
     c. Improve locality by co-locating related code
   - Use AI to propose designs (examples in [Code Examples](references/code_examples.md))

4. **Grilling Session**
   - Engage in Q&A with AI to refine the solution
   - Address edge cases and implementation details
   - Make strategic decisions about interface design

5. **Implementation**
   - Create GitHub issues for AFK agents to implement
   - Or implement changes directly with AI assistance

6. **Testing**
   - Write tests at module seams
   - Verify interface contracts
   - Ensure adapters work in all contexts

## Best Practices
1. **Regular Execution**: Run this skill every few days in active codebases
2. **Strategic Oversight**: You must make the high-level decisions
3. **Deep Over Shallow**: Always prefer modules that hide complexity
4. **Clear Interfaces**: Document interface contracts thoroughly

## Common Pitfalls
1. **Over-automation**: Trying to run this fully AFK (requires human judgment)
2. **Interface Bleed**: Letting implementation details leak into interfaces
3. **Premature Optimization**: Deepening modules that don't need it
4. **Testing Neglect**: Forgetting to establish tests at seams

## Validation
1. **Metrics**: Count of shallow → deep module conversions
2. **Testing**: Verify modules can be tested in isolation
3. **Change Impact**: Measure how changes affect other parts of system
4. **Leverage**: Assess capability gained per interface unit

Remember: The AI is your tactical partner, but you must provide strategic direction. Combine this skill with testing practices for maximum impact on legacy codebases.

## 📺 Source Videos

- [How To De-Slop A Codebase Ruined By AI (with one skill)](https://www.youtube.com/watch?v=3MP8D-mdheA) — AI Coding

**Difficulty**: Intermediate

## Prerequisites

- Basic understanding of software architecture
- Familiarity with modular programming
- Experience with code refactoring
