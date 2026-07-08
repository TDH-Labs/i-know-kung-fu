---
description: Implement and manage AI agents where the log is the primary source of
  truth, enabling durability, scalability, and ownership.
name: Log-Centric Agent Architecture
tags:
- agent architecture
- log-based systems
- durable state
- agent ownership
- scalability
---

# Log-Centric Agent Architecture

> Implement and manage AI agents where the log is the primary source of truth, enabling durability, scalability, and ownership.

## Overview
This skill teaches you to build AI agents where the event log is the source of truth, not the runtime or model. Key benefits include:
- **Reliability**: Survives process crashes
- **Scalability**: Parallel processing of agents
- **Ownership**: Avoid vendor lock-in

Learn the core principles in [Core Concepts](references/core_concepts.md).

## Step-by-Step Workflow
1. **Initialize Log Storage**
   ```python
   # Using AWS S3 for durable storage
   import boto3
   s3 = boto3.client('s3')
   
   def append_log(session_id: str, entry: dict):
       """Atomically append to log"""
       key = f"agents/{session_id}/log.jsonl"
       s3.put_object(
           Bucket='my-agent-logs',
           Key=key,
           Body=json.dumps(entry) + '\n',
           ACL='private'
       )
   ```

2. **Worker Loop**
   ```python
   def process_agent_step(session_id: str):
       # 1. Acquire distributed lock
       with redis.lock(f"agent:{session_id}"):
           # 2. Read full log
           log = s3.get_object(Bucket='my-agent-logs', Key=f"agents/{session_id}/log.jsonl")
           
           # 3. Reconstruct state
           state = reconstruct_state(log)
           
           # 4. Get model response
           prompt = create_prompt(state)
           response = model.generate(prompt)
           
           # 5. Append new event
           append_log(session_id, {
               'timestamp': datetime.utcnow().isoformat(),
               'eventType': 'model_output',
               'content': response,
               'sequenceId': len(log.splitlines()) + 1
           })
   ```

3. **State Reconstruction**
   ```python
   def reconstruct_state(log_entries: list) -> dict:
       """Project log into current state"""
       state = {'history': [], 'pending_actions': []}
       
       for entry in log_entries:
           if entry['eventType'] == 'user_input':
               state['history'].append(f"User: {entry['content']}")
           elif entry['eventType'] == 'model_output':
               state['history'].append(f"Agent: {entry['content']}")
               
               # Parse tool calls
               if 'tool_call' in entry['content']:
                   state['pending_actions'].append(parse_tool_call(entry['content']))
       
       return state
   ```

## Best Practices
1. **Log Design**:
   - Use immutable, append-only writes
   - Include sequence IDs for ordering
   - Store in durable, centralized storage

2. **Worker Implementation**:
   - Keep workers stateless
   - Implement heartbeat checks
   - Use exponential backoff for contention

3. **Error Handling**:
   ```python
   try:
       process_agent_step(session_id)
   except ToolTimeoutError:
       append_log(session_id, {
           'eventType': 'failure',
           'content': {'error': 'Tool timeout', 'step': 'email_send'}
       })
   ```

## Validation Steps
1. **Crash Recovery Test**:
   - Kill worker mid-process
   - Verify new worker resumes correctly

2. **Log Consistency Check**:
   ```bash
   # Verify no gaps in sequence IDs
   awk '{print $2}' log.jsonl | sort -n | awk 'BEGIN{prev=0} {if ($1 != prev+1) print "Gap at " prev+1; prev=$1}'
   ```

3. **Projection Validation**:
   - Generate multiple summaries from same log
   - Verify key decisions remain consistent

For complete implementation guidance, see [Practical Guide](references/practical_guide.md). To avoid common mistakes, review [Common Pitfalls](references/common_pitfalls.md).

## 📺 Source Videos

- [The Log Is The Agent - Ishaan Sehgal, Omnara](https://www.youtube.com/watch?v=UPwGaM2MKHY) — AI Engineer

**Difficulty**: Intermediate

## Prerequisites

- basic understanding of AI agents
- familiarity with event logs
- experience with distributed systems
