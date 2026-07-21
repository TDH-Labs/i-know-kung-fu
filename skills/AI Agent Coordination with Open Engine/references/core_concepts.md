# Core Concepts of Open Engine

## The Handoff Problem
Modern AI users often employ multiple specialized agents (Claude for design, Codex for engineering, etc.), but these tools don't communicate. Humans become the 'hallway' between disconnected systems, manually copying context between:
- Different AI tools
- Team members' agents
- Support/product workflows
- Calendar/coding systems

## Queue-Based Coordination
Open Engine solves this by:
1. **Centralizing work** in a shared queue (Linear/Jira/etc.)
2. **Standardizing tickets** with:
   - Clear ownership (human or agent)
   - Required background context
   - Definition of done
   - Explicit handoff points
3. **Agent protocols** for:
   - Claiming tasks
   - Moving statuses
   - Leaving audit trails

## Key Distinctions
- **Prompt vs Work Mode**: 
  - Prompt: "Write a follow-up email"
  - Work: "Here's transcript + constraints. Draft follow-up, flag for review, leave notes"
- **Output vs Work**: 
  - Output is what AI returns
  - Work is reviewable, actionable artifacts

## System Components
1. Queue system (Linear recommended)
2. Setup skill (configuring agents)
3. Status skill (tracking progress)
4. Execution skill (processing tasks)
5. Smoke test (validation)

Example: When Codex finishes a coding task, it:
1. Moves ticket to 'Agent Done'
2. Attaches changed files
3. Notes remaining questions
4. Triggers next agent (e.g., Claude for UI review)