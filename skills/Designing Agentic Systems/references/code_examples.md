## Code Examples
### Structured Output Example
```python
{
  "decision": "approve",
  "score": 4.5,
  "reason": "The house meets all criteria and has a short commute."
}
```

### Idempotency Check Example
```python
if not action_already_taken:
    take_action()
    log_action()
else:
    complete_missing_parts()
```