# Core Concepts of Agent Analytics

Agent analytics fundamentally shifts from traditional product metrics (clicks, sessions) to tracking **delegated work units**. Key concepts:

1. **Agent Run**: The complete lifecycle of an agent attempting a task, from instruction to completion. Unlike sessions, runs track workflow success/failure states.

2. **Correction Signals**: User interventions (edits, denials, interruptions) that reveal agent misunderstandings. These are the 'new clicks' for agent products.

3. **Completion vs Acceptance**: 
   - Completion: Task reached an end state
   - Acceptance: User trusted the output
   Gap between these indicates trust issues.

4. **Work Unit Telemetry**: Must capture:
   - Initial instruction context
   - Tool calls attempted/succeeded
   - Permission boundary hits
   - Retry patterns
   - User corrections

Example: A database deletion incident could be predicted by analyzing patterns of excessive retries on destructive operations or frequent permission boundary violations in similar workflows.

5. **Three Critical Events**:
   - Run start (intent capture)
   - Task completion (workflow state)
   - Mid-run corrections (real-time feedback)

Without this granular view, teams risk monitoring 'activity' (e.g., chat volume) while missing actual workflow failures.