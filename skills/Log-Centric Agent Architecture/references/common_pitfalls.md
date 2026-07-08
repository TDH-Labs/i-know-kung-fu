# Common Pitfalls and Solutions

## 1. Treating Logs as Secondary
**Anti-pattern**: Storing logs as afterthought (e.g., local JSONL files without durability guarantees)
**Consequence**: Data loss when processes crash
**Solution**: Make log storage your primary architectural concern

## 2. Over-Compaction
**Anti-pattern**: Discarding raw logs after summarization
**Consequence**: Irreversible loss of agent history
**Solution**: Always retain raw logs; treat summaries as derived views

## 3. Provider Lock-in
**Anti-pattern**: Using proprietary log formats tied to specific platforms
**Consequence**: Inability to migrate agents
**Solution**: Use open formats (JSON Schema, Protocol Buffers)

## 4. State Leakage
**Anti-pattern**: Assuming tool calls are deterministic
**Example**: Agent sends email, then log is rewound - email remains sent
**Solution**: Clearly separate:
- Agent's view (log)
- World state (external systems)

## 5. Scaling Mistakes
**Anti-pattern**: Sticky sessions tying agents to specific workers
**Consequence**: Bottlenecks and difficult failover
**Solution**: Stateless workers + centralized log storage

## Debugging Tips
1. **Replay Testing**: Reconstruct agent state from log at any point
2. **Diff Analysis**: Compare projections from same log
3. **Failure Injection**: Kill workers mid-process to verify durability