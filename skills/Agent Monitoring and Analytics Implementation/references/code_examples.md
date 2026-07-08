# Code Examples for Agent Telemetry

## Python Instrumentation
```python
# Decorator for tool call tracking
def track_tool_call(tool_name):
    def decorator(func):
        def wrapper(*args, **kwargs):
            run_id = get_current_run_id()  # From thread-local/context
            emit_event(run_id, {
                'eventType': 'tool_call',
                'tool': tool_name,
                'timestamp': datetime.utcnow().isoformat()
            })
            try:
                result = func(*args, **kwargs)
                emit_event(run_id, {'status': 'success'})  # Success follow-up
                return result
            except PermissionError as e:
                emit_event(run_id, {
                    'status': 'permission_denied',
                    'error': str(e)
                })
                raise
        return wrapper
    return decorator

# Usage example
@track_tool_call('database.execute')
def execute_sql(query):
    # ... actual DB logic
```

## Critical Prompts
**Agent Self-Reporting Template**:
```
You are assisting with {workflow_type}. Before taking any action, you MUST:

1. Confirm the current run ID is {run_id}
2. Classify this step as one of:
   - [INFO_LOOKUP] Gathering data
   - [ACTION] Attempting change
   - [REVIEW] Seeking approval
3. If hitting a permission boundary, report:
   "PERMISSION_CHECK_FAILED: {reason}"

After completion, summarize:
"RUN_STEP_COMPLETE: {outcome} with {retries} retries"
```

**Correction Analysis Query** (SQL):
```sql
SELECT 
  workflow_type,
  COUNT(CASE WHEN eventType = 'correction' THEN 1 END) * 100.0 / COUNT(*) as correction_rate,
  AVG(CASE WHEN completionState = 'success' THEN 1 ELSE 0 END) as completion_rate
FROM agent_events
GROUP BY workflow_type
HAVING correction_rate > 15  # Threshold for investigation
```