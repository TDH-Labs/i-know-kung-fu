# Core Concepts of Agent Maintenance

## The Harness (Workbench) Concept

The harness is the controlled environment surrounding your AI agent that defines:
- What data sources it can access
- What tools it can use
- What actions it's permitted to take
- What proof requirements exist for its outputs
- What human review steps are required

Unlike traditional software, agents require maintenance in two directions:
1. **Model Evolution**: As the underlying AI model improves, the harness must adapt to leverage new capabilities while maintaining appropriate constraints.
2. **Workflow Drift**: As business processes change, the agent's sources, tools, and permissions must stay synchronized with current reality.

## The Pruning Principle

Counterintuitively, agents often improve when tools are removed rather than added. Vercel's case study showed an 80% reduction in tools led to better performance by:
- Reducing cognitive load on the agent
- Minimizing potential failure points
- Focusing the agent on core competencies

## Maintenance Cycles

Effective agent maintenance requires regular checks of:
1. **Input Sources**: Are the documents, databases, and context still accurate and relevant?
2. **Permission Scope**: Does the agent's access level match its current reliability?
3. **Output Validation**: Are proof requirements rigorous enough for the agent's growing capabilities?
4. **Value Assessment**: Is the agent's output actually being used and improving workflows?

## The Sailboat Analogy

Agents are more like sailboats than traditional software - they exist in dynamic environments where:
- Salt (data drift) corrodes components
- Lines (prompts) loosen over time
- Weather (business conditions) changes constantly

This requires ongoing maintenance rather than one-time deployment.