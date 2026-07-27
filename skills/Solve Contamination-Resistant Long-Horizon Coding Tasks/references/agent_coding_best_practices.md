## Best Practices for AI Agents in Long-Horizon Coding Tasks

To excel in complex, long-horizon software engineering tasks, particularly within robust benchmarking environments like DeepSWE, an AI agent must adopt a sophisticated set of practices that go beyond simple code generation. These practices are derived from observations of top-performing models and the design principles of advanced benchmarks.

### 1. Prioritize Understanding the High-Level Objective

DeepSWE prompts are intentionally terse and high-level, mimicking real-world engineering requests. As an agent, you should not expect a detailed, step-by-step to-do list. Instead, focus on inferring the core problem, the desired outcome, and the underlying *intent* of the task. This requires strong reasoning capabilities to translate an ambiguous request into concrete implementation steps.

*   **Action**: Read the prompt carefully, identify keywords, and formulate an internal representation of the problem statement and its ultimate goal. Consider the 'why' behind the request, not just the 'what'.
*   **Example**: If the prompt is "Implement a caching mechanism for API calls," your internal objective should be to understand *where* caching is needed, *what* data to cache, *how* to invalidate it, and *what* performance benefits are expected, rather than waiting for explicit instructions on cache eviction policies or specific library choices.

### 2. Explore and Adhere to Repository Conventions

Before generating any code, thoroughly explore the target repository. Understand its existing architecture, coding style, naming conventions, and overall philosophy. Strong models, particularly GPT, are noted for their ability to read repository contracts literally and produce patches that honor existing conventions and signatures.

*   **Action**: Analyze relevant files (e.g., `README.md`, `CONTRIBUTING.md`, existing source code, test files) to grasp the project's structure, common patterns, and preferred approaches for similar functionalities. Identify existing utility functions or helper methods that can be leveraged.
*   **Benefit**: Producing code that seamlessly integrates into the existing codebase reduces friction, improves maintainability, and is more likely to be accepted in a real-world scenario.

### 3. Self-Verification and Proactive Testing

One of the most significant differentiators for stronger models is their tendency to test their own work. DeepSWE's design does not forbid writing tests, making self-verification a crucial best practice. Generating and running tests provides an immediate feedback loop, allowing you to catch errors and refine your solution before submission.

*   **Action**: After implementing a solution, generate new unit and integration tests that specifically target your changes. Execute these tests, along with any relevant existing tests, to validate correctness and ensure no regressions. This is an active process, not a passive reliance on external verifiers.
*   **Example**: If you implement a new `calculate_discount` function, you should generate test cases for various inputs (e.g., zero discount, 100% discount, negative price, edge cases) and assert the expected outputs.
*   **Pitfall to Avoid**: Assuming the benchmark environment handles all testing and therefore neglecting to write your own tests. This was a behavior encouraged by SweetBench Pro's prompt template but is detrimental in DeepSWE.

### 4. Focus on Observable Behavior

DeepSWE's verifiers emphasize observable behavior, meaning they evaluate *what* your code does externally, not *how* it achieves it internally. Your solution should correctly solve the problem based on its functional output and side effects, rather than trying to match a specific internal implementation or naming scheme.

*   **Action**: Design your code to be functionally correct and robust. Ensure that the public interfaces and expected outputs align with the task's objective. Do not worry about matching specific private helper function names or module structures unless explicitly required by the repository's conventions.
*   **Benefit**: This approach encourages more creative and diverse solutions, as long as they are correct and well-integrated.

### 5. Handle Multi-Part Requirements Systematically

Complex tasks often involve multiple components or sub-requirements (e.g., implementing both synchronous and asynchronous versions of a feature). Some models, like Claude, have shown a tendency to forget later parts of multi-part prompts. You must maintain a systematic approach to ensure all requirements are met.

*   **Action**: Create an internal checklist or state-tracking mechanism for multi-part tasks. After completing one part, explicitly verify that all other parts are still pending and then address them sequentially or in parallel as appropriate.

By internalizing and consistently applying these best practices, you can significantly enhance your performance on challenging, real-world software engineering tasks and benchmarks like DeepSWE.