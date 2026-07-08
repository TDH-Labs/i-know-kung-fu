# Practical Guide: Implementing Log-Centric Agents

## Log Structure
Design your log with these required fields:
```typescript
interface LogEntry {
  timestamp: string; // ISO-8601
  eventType: 'user_input' | 'model_output' | 'tool_call' | 'tool_result' | 'permission' | 'failure';
  content: string; // JSON string of event details
  sequenceId: number; // Strictly increasing
  sessionId: string; // Unique agent identifier
}

## Storage Requirements
1. **Durability**: Use write-ahead logging with fsync or equivalent cloud storage guarantees
2. **Atomicity**: Each append must be atomic (consider WAL or transaction logs)
3. **Access Control**: Implement fine-grained permissions for multiplayer scenarios

## Worker Implementation
Workers should:
1. Claim a session via distributed lock
2. Read the full log
3. Reconstruct state
4. Advance one step
5. Append new events
6. Release lock

Critical considerations:
- Workers must be stateless
- Never modify existing log entries
- Handle partial writes (use checksums)

## Compaction Strategies
1. **Windowed**: Keep last N entries + summary
2. **Semantic**: Identify and preserve key events
3. **Hybrid**: Combine recency with importance

Example compaction rule:
"If log exceeds 100 entries, summarize first 50 into 5 key points, keep last 50 verbatim"