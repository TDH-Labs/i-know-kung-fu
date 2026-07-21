# Core Concepts

## Overview
This document outlines the core concepts behind the AI-driven software development workflow. Understanding these concepts is crucial for effectively using the skills provided.

## Key Concepts

### Grilling
Grilling involves asking the user detailed questions to gather comprehensive requirements. The `grill_me` skill ensures that questions are asked one at a time to avoid overwhelming the user.

### Specifications
Specifications (`to_spec` skill) are detailed documents that outline the technical and non-technical aspects of a project. They serve as the blueprint for development.

### Tickets
Tickets (`to_tickets` skill) break down the specification into manageable tasks. Each ticket represents a task that can be completed in a single agent session.

### Implementation
Implementation (`implement` skill) involves coding the features described in the tickets. Following Test-Driven Development (TDD) practices ensures high-quality code.

### Code Review
Code review (`code_review` skill) checks the implemented code for adherence to coding standards and ensures it faithfully implements the specification.

### Committing Work
Once the code review is complete, the work is committed to the current branch, marking the completion of the task.

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