# Practical Guide to Implementing Agent Systems

## Setting Up agents.md
1. Create an agents.md file at your project root
2. Include these essential sections:
   - **Setup Commands**: Installation and environment preparation
   - **Test Procedures**: Commands to validate work (e.g., `npm test`)
   - **Style Guidelines**: Code formatting rules
   - **Workflow Rules**: PR title formats, commit message conventions

Example agents.md structure:
```markdown
# Project X Agent Configuration

## Setup
Run: `npm install && pip install -r requirements.txt`

## Testing
Always execute before committing:
`pytest ./tests && npm run lint`

## Style Guide
- Use 4-space indentation
- Follow PEP8 for Python
- Prefix React components with 'X'
```

## Developing Agent Skills
1. Create a skill folder with:
   - skill.md (metadata and invocation conditions)
   - Required scripts/resources
2. In skill.md, specify:
   - Description of when to use the skill
   - Required parameters
   - Expected outputs

Example skill.md:
```markdown
# PowerPoint Creation Skill

Invoke when user requests:
- "create presentation"
- "make slides about X"

## Parameters
- topic: string
- slide_count: integer

## Output
.pptx file in /output
```

## MCP Integration
1. Identify target APIs/tools
2. Deploy MCP servers as wrappers
3. Configure agent to connect via:
   - Standard MCP port (default 8080)
   - Authentication tokens

## A2A Implementation
1. Publish agent cards describing:
   - Capabilities
   - Input/output formats
   - Availability
2. Set up discovery service for agents to find each other