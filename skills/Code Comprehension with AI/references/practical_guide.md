# Practical Guide to Implementing Code Comprehension Skills

## Creating Your 'Catch Me Up' Skill

1. **Template Structure**: Create a markdown file with:
   - Clear objectives
   - Context about your role
   - Specific exploration modes
   - Formatting preferences (tables, diagrams)

2. **Example Prompt Structure**:
```
I am [your role] working on [codebase/project]. Catch me up on:
1. [Architecture/Convention/Feature Trace/Syntax/Testing/History]
2. Specifically clarify: [your specific question]
3. Present information as: [table/diagram/bullet points]

Additional context: [any relevant background]
```

## Daily Workflow Integration

1. **Onboarding to New Code**:
   - Start with Architecture mode for high-level understanding
   - Then use Feature Trace for your specific work area

2. **PR Review Process**:
   - Use Convention mode to check against codebase standards
   - History mode to understand changes in context

3. **Incident Investigation**:
   - Combine Feature Trace and History modes
   - Ask for timeline of relevant changes

## Tooling Recommendations

- Store frequent prompts as reusable templates
- Maintain a prompt library categorized by exploration mode
- Log successful comprehension sessions for future reference

## Collaboration Practices

- Share effective prompts with team members
- Create team-standard comprehension templates
- Document 'gotchas' and verification steps