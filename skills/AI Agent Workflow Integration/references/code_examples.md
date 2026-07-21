## Code Examples
### CLI Commands
```bash
# Delegate a task to create a finance app
copilot delegate "Create a finance app that tracks my spending. Use HTML, CSS, and JavaScript."
```

### Agents.md
```markdown
## Project Overview
This project is a finance tracker built with React and Tailwind.
## Agent Responsibilities
- Do not change the architecture without explicit approval.
- Follow coding standards defined in the repository.
```

### Custom Agent Definition
```yaml
# Example custom agent definition
role: Security Expert
tools:
  - Read files
  - Search the web
  - Create to-do lists
skills:
  - Security audit
  - Vulnerability scanning
```

### Delegation in GitHub UI
```markdown
# Example GitHub issue
Title: Add dark mode to my app
Description: Implement dark mode using Tailwind CSS.
Assign to agent: Copilot
```