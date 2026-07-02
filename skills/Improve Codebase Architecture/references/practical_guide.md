# Practical Guide to Improving Codebase Architecture

## Step 1: Codebase Exploration
Begin by having your AI assistant explore the codebase to identify:
- Shallow modules (complex interfaces with little implementation)
- Poorly defined interfaces
- Duplicate implementations of the same concept
- Areas with low locality (related code scattered)

## Step 2: Candidate Identification
Look for these common patterns:
1. **Duplicate implementations**: Same concept implemented in multiple places
   - Example: Frontend and backend both implementing business rules
2. **Overexposed modules**: Too many implementation details in interfaces
3. **Tight coupling**: Modules with many direct dependencies

## Step 3: Deepening Modules
For each candidate:
1. Define a clear interface that hides implementation details
2. Consolidate duplicate implementations
3. Move related functionality into the module to improve locality

## Step 4: Establishing Seams
1. Identify natural boundaries between modules
2. Define clear interfaces at these boundaries
3. Implement adapters for different contexts (e.g., testing vs production)

## Step 5: Testing Strategy
1. Write tests at module seams
2. Use mocks/stubs to test modules in isolation
3. Verify interface contracts are maintained

## Working with AI
1. Use the AI to explore and identify candidates
2. Engage in a "grilling session" to refine solutions
3. Have the AI propose module shapes and interfaces
4. Make strategic decisions about what to implement

Remember: The AI is tactical, you provide strategic direction. Run this process regularly (every few days) in fast-moving codebases.