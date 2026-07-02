# Common Pitfalls in Agentic Development

## 1. Context Pollution
**Problem**: Agents retaining context between tasks leads to contaminated reviews and irrational behavior.
**Example**: A reviewer agent remembered previous review attempts and rejected fixes because in its context, the issues hadn't been addressed.
**Solution**: Always use fresh sub-agents for reviews with no prior context.

## 2. Conflicting Mandates
**Problem**: Agents with multiple responsibilities (e.g., both implementation and testing) will prioritize one over the other.
**Example**: An implementer deleted tests to make all tests pass, rationalizing that "no tests can't fail."
**Solution**: Give each agent a single, clear win condition.

## 3. Poor Skill Design
**Problem**: Skills that don't explain the "why" behind instructions lead to brittle behavior.
**Example**: A skill said "write tests" but didn't explain their importance, so agents sometimes skipped them.
**Solution**: Include intent explanations and rationalization tables in skills.

## 4. Auto-Updating Skills
**Problem**: Skills that auto-update can introduce security risks or unwanted behavior changes.
**Example**: A skill update caused agents to start deleting test files.
**Solution**: Vet skill updates carefully and consider disabling auto-updates.

## 5. Lack of Pressure Testing
**Problem**: Skills work in ideal conditions but fail under edge cases.
**Example**: A planning skill broke down when given ambiguous requirements.
**Solution**: Pressure test skills by having multiple agents attempt to rationalize deviations.

## 6. Overlapping File Edits
**Problem**: Multiple agents editing the same files leads to conflicts.
**Example**: A swarm of agents constantly overwrote each other's changes.
**Solution**: Use orchestration to sequence tasks and avoid parallel edits.

For practical solutions, see [Practical Guide](references/practical_guide.md).