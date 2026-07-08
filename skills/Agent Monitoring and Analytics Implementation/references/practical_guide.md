# Practical Implementation Guide

## Instrumentation Layers
1. **Engineer Observability**:
   - Model call tracing
   - Tool execution logs
   - Error rate monitoring
   - Latency/cost metrics

2. **Product Analytics**:
   - Workflow completion rates
   - User acceptance metrics
   - Correction frequency by task type
   - Permission boundary hits

## Implementation Steps
1. **Tagging Strategy**:
   - Unique run IDs persisting across all events
   - Workflow type classification (e.g., 'db_operation', 'report_generation')
   - Criticality flags for destructive actions

2. **Event Schema**:
```typescript
interface AgentRunEvent {
  runId: string;
  workflowType: string;
  timestamp: ISO8601;
  eventType: 'start' | 'tool_call' | 'permission_check' | 'correction' | 'completion';
  payload: {
    // Contextual data specific to event type
    toolsAttempted?: string[];
    userCorrection?: 'edit' | 'denial' | 'interruption';
    completionState?: 'success' | 'partial' | 'failed';
  };
}
```

3. **Dashboard Essentials**:
   - Completion/acceptance rate divergence
   - Correction heatmaps by workflow step
   - Permission failure clusters
   - Tool call success rate trends

**Critical Integration**: Pipe engineering traces (e.g., OpenAI API errors) into the same run context as product events to correlate technical failures with user impact.