# Code Examples for Agent OS Components

Here are practical code snippets for implementing key Agent OS components:

1. **Scheduler/Orchestrator (Python)**:
```python
from queue import PriorityQueue

class Scheduler:
    def __init__(self):
        self.task_queue = PriorityQueue()

    def add_task(self, task, priority):
        self.task_queue.put((priority, task))

    def run_next_task(self):
        if not self.task_queue.empty():
            priority, task = self.task_queue.get()
            task.execute()

# Example usage
scheduler = Scheduler()
scheduler.add_task(live_customer_chat, priority=1)
scheduler.add_task(background_report, priority=2)
scheduler.run_next_task()
```

2. **Memory Manager (Python with Redis)**:
```python
import redis

class MemoryManager:
    def __init__(self):
        self.redis = redis.Redis(host='localhost', port=6379, db=0)

    def store_memory(self, agent_id, memory_type, data):
        key = f"{agent_id}:{memory_type}"
        self.redis.set(key, data)

    def retrieve_memory(self, agent_id, memory_type):
        key = f"{agent_id}:{memory_type}"
        return self.redis.get(key)

# Example usage
mm = MemoryManager()
mm.store_memory("hr_agent", "long_term", "user asked about parental leave")
print(mm.retrieve_memory("hr_agent", "long_term"))
```

3. **Tool Manager (Python with Sandboxing)**:
```python
import subprocess
import os

class ToolManager:
    def __init__(self, sandbox_dir):
        self.sandbox_dir = sandbox_dir
        os.makedirs(sandbox_dir, exist_ok=True)

    def run_tool(self, command):
        try:
            result = subprocess.run(command, cwd=self.sandbox_dir, capture_output=True, text=True, timeout=30)
            return result.stdout
        except subprocess.TimeoutExpired:
            return "Tool execution timed out"

# Example usage
tm = ToolManager("/path/to/sandbox")
print(tm.run_tool(["python", "script.py"]))
```

These examples provide a starting point for building your own Agent OS components.