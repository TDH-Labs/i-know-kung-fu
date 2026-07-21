# Practical Implementation Guide

## Queue System Setup
1. **Choose your platform**:
   - Linear (free tier works)
   - Jira
   - Custom Kanban
2. **Create standard labels**:
   - `agent-instructions` (tasks for AI)
   - `needs-input` (blocked tasks)
   - `agent-done` (completed work)

## Agent Configuration
For each AI tool (Claude/Codex/etc.), create skills that:
1. **Check assigned queue** every [interval]
2. **Claim tasks** by:
   - Moving to 'Agent Working'
   - Leaving "Claimed by [Agent]" comment
3. **Process work** with:
   - All source materials attached
   - Clear stopping points
4. **Complete tasks** by:
   - Moving to 'Agent Done'
   - Attaching outputs
   - Noting next steps

## Human-Agent Collaboration
1. **Creating tasks**:
   - Include: "Background:", "Constraints:", "Definition of Done:"
   - Example: "Background: Client call transcript attached. Constraints: Don't promise timelines. Done: Draft email + approval request."
2. **Reviewing work**:
   - Check 'Agent Done' queue
   - Verify attached artifacts
   - Provide feedback via ticket comments

## Team Coordination
1. **Cross-agent delegation**:
   - Agent A creates ticket for Agent B
   - Includes all context needed
   - Labels as `agent-instructions`
2. **Audit trails**:
   - All communication stays in tickets
   - No context lost in private chats

Example Workflow:
1. Human creates ticket: "Redesign login flow - mobile first"
2. Codex claims it, implements backend
3. Codex creates new ticket: "Review UI for new login" → Claude
4. Claude provides feedback in ticket
5. System notifies human for final approval