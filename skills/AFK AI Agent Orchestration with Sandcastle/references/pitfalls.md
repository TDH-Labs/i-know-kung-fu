# Common Pitfalls and Solutions

## Permission Management
**Problem:** Agents making dangerous system changes
**Solution:** Always use sandboxes. The transcript warns about agents deleting home directories when run unsandboxed.

## Resource Contention
**Problem:** Parallel agents conflicting on shared resources
**Solution:** Use separate branches per task. The example shows each implementer works on its own branch.

## Infinite Loops
**Problem:** Agents getting stuck in recursive tasks
**Solution:** Set timeouts in Sandcastle.run() and monitor context window usage (shown in planner logs).

## Prompt Injection
**Problem:** Malicious issue content affecting agent behavior
**Solution:** Sanitize GitHub issue inputs and use constrained output formats (like the <plan> XML tags).

## Merge Conflicts
**Problem:** Parallel changes causing integration issues
**Solution:** Use a dedicated merger agent with conflict resolution skills, as demonstrated in the transcript.

## API Limitations
**Problem:** Anthropic's restrictions on subscription usage
**Solution:** Follow the latest guidelines from their API docs or use API keys instead of subscriptions.

## Log Management
**Problem:** Losing track of parallel agent activities
**Solution:** Use the built-in logging system and control-click links to inspect individual agent sessions.