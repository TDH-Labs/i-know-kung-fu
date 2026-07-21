# Core Concepts

## Skills Repository
A skills repository is a collection of AI-driven tools and scripts designed to assist in various coding tasks. These skills can be invoked by AI agents to perform specific functions, such as code generation, debugging, and documentation.

## AI Agents
AI agents are software entities that perform tasks based on the skills installed in the repository. They can be configured to work with different environments and tools, making them versatile for various coding projects.

## Context Window
The context window refers to the amount of information (measured in tokens) that an AI agent can process at once. Managing the context window is crucial for maintaining the agent's performance and avoiding issues like attention degradation.

## Installation and Setup
Installing and setting up the skills repository involves using Node.js and NPX to add the repository to your project. Configuration steps ensure that the skills are compatible with your preferred AI agent.

## Workflow
The main workflow involves refining an idea using the 'grill with docs' skill, converting it into a detailed specification, breaking down the specification into manageable tickets, and implementing these tickets using the AI agent. Code reviews are performed to ensure quality and adherence to standards.

## Best Practices
- **Context Window Management**: Keep the context window within the smart zone (around 140k tokens) to avoid attention degradation.
- **Skill Selection**: Choose skills that are well-documented and supported.
- **Regular Updates**: Stay updated with the latest skills and improvements.

## Common Pitfalls
- **Overloading Context Window**: Exceeding the context window limit can lead to hallucinations and degraded performance.
- **Incomplete Setup**: Ensure all setup steps are completed to avoid runtime errors.

## Validation and Testing
- **Specification Check**: Ensure the specification matches the initial idea.
- **Ticket Verification**: Verify that tickets are manageable and within the context window.
- **Code Review**: Perform thorough code reviews to catch any issues.