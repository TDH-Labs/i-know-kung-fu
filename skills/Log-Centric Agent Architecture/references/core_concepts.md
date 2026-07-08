# Core Concepts: Log-Centric Agent Architecture

## The Log as the Agent
At its core, this architecture posits that an agent's identity and state are not defined by its runtime environment or model, but rather by its immutable, append-only event log. This log contains every significant state transition:
- User inputs
- Model outputs
- Tool calls and their results
- Permission requests
- Failures

## Key Properties
1. **Durability**: The agent survives process failures because its state is reconstructed from the log.
2. **Scalability**: Workers can process any agent's state by reading its log, enabling horizontal scaling.
3. **Ownership**: The log becomes the valuable asset, not the runtime or model.

## Projections
Various components interact with projections (derived views) of the log:
- **Model Context**: A compacted summary fitting within context windows
- **UI State**: A rendered view of current status
- **Debugging**: Full trace of all events

## Compaction
While logs grow indefinitely, models require finite context. Compaction creates lossy summaries that:
- Preserve essential agent state
- Allow continuation of work
- Don't replace the raw log (which remains the source of truth)