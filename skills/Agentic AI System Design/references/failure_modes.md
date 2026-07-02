# Detailed Analysis of Agentic AI Failure Modes

## Infinite Loops
Occur when agents repetitively perform similar tasks without making progress toward goal completion. Primary causes:
1. **Missing Termination Conditions**: No defined limits on retries or runtime
2. **Lack of Action Tracking**: Not monitoring if actions change between iterations
3. **No Progress Measurement**: Failing to track whether results improve with retries

Example: An agent searching for a non-existent document keeps retrying with similar search terms without realizing the document doesn't exist.

## Hallucinated Planning
Happens when agents create plausible but impossible execution plans due to:
1. **Undefined Tool Capabilities**: Agents assume unavailable functionality
2. **Missing Plan Validation**: Executing without verifying feasibility
3. **Unclear Constraints**: Agents make assumptions instead of checking limitations

Example: An agent plans to book flights using a non-existent travel API.

## Unsafe Tool Use
Occurs when technically valid actions have unintended consequences:
1. **Overprivileged Tools**: Excessive permissions granted
2. **Missing Approval Workflows**: No review for high-risk actions
3. **Undefined Access Tiers**: No separation between read/write/delete operations

Example: A database cleanup agent accidentally deletes active records instead of archived ones.