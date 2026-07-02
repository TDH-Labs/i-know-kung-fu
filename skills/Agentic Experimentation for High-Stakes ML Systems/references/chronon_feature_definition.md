Example Chronon feature definition:
```python
# Define a windowed aggregation feature
Feature(
  name="user_purchase_count_7d",
  sources=[Source(
    events=EventSource(
      table="purchase_events",
      query="SELECT user_id, timestamp, amount FROM purchases"
    )
  )],
  aggregation=Aggregation(
    operation=Operation.SUM,
    windows=[Window(length=7, timeUnit=TimeUnit.DAYS)]
  )
)