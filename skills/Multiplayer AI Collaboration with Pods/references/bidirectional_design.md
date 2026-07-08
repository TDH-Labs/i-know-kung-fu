# Bidirectional Design Principle

## Core Concept

Any feature must be equally accessible to both humans and agents. This creates symmetry in collaborative workflows and prevents artificial barriers between human and AI work.

## Implementation Guidelines

1. **API Parity**: 
   - All UI actions must have equivalent API endpoints
   - All API features must have UI representations
2. **State Visibility**:
   - Agents and humans see the same data structures
   - No hidden state or privileged interfaces
3. **Interaction Patterns**:
   - Humans can interrupt/take over agent workflows
   - Agents can request human input when stuck

## Example: Task Management

- **Human Actions**:
  - Create task via UI
  - Assign to agent
  - Mark complete
- **Agent Actions**:
  - Create task via API
  - Self-assign work
  - Update status
  - Spawn sub-tasks

## Pitfalls to Avoid

- Creating "agent-only" features that humans can't understand
- Building "human-only" workflows that agents can't participate in
- Assuming certain actions will always be human-driven or agent-driven

## Testing Approach

For every new feature:
1. Implement human interface
2. Simultaneously build agent API
3. Verify round-trip:
   - Human creates → agent modifies
   - Agent creates → human modifies