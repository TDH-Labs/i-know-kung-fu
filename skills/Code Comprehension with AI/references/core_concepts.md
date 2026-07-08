# Core Concepts of AI-Assisted Code Comprehension

## The Comprehension-Generation Paradox

The transcript reveals a surprising insight: 67% of AI usage was for comprehension tasks, while only 2% was for code generation. This challenges the common assumption that AI's primary value is in generating code. Comprehension includes:

- Understanding architecture and dependencies
- Tracing feature implementations
- Learning codebase conventions
- Investigating historical changes

## Exploration Modes Framework

Priscila's 'Catch Me Up' skill structures comprehension into six exploration modes:

1. **Architecture**: High-level system structure and component relationships
2. **Convention**: Codebase-specific patterns and style guidelines
3. **Feature Trace**: How specific features are implemented across the system
4. **Syntax**: Language/framework-specific implementation details
5. **Testing**: Test coverage and validation approaches
6. **History**: Evolution of components and rationale for changes

## Mental Model Alignment

Critical to success is aligning your mental model with the AI's understanding:

- Verify comprehension before acting on AI outputs
- Cross-reference multiple information sources
- Treat AI as a 'senior engineer' who needs context

## Quality Over Speed

In production environments (like Sentry's 15+ year old codebase):

- Never ship code you don't fully understand
- Use AI to accelerate understanding, not bypass it
- Maintain high standards despite faster iteration cycles