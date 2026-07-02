# Practical Guide to Agentic Development

This guide provides step-by-step instructions for implementing agentic development workflows using skills.

## 1. Brainstorming
Start with the brainstorming skill to extract clear requirements from the user. Use psychological tricks to help users articulate what they actually want, not just what they think they want.

## 2. Planning
Convert the brainstormed ideas into a detailed plan. The plan should:
- Break the task into tiny, testable steps
- Specify files to touch
- Define success criteria
- Include likely code snippets

## 3. Implementation
Use sub-agents for implementation. Each sub-agent should:
- Receive only the context needed for its specific task
- Return results to the orchestrator
- Be disposable (no persistent state)

## 4. Review
Review tasks should be performed by fresh sub-agents with no prior context. Reviews should check:
- Spec compliance (did it do what was asked?)
- Code quality (is it well-written?)

## 5. Handoff
Use the handoff skill to transfer context between agents. The handoff document should:
- Summarize the current conversation
- Suggest skills for the next session
- Reference artifacts by path/URL, not by duplicating content

## Example Workflow
1. User describes a feature in a brainstorming session.
2. Orchestrator creates a plan with 10 small steps.
3. For each step, an implementer sub-agent is spawned, completes the task, and reports back.
4. A fresh reviewer sub-agent checks each step.
5. If changes are needed, the orchestrator sends the implementer back to fix.
6. Once all steps are done, a final review is performed.

For code examples, see [Code Examples](references/code_examples.md).