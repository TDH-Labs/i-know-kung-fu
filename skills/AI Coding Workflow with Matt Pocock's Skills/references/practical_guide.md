# Practical Guide

## Installation
To install Matt Pocock's skills repository, use the following command:
```bash
npx skills@latest add mattpocock/skills
```
This command assumes you have Node.js installed and uses NPX to run the skills.sh command line installer from Vercel.

## Configuration
After installation, configure the skills to work with your preferred AI agent. Follow the CLI prompts to select the skills and agent.

## Setup
Run the setup command to configure the repository:
```bash
setup_matt_pocock_skills
```
This command sets up the repository to use an issue tracker, triage labels, and domain documentation.

## Grill with Docs
Use the 'grill with docs' skill to refine your idea:
```bash
grill_with_docs "I would like to remove most of the internal tooling on this CLI to make it just only public-facing."
```
This skill interviews you to sharpen the idea and records what it learns in context.md and ADRs.

## Specification
Convert the refined idea into a detailed specification:
```bash
to_spec
```
This command compresses the discussion into a document that can be used later.

## Tickets
Break down the specification into manageable tickets:
```bash
to_tickets
```
Each ticket is supposed to be the size of a single context window or a single smart zone.

## Implementation
Implement the tickets using the AI agent:
```bash
implement
```
This command runs the code review as part of the implementation process.

## Code Review
Perform a code review to ensure quality:
```bash
code_review
```
This command compares the work done against the original spec and checks against the standards documentation.

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