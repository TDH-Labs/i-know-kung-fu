# Code Examples for AI Agent Integration

## Defining a Feature with Chronon
```python
from chronon import Feature, Join

# Define a new feature
feature = Feature(
    name="user_7day_activity",
    description="7-day window of user activity",
    aggregation="sum",
    source="user_activity_logs",
    window="7d"
)

# Add the feature to a join
join = Join(
    name="user_features",
    features=[feature]
)

# Compile the join
join.compile()
```

## Running an Experiment
```python
# Create a new branch for the experiment
branch = "experiment_user_7day_activity"

# Modify the feature set
join.features.append(Feature(
    name="user_30day_activity",
    description="30-day window of user activity",
    aggregation="sum",
    source="user_activity_logs",
    window="30d"
))

# Backfill the data
join.backfill(branch=branch)

# Train a new model version
model.train(training_data=join.get_training_data(), branch=branch)

# Deploy to dev
model.deploy(environment="dev", branch=branch)
```

## Reviewing and Deploying Changes
```python
# Human review process
if human_review_approved:
    # AB test in dev
    model.ab_test(environment="dev", branch=branch)
    
    # Monitor performance
    performance = model.monitor(environment="dev", branch=branch)
    
    if performance.meets_criteria:
        # Deploy to prod
        model.deploy(environment="prod", branch=branch)
```