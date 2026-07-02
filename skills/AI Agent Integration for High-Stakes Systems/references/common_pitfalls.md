# Common Pitfalls in AI Agent Integration

## Lack of Resource Isolation
**Pitfall**: Allowing agents to directly modify production infrastructure can lead to interference with critical systems.
**Example**: An agent modifying Flink or Spark jobs in production could disrupt real-time feature serving.
**Solution**: Use branch-based resource isolation to ensure agent experiments run in isolated environments.

## Ignoring Compute Reuse
**Pitfall**: Recomputing unchanged features for every experiment is costly and inefficient.
**Example**: An agent recomputing 30-day and 60-day features when only adding a 7-day feature.
**Solution**: Leverage Chronon's partial aggregate caching to reuse precomputed features.

## Unreviewed Changes
**Pitfall**: Deploying agent-generated changes to production without human review can introduce risks.
**Example**: An agent deploying a poorly performing model to production due to lack of oversight.
**Solution**: Require human review for all changes before they proceed to production.

## Inadequate Resource Limits
**Pitfall**: Allowing unlimited agent experimentation can lead to skyrocketing infrastructure costs.
**Example**: Running 2,000 simultaneous experiments without cost controls.
**Solution**: Set resource allocation limits at the team, agent, or user level to manage costs.