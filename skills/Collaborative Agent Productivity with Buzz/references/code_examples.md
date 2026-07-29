# Code Examples for Buzz
This document provides practical code snippets for integrating and managing agents in Buzz.

## Adding an Agent
```python
# Example: Adding an agent to Buzz
agent = BuzzAgent(name='Fizz', role='Code Reviewer')
agent.add_to_team(team_id='your_team_id')
```

## Assigning Tasks
```python
# Example: Assigning a task to an agent
task = Task(description='Review the latest code commit', agent='Fizz')
task.assign()
```

## Initiating an Agent Huddle
```python
# Example: Initiating an agent huddle
huddle = AgentHuddle(agents=['Fizz', 'Honey'])
huddle.start()
```

## Sharing LLMs
```python
# Example: Sharing a local LLM
llm = LocalLLM(model='Codex')
llm.share_with_team(team_id='your_team_id')
```

For best practices and common pitfalls, refer to the [Practical Guide](references/practical_guide.md).