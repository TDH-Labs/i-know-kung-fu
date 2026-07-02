# Practical Implementation Guide

## Environment Setup
1. Install Sandcastle: `npm install @aihero/sandcastle`
2. Initialize configuration: `npx sandcastle init`
   - Select agent (Claude Code recommended)
   - Choose sandbox (Docker)
   - Select backlog manager (GitHub Issues)
   - Pick template (Parallel Planner with Review)

## Docker Configuration
The generated Dockerfile includes:
- System dependencies
- GitHub CLI
- Home directory setup
- Agent installation
Build with: `docker build -t sandcastle-agent .`

## Authentication
Set these in `.sandcastle/.env`:
```
ANTHROPIC_API_KEY=your_key
GITHUB_TOKEN=your_token
```

## Workflow Customization
Modify these key files:
1. `.sandcastle/main.mts` - Main orchestration logic
2. `.sandcastle/prompts/plan.md` - Planner prompt template
3. `.sandcastle/prompts/implement.md` - Implementation prompt
4. `.sandcastle/prompts/review.md` - Code review criteria

## Execution
Add to package.json:
```json
"scripts": {
  "sandcastle": "npx tsx .sandcastle/main.mts"
}
```
Run with: `npm run sandcastle`