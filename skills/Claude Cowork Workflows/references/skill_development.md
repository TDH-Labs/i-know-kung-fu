# Comprehensive Skill Development Guide

## Skill Components
Every skill should consider including:
1. skill.md - Core instruction file with:
   - Process steps
   - Human-in-the-loop points
   - Reference file usage instructions
   - Expected outputs
   - Rules

2. Reference Files (optional but recommended):
   - Text files (style guides, examples, ICP)
   - Assets (images, presentations for examples)
   - Code scripts (for API calls or functions)

## Building Process
1. Define the ideal step-by-step process
2. Identify needed knowledge sources
3. Determine required tools/connectors
4. Prepare good output examples

## Prompt Template for Skill Creation
```
Create a skill according to the following guidelines:

Name: [Skill Name]
Trigger: [When should the skill activate?]

Goal: [Clear objective for the skill]

Connectors: [List of required connectors/APIs/MCPs]

Reference Files:
- [File 1]: [Purpose]
- [File 2]: [Purpose]

Process:
1. [Step 1 description]
   - Human in the loop: [Yes/No]
   - Input: [What's needed]
   - Output: [Expected result]
2. [Step 2 description]
   ...

Rules:
- [Rule 1: Potential failure point to avoid]
- [Rule 2: Reference file usage requirement]

Progressive Updates:
- Automatically update rules when users specify "don't do X"
- Save approved outputs as good examples
```

## Testing and Optimization
### Evaluation Framework
1. Define optimization focus (one primary metric)
2. Set evaluation criteria (3-5 specific measures)
3. Specify test parameters:
   - Number of variations
   - Input consistency

Example test prompt:
```
Run a new test to optimize for [specific metric].

Criteria:
1. [Criterion 1]
2. [Criterion 2]
3. [Criterion 3]

Parameters:
- Use [specific input] for all tests
- Run [number] variations
- Focus on [specific aspect]
```

### AB Testing
Use for:
- Comparing skill versions
- Optimizing existing skills
- Testing against new model versions

AB Test Prompt:
```
Run an AB test on [Skill Name] to optimize for [metric].

Constraints:
- Must maintain [critical feature]
- Cannot compromise [important aspect]

Use [specific input] for testing.
```