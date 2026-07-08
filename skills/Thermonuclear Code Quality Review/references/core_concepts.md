# Core Concepts of Thermonuclear Code Review

## Code Judo

The principle of finding structural improvements that dramatically simplify code by reframing problems. Examples from transcript:
- Replacing scattered if-statements with type-driven logic
- Creating generic functions to eliminate 20+ lines of boilerplate
- Splitting large files (>1K lines) into focused modules

## Structural Simplification

Key metrics to enforce:
1. File size limits (1K lines maximum)
2. Abstraction quality (dedicated helpers over inline logic)
3. Type boundaries (eliminate any/unknown/unnecessary optionality)

## Review Priorities

1. Blocking structural issues (file size violations, spaghetti growth)
2. Type safety violations
3. Duplication and boilerplate
4. Legibility concerns

## Non-Negotiables

- Never let a file grow beyond 1K lines without exceptional justification
- Treat nested conditionals as design problems requiring abstraction
- Prefer boring, direct code over clever solutions
- Challenge all type safety compromises (any, unknown, excessive casting)