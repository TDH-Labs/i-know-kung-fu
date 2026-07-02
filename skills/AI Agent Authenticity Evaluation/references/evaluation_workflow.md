# Step-by-Step Evaluation Workflow

## Preparation Phase
1. Gather all available product documentation
2. Identify claimed capabilities from marketing materials
3. Note any specific technical claims about architecture

## Testing Methodology
### 1. Capability Verification
- **Test Input**: Present a simple, well-defined task
- **Expected Behavior**: Observe if the system can complete the task end-to-end
- **Level 1 Indicator**: Only provides classification/decision outputs
- **Level 2 Indicator**: Generates content but requires manual iteration
- **Level 3 Indicator**: Autonomously completes multi-step tasks

### 2. Process Examination
- **Request**: Ask for execution details or intermediate steps
- **Level 1-2 Sign**: No visible process or simple linear generation
- **Level 3 Sign**: Demonstrates planning, iteration, and adaptation

### 3. Goal Persistence Test
- **Method**: Give a complex, ambiguous instruction
- **Evaluation**: Does the system ask clarifying questions and maintain goal focus?
- **True Agent Behavior**: Shows capacity for context maintenance and problem decomposition

## Scoring Rubric
Create a weighted scoring system across these dimensions:
1. Autonomy (40% weight)
2. Generative Capacity (30%)
3. Iterative Improvement (20%)
4. Context Maintenance (10%)

Thresholds:
- Below 50: Level 1 system
- 50-75: Level 2 system
- Above 75: Likely Level 3 agent