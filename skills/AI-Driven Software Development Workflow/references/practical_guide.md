# Practical Guide

## Overview
This guide provides practical steps for implementing the AI-driven software development workflow. Follow these steps to ensure a smooth and efficient development process.

## Step-by-Step Workflow
1. **Grill the User**: Start by grilling the user to gather detailed requirements. Use the `grill_me` skill to ask one question at a time and ensure a shared understanding before proceeding.
2. **Create Specifications**: Convert the gathered requirements into a detailed specification using the `to_spec` skill. This document should outline the technical and non-technical aspects of the project.
3. **Break Down Tasks**: Use the `to_tickets` skill to break down the specification into individual tickets. Each ticket should represent a manageable task that can be completed in a single agent session.
4. **Implement Features**: Implement each ticket using the `implement` skill. Follow Test-Driven Development (TDD) practices where possible and run type checking and tests regularly.
5. **Code Review**: Review the implemented code using the `code_review` skill. Check for adherence to coding standards and ensure the code faithfully implements the originating specification.
6. **Commit Work**: Once the code review is complete, commit the work to the current branch.

## Code Snippets
```javascript
// Example of using the implement skill
const implementSkill = require('skills/implement');
implementSkill.execute({
  spec: 'path/to/spec.md',
  ticket: 'path/to/ticket.md',
  tdd: true,
  typeChecking: true,
  testSuite: true
});
```

## Best Practices
- **Ask One Question at a Time**: Avoid overwhelming the user with multiple questions simultaneously.
- **Use TDD**: Implement features using Test-Driven Development to ensure code quality.
- **Regular Type Checking**: Run type checking regularly to catch errors early.
- **Full Test Suite**: Run the full test suite at the end of the implementation to ensure all tests pass.

## Common Pitfalls
- **Multiple Questions**: Asking multiple questions at once can confuse the user and lead to incomplete or incorrect requirements.
- **Skipping Code Review**: Skipping the code review step can result in code that does not adhere to standards or fully implement the specification.
- **Ignoring TDD**: Not using TDD can lead to poorly tested code and increased technical debt.

## Validation and Testing
- **Shared Understanding**: Ensure the user confirms a shared understanding before proceeding with implementation.
- **Code Standards**: Verify that the code adheres to the repository's documented coding standards.
- **Specification Adherence**: Check that the code faithfully implements the originating specification.