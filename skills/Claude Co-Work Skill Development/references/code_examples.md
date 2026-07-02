# Code and Prompt Examples for Claude Skills

## Skill Creation Prompt Template
```
Create a skill according to the following guidelines:

1. Name and Trigger:
- Name: [Skill Name]
- Trigger when: [description of when skill should activate]

2. Goal:
[Clear objective of what the skill accomplishes]

3. Connectors/APIs:
- [List required integrations]
- [Specify any special usage instructions]

4. Reference Files:
- [List required context files]
- [Explain their purpose]

5. Process Steps:
1. [First step with details]
2. [Second step with details]
...
[N. Final step and output]

6. Rules:
- [Edge case handling]
- [Quality controls]
- [Progressive improvement instructions]
```

## MCP Server Installation
For custom MCP servers:
1. Find documentation (search "[Tool] MCP server")
2. Either:
   - Add remote server URL via Connectors > +
   OR
   - Edit config file (Settings > Developer > Edit Config)
3. For config edits:
   - Paste JSON into Claude and ask for update
   - Insert new MCP configuration
   - Save and restart Claude

## Testing Prompt Example
```
Run an evaluation test for [Skill Name] with:
- Optimization focus: [specific aspect to improve]
- Test criteria:
  1. [Criterion 1]
  2. [Criterion 2]
  3. [Criterion 3]
- Test method:
  - Use [number] variations
  - Test on [specific input or range]
  - Compare against [baseline if applicable]
```