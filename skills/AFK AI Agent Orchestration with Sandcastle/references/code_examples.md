# Code Examples and Templates

## Basic Orchestration Snippet
```typescript
// From .sandcastle/main.mts
import { run } from '@aihero/sandcastle';

// Planner agent
const plan = await run({
  name: 'planner',
  agent: 'claude-code',
  sandbox: 'docker',
  prompt: 'plan.md', // Contains GitHub issue processing logic
});

// Extract issues from plan output
const { issues } = JSON.parse(
  plan.match(/<plan>([\s\S]*?)<\/plan>/)[1]
);

// Parallel implementation
await Promise.all(issues.map(async (issue) => {
  const implementation = await run({
    name: `implementer-${issue.id}`,
    agent: 'claude-code',
    sandbox: 'docker',
    prompt: 'implement.md',
    promptArgs: {
      issueTitle: issue.title,
      taskId: issue.id
    }
  });

  // Reviewer workflow
  if (implementation.commits.length > 1) {
    await run({
      name: `reviewer-${issue.id}`,
      agent: 'claude-code',
      sandbox: 'docker',
      prompt: 'review.md',
      promptArgs: {
        sourceBranch: 'main',
        branch: implementation.branch
      }
    });
  }
}));
```

## Dynamic Prompt Example (review.md)
```markdown
Analyze this code change:

!```git diff {{sourceBranch}} {{branch}}```

Coding Standards:
1. Use TypeScript strict mode
2. All functions under 50 lines
3. 100% test coverage for new features
4. JSDoc comments for public APIs

Output format:
<analysis>
  <correctness>...</correctness>
  <improvements>...</improvements>
</analysis>
```