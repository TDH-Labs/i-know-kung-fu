# Common Pitfalls & Solutions

## Context Leakage
**Problem**: Agents work in isolation, losing context between steps.
- *Example*: Codex fixes bug but doesn't tell Claude about UI impacts.
**Solution**:
- Require ALL context in tickets
- Use template: "Background:", "Related:", "Dependencies:"

## Ambiguous Handoffs
**Problem**: Unclear when work transitions between agents/humans.
- *Example*: Support agent escalates without customer history.
**Solution**:
- Explicit "Definition of Done" in every ticket
- Standard status transitions:
  - Agent Working → Needs Input (blocked)
  → Agent Done

## Silent Failures
**Problem**: Agents fail without notification.
- *Example*: Codex hits API error but ticket stays 'Working'.
**Solution**:
- Implement heartbeat checks
- Timeout after [interval] if no updates
- Escalate to 'needs-input' on errors

## Overloaded Tickets
**Problem**: Single ticket contains multiple workstreams.
- *Example*: "Redesign UI + fix backend + update docs"
**Solution**:
- One discrete action per ticket
- Use "Epic" tickets to group related work
- Enforce title format: "[Verb] [Noun]" (e.g., "Update login CSS")

## Audit Trail Gaps
**Problem**: Decisions get lost in private chats.
- *Example*: Paint color chosen in Claude chat but not recorded.
**Solution**:
- Ban side-channel communication
- Require ALL outputs as ticket attachments
- Use template:
  "Decision: [ ]
  Rationale: [ ]
  Alternatives: [ ]"

## Tool Limitations
**Problem**: Queue system lacks needed features.
- *Example*: Jira doesn't show agent statuses clearly.
**Solution**:
- Use Linear (best for Open Engine)
- Or extend with custom fields:
  - "Agent Owner"
  - "Last Agent Activity"
  - "Blocked Reason"