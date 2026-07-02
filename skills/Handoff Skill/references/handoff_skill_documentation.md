# Handoff Skill Documentation

## Overview
The Handoff Skill allows an AI agent to compact the current conversation into a handoff document for another agent to pick up. This ensures seamless continuation of work across different agent sessions.

## Usage
To use the Handoff Skill, simply initiate the handoff process by instructing the agent to create a handoff document. The agent will summarize the conversation, suggest relevant skills, and write the document to a temporary file.

## Examples
```python
# Example command to initiate handoff
handoff_command = "/handoff"

# Example prompt for summarizing conversation
summary_prompt = "Summarize the current conversation for handoff to another agent."
```

## Troubleshooting
- **Incomplete Summary**: Ensure the summary captures all relevant details.
- **File Handling Errors**: Always read the file before writing to avoid errors in Claude.
- **Redundant Content**: Reference existing artifacts to avoid duplication.