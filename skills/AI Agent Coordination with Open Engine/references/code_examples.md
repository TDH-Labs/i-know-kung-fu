# Code Examples & Prompt Templates

## Agent Setup Prompt
```markdown
You are now integrated with Open Engine. Follow these protocols:

1. Every [15 minutes], check Linear queue for:
   - Issues assigned to you
   - Labeled 'agent-instructions'
2. To claim a task:
   - Move to 'Agent Working'
   - Comment: "[AgentName] claimed this task at [Time]. Expected completion: [ETA]."
3. When working:
   - Keep all context in this ticket
   - If blocked, move to 'needs-input' and ask EXACT question
4. When done:
   - Attach ALL outputs
   - Move to 'Agent Done'
   - Comment: "Completed: [Summary]. Next steps: [ ]."
```

## Task Creation Template
```markdown
**Title**: [Clear action phrase]

**Background**:
- [Relevant context]
- [Attached files/links]

**Constraints**:
- [Limitations/requirements]
- [Avoid X]

**Definition of Done**:
- [Deliverable 1]
- [Review criteria]
- [Approval needed?]
```

## Delegation Between Agents
```python
# Example: Codex delegating to Claude
create_ticket(
  title="Review UI for new dashboard",
  assignee="claude-agent",
  labels=["agent-instructions"],
  description=f"""
  Background: New dashboard implemented (see attached specs).
  Constraints: Mobile-first, comply with styleguide.pdf
  Done: Markup review + suggested changes in Figma
  """,
  attachments=["specs.md", "styleguide.pdf"]
)
```

## Smoke Test
1. Create test ticket: "Say hello from the queue"
2. Assign to agent
3. Verify agent:
   - Claims ticket
   - Moves status
   - Leaves receipt
   - Completes task