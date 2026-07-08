# Flocking Algorithm for AI Coordination

## Core Principles

The flocking algorithm provides a framework for autonomous coordination between multiple agents (or between agents and humans) through three simple rules:

1. **Local Separation**: Small repulsive forces that prevent crowding (e.g., trust-based delegation where humans don't micromanage)
2. **Distant Attraction**: Pulling forces toward shared objectives (e.g., writing culture that surfaces related work)
3. **Alignment**: Common direction/orientation (e.g., clear company vision)

## Implementation in AI Systems

- **Writing Culture as Attraction**: At Stripe, mailing lists served as the 'distant attraction' mechanism by exposing related work across teams
- **Trust as Separation**: When an agent/human claims responsibility for a task, others stop worrying about it
- **Vision as Alignment**: Clear, simple mission statements ("Dev API for payments") create natural alignment

## Technical Considerations

- Requires shared state visibility (like Dust's pod file system)
- Needs mechanisms for discovering related work (automated or manual)
- Must maintain bidirectional accessibility (all features available to both humans and agents)

## Example Patterns

- Weekly team meeting automation where agents:
  1. Create individual slide sessions
  2. Ping responsible humans
  3. Consolidate outputs
- Project pods with shared tasks that both humans and agents can create/edit/complete