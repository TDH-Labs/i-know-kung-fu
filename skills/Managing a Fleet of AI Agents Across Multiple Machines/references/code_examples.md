# Code Examples
This document provides code examples for managing a fleet of AI agents across multiple machines.

## CLI Harness for Dispatching Tasks
```bash
function dispatch_task() {
  local task=$1
  local worker=$2
  tmux send-keys -t $worker "$task" C-m
}
```

## Git Commit and Push for Context Files
```bash
git add .
git commit -m "Update context files"
git push origin main
```

## Tmux Send-Keys Over SSH
```bash
ssh user@machine 'tmux send-keys -t session_name "git pull" C-m'
```

## Example Workspace Structure
```
/workspaces
  /shared
  /machineA
  /machineB
  /handoff
```

## Example Review Gateway Hook
```bash
function approve_task() {
  local task=$1
  local worker=$2
  tmux send-keys -t $worker "$task" C-m
}
```

For more detailed information, refer to the Core Concepts and Practical Guide.