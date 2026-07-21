---
description: A comprehensive guide to setting up and using Matt Pocock's AI coding
  skills repository for efficient and effective code development. This skill covers
  installation, configuration, and the main workflow from idea to implementation.
name: AI Coding Workflow with Matt Pocock's Skills
tags:
- AI coding
- Matt Pocock
- skills repository
- workflow
- implementation
---

# AI Coding Workflow with Matt Pocock's Skills

> A comprehensive guide to setting up and using Matt Pocock's AI coding skills repository for efficient and effective code development. This skill covers installation, configuration, and the main workflow from idea to implementation.

## Overview
This skill provides a step-by-step guide to using Matt Pocock's AI coding skills repository. The repository is designed to streamline the coding process from idea to implementation, leveraging AI agents to handle various tasks efficiently.

## Core Concepts
Before diving into the workflow, it's essential to understand the core concepts:
- **Skills Repository**: A collection of AI-driven tools and scripts that assist in coding tasks.
- **AI Agents**: Software agents that perform specific tasks based on the skills installed.
- **Context Window**: The amount of information (tokens) that an AI agent can process at once.

For a deeper dive into these concepts, refer to [Core Concepts](references/core_concepts.md).

## Step-by-Step Workflow
1. **Installation**: Install the skills repository using Node.js and NPX.
   ```bash
   npx skills@latest add mattpocock/skills
   ```
2. **Configuration**: Configure the skills to work with your preferred AI agent.
   ```bash
   # Follow the CLI prompts to select skills and agent
   ```
3. **Setup**: Run the setup command to configure the repository.
   ```bash
   setup_matt_pocock_skills
   ```
4. **Grill with Docs**: Use the 'grill with docs' skill to refine your idea.
   ```bash
   grill_with_docs "I would like to remove most of the internal tooling on this CLI to make it just only public-facing."
   ```
5. **Specification**: Convert the refined idea into a detailed specification.
   ```bash
   to_spec
   ```
6. **Tickets**: Break down the specification into manageable tickets.
   ```bash
   to_tickets
   ```
7. **Implementation**: Implement the tickets using the AI agent.
   ```bash
   implement
   ```
8. **Code Review**: Perform a code review to ensure quality.
   ```bash
   code_review
   ```

For detailed examples and code snippets, see [Code Examples](references/code_examples.md).

## Best Practices
- **Context Window Management**: Keep the context window within the smart zone (around 140k tokens) to avoid attention degradation.
- **Skill Selection**: Choose skills that are well-documented and supported.
- **Regular Updates**: Stay updated with the latest skills and improvements.

## Common Pitfalls
- **Overloading Context Window**: Exceeding the context window limit can lead to hallucinations and degraded performance.
- **Incomplete Setup**: Ensure all setup steps are completed to avoid runtime errors.

For more on best practices and pitfalls, refer to [Practical Guide](references/practical_guide.md).

## Validation and Testing
- **Specification Check**: Ensure the specification matches the initial idea.
- **Ticket Verification**: Verify that tickets are manageable and within the context window.
- **Code Review**: Perform thorough code reviews to catch any issues.

## Conclusion
This skill provides a robust framework for leveraging AI in your coding workflow. By following the steps and best practices outlined, you can enhance your productivity and code quality.

For further reading, check out the [Core Concepts](references/core_concepts.md), [Practical Guide](references/practical_guide.md), and [Code Examples](references/code_examples.md) documents.

## 📺 Source Videos

- [mattpocock/skills: A complete AI Coding workflow, end-to-end](https://www.youtube.com/watch?v=M6mYodf0dJM) — Matt Pocock

**Difficulty**: Intermediate

## Prerequisites

- Basic knowledge of Node.js
- Familiarity with command line interfaces
- Understanding of AI agents
