# Code Examples and Templates

## Feature Definition Example (Chronon API)
```python
# Defining a new feature to add to fraud detection model
from chronon import GroupBy, Aggregation

# Reusing existing production features
payment_features = GroupBy(
    sources=["table.payments"],  # Existing production data source
    keys=["user_id"],           # Join key
    aggregations=[
        # Existing 30-day feature
        Aggregation(
            operation="SUM",
            column="amount",
            windows=["30d"]
        ),
        # New 7-day feature proposed by agent
        Aggregation(
            operation="SUM",
            column="amount",
            windows=["7d"],  # New window size
            name="payment_sum_7d"  # Explicit naming
        )
    ]
)
```

## Experiment Workflow Template
```python
# Agent experiment workflow pseudocode
def run_experiment():
    # 1. Create isolated branch
    branch = create_isolated_branch("fraud-model-iteration-42")
    
    # 2. Modify feature set (reusing existing features)
    new_features = modify_features(
        existing="prod_fraud_features",
        modifications=["add_7d_window"]
    )
    
    # 3. Generate training data (automatically reuses computations)
    training_data = generate_training_data(
        features=new_features,
        isolation_branch=branch
    )
    
    # 4. Train model (on isolated resources)
    model = train_model(
        data=training_data,
        target="is_fraud",
        infrastructure="dev"
    )
    
    # 5. Package results for review
    return {
        "branch": branch,
        "feature_changes": diff("prod", branch),
        "model_metrics": model.evaluate(),
        "compute_cost": get_cost(branch)
    }
```

## Safety Checks
```python
# Pre-flight checks before experiment runs
def safety_checks(feature_changes):
    # Ensure no production data will be modified
    assert not feature_changes.affects_production(), \
        "Cannot modify production data directly"
    
    # Validate resource limits
    assert estimated_cost(feature_changes) < MAX_BUDGET, \
        f"Experiment exceeds ${MAX_BUDGET} budget"
    
    # Verify feature semantics are clear
    assert feature_changes.is_semantically_clear(), \
        "Feature changes must have clear semantics"
```