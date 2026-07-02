# Code Examples and Prompt Templates

## Handoff Skill Template
```markdown
# Handoff

We're going to compact the current conversation into a handoff document for another agent to pick up.

## Instructions
1. Write a handoff document summarizing the current conversation so a fresh agent can continue the work.
2. Save it to a path produced by `mktemp handoff-XXXXXX.md`.
3. Read the file before you write to it (Claude requires this).
4. Suggest the skills to be used (if any) by the next session.
5. Do not duplicate content already captured in other artifacts - reference them by path or URL instead.
6. If the user passed arguments, treat them as a description of what the next session will focus on and tailor the doc accordingly.
```

## Prototyping Skill Template
```markdown
# Prototype

Build a throwaway prototype to explore design decisions.

## When to Use
- When you have unknown unknowns that can only be figured out by looking at code
- For UI variations (generates multiple radically different options)
- For complex state logic (build a tiny interactive terminal app)

## Instructions
1. Identify the key uncertainty to prototype.
2. Build a minimal prototype to explore it.
3. For UI: create multiple variations with a selector to toggle between them.
4. For logic: build an interactive terminal app that steps through state changes.
5. Get user feedback and iterate before handing off to implementation.
```

## Review Skill Template
```markdown
# Review

Perform a code review focusing on two axes:
1. Standards: Does the diff follow the repo's coding standards?
2. Spec: Does the diff faithfully implement the original issue/PRD?

## Instructions
1. Spawn two parallel sub-agents:
   - Standards Reviewer: Checks against coding standards
   - Spec Reviewer: Verifies implementation matches requirements
2. Combine their feedback into a single report.
3. Flag any deviations from either axis.
4. Do not fix the code - return feedback to the implementer.
```

For more core concepts, see [Core Concepts](references/core_concepts.md).