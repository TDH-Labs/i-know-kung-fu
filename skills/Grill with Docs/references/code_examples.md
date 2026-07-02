# Code Examples

## Context.md Example
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

## ADR Example
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

## Prompt Template
```markdown
# Grill with Docs Prompt

## Session Start
Start a grilling session to resolve ambiguities and dependencies in the code.

## Definitions
Define key terms and entities in the domain.

## Relationships
Document the relationships between entities.

## Decisions
Capture non-obvious decisions in ADRs.

## Updates
Continuously update the context.md and ADRs as new terms and decisions are made.
```