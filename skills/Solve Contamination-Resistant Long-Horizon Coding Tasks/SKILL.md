---
description: This skill enables an AI agent to effectively approach and solve complex,
  multi-file software engineering tasks within a contamination-resistant benchmarking
  environment like DeepSWE. It emphasizes understanding high-level objectives, exploring
  repository conventions, generating robust solutions focused on observable behavior,
  and performing self-verification.
name: Solve Contamination-Resistant Long-Horizon Coding Tasks
tags:
- AI coding
- software engineering
- long-horizon tasks
- benchmarking
- DeepSWE
- contamination resistance
- code generation
- code testing
- problem-solving
- observable behavior
---

# Solve Contamination-Resistant Long-Horizon Coding Tasks

> This skill enables an AI agent to effectively approach and solve complex, multi-file software engineering tasks within a contamination-resistant benchmarking environment like DeepSWE. It emphasizes understanding high-level objectives, exploring repository conventions, generating robust solutions focused on observable behavior, and performing self-verification.

## Overview
As an AI agent, your ability to solve complex software engineering problems is paramount. This skill focuses on tackling 'long-horizon' coding tasks, which involve significant changes across multiple files and require deep understanding of a codebase, rather than simple, isolated bug fixes. The context for this skill is derived from benchmarks like DeepSWE, designed to be 'contamination-resistant' and evaluate true problem-solving capabilities, unlike older benchmarks that suffered from data leakage and brittle verifiers.

DeepSWE tasks are characterized by their originality, terse high-level prompts, and verifiers that focus on observable behavior rather than specific implementation details. This demands a more sophisticated approach from you, moving beyond merely following explicit instructions to truly reasoning about and implementing solutions that integrate seamlessly into existing projects. For a deeper understanding of DeepSWE's design and its advantages, refer to [DeepSWE Overview](references/deep_swe_overview.md).

## Step-by-Step Workflow
To successfully navigate and solve long-horizon, contamination-resistant coding tasks, follow this structured workflow:

1.  **Understand the High-Level Objective**: DeepSWE prompts are intentionally terse and high-level, mirroring real-world engineering requests. You will not be given a detailed to-do list. Your first step is to thoroughly analyze the prompt to infer the core problem and the desired outcome. Focus on the *intent* behind the request.

    *   **Best Practice**: Treat the prompt as a high-level goal, not a prescriptive set of instructions. You must reason about the necessary steps yourself.
    *   **Pitfall**: Over-reliance on explicit instructions, expecting a detailed breakdown of tasks or function signatures, as seen in older benchmarks like SweetBench Pro.

2.  **Explore the Repository and Existing Conventions**: Before writing any code, immerse yourself in the target repository. Understand its architecture, existing conventions, coding style, and the philosophy behind its design. This is crucial for producing a solution that integrates naturally.

    *   **Action**: Scan relevant files, read documentation, and identify common patterns for function signatures, error handling, and module organization.
    *   **Best Practice**: Emulate the behavior of strong models like GPT, which excel at reading repository contracts literally and honoring existing conventions.
    *   **Prompt Snippet (Internal Thought Process)**:
        ```
        "Analyze the provided repository context. Identify key architectural patterns, naming conventions, and existing utility functions. Specifically, look for how similar features are implemented and how tests are structured. My goal is to produce a patch that aligns with these conventions." 
        ```

3.  **Reason about To-Dos and Plan Implementation**: Based on the high-level objective and your understanding of the repository, break down the problem into a series of concrete, actionable steps. This involves identifying which files need to be modified, what new functions or classes might be required, and how they will interact.

    *   **Best Practice**: Develop a clear, multi-step plan before generating code. Consider potential edge cases and dependencies.
    *   **Pitfall**: Forgetting parts of a multi-part prompt. Models like Claude have been observed to implement synchronous parts but drop asynchronous requirements in multi-part tasks. Always re-verify all requirements before proceeding.

4.  **Implement the Solution Focusing on Observable Behavior**: Generate the code changes across multiple files as identified in your plan. Your primary goal is to ensure the solution correctly achieves the task's objective, as measured by its external, observable behavior. Do not try to match a specific internal implementation or function naming scheme that might have been used in a historical PR.

    *   **Best Practice**: Produce a solution that is robust and functionally correct, regardless of internal implementation specifics. DeepSWE verifiers reward *any* correct implementation. Refer to [Designing Robust Verifiers](references/designing_robust_verifiers.md) for more details.
    *   **Action**: Modify existing files, create new ones, and ensure all changes are consistent with the repository's conventions.
    *   **Code Snippet (Example of a patch)**:
        ```diff
        --- a/src/utils.py
        +++ b/src/utils.py
        @@ -10,6 +10,10 @@
         def format_name(first, last):
             return f"{first.capitalize()} {last.capitalize()}"
        
        +def calculate_discount(price, percentage):
        +    return price * (1 - percentage / 100)
        +
         def is_valid_email(email):
             import re
             return re.match(r"[^@]+@[^@]+\.[^@]+", email) is not None
        ```

5.  **Self-Verification and Testing**: This is a critical step for stronger models. Since DeepSWE does not explicitly forbid writing tests, you should actively generate and run tests to verify your own work. This provides an immediate feedback loop and helps catch errors before submission.

    *   **Best Practice**: Proactively write new tests or extend existing ones to cover your changes. Stronger models (e.g., GPT 5.4/5.5, Opus 4.7/4.8) exhibit this behavior frequently. This is a key differentiator.
    *   **Prompt Snippet (Internal Thought Process)**:
        ```
        "Given the implemented changes, generate a comprehensive set of unit and integration tests to validate the new functionality and ensure no regressions have been introduced. Execute these tests and analyze the results." 
        ```
    *   **Pitfall**: Assuming tests are 'handled' by the benchmark environment and neglecting to write your own, as models were prompted to do in SweetBench Pro.

6.  **Iterate and Refine**: Based on the results of your self-verification, iterate on your solution. Debug any failures, refine your implementation, and re-run tests until you are confident in the correctness and robustness of your patch.

    *   **Best Practice**: Treat test failures as opportunities to learn and improve. Don't stop at the first working solution; strive for optimal integration and robustness.

## Best Practices
*   **Prioritize Intent over Literal Prescription**: DeepSWE prompts are high-level. Focus on the underlying problem and desired outcome, not a rigid set of instructions. This encourages exploration and reasoning.
*   **Adhere to Repository Conventions**: Always analyze and respect the existing code style, architecture, and conventions of the target repository. Your solution should look and feel like it belongs.
*   **Actively Self-Test**: Generate and execute tests for your own code. This is a hallmark of strong AI agents and is not discouraged by DeepSWE's design. It significantly improves solution quality.
*   **Focus on Observable Behavior**: Ensure your solution correctly solves the problem based on its external effects. DeepSWE's verifiers are designed to be implementation-agnostic, rewarding any functionally correct approach.
*   **Manage Multi-Part Requirements**: When a task has multiple sub-components, maintain a clear internal checklist to ensure all parts are addressed. Avoid dropping requirements, a common pitfall for some models.
*   **Resist Contamination Attempts**: Do not attempt to 'cheat' by accessing external knowledge bases, public PRs, or `git log` history for golden patches. DeepSWE is specifically designed to prevent such exploits. For more details, see [Avoiding Benchmark Contamination](references/avoiding_benchmark_contamination.md).

## Common Pitfalls
*   **Expecting Overly Verbose Prompts**: Unlike SweetBench Pro, DeepSWE prompts are terse. Expecting a detailed to-do list will lead to inaction or incorrect assumptions.
*   **Missing Requirements in Multi-Part Tasks**: As observed with Claude, failing to address all aspects of a complex, multi-faceted task is a significant pitfall.
*   **Attempting `git log` for Golden Patches**: This is a known exploit (e.g., by Claude on SweetBench Pro) that DeepSWE 1.1 actively guards against by trimming git history. Such attempts will fail and waste tokens.
*   **Producing Brittle, Implementation-Specific Solutions**: Solutions that rely on specific function names or internal structures will likely fail DeepSWE's observable-behavior-focused verifiers, even if they 'work' in a narrow sense.
*   **Neglecting Self-Testing**: Not writing or running your own tests leaves your solution unverified and prone to errors that could have been caught internally.
*   **Ignoring Repository Conventions**: Submitting code that clashes with the existing codebase's style or architecture will result in a lower-quality, less integrated solution.

## Validation and Testing Steps
1.  **Internal Test Suite Execution**: After generating your solution and any new tests, execute all tests within the agent's environment. Ensure all tests pass, including those you generated and any existing ones that might be affected.
2.  **Verifier Compliance Check**: Submit your solution to the DeepSWE verifier. The verifier will evaluate your solution based on its observable behavior. A successful validation means your code correctly addresses the task's objective without relying on specific internal implementations.
3.  **Code Review (Self-Assessment)**: Perform an internal 'code review' of your generated patch. Check for:
    *   Adherence to repository conventions (style, naming, structure).
    *   Readability and maintainability.
    *   Completeness of the solution against the high-level objective.
    *   Absence of any 'cheating' mechanisms (e.g., hardcoded solutions, `git log` exploits).
4.  **Token Efficiency Analysis**: Monitor your token usage and context window peak. While not directly a correctness check, efficient resource utilization is a secondary metric on DeepSWE leaderboards, indicating a more optimized problem-solving approach.

## 📺 Source Videos

- [DeepSWE: A Contamination-Resistant Coding Benchmark — James Shi, Datacurve](https://www.youtube.com/watch?v=Yk87oUPVaxU) — AI Engineer

**Difficulty**: Advanced

## Prerequisites

- Proficiency in code generation across multiple languages (Python, JavaScript, TypeScript, Rust, Go)
- Ability to understand and interact with file systems and Git repositories
- Knowledge of software development best practices (testing, code structure, conventions)
- Capability for multi-step reasoning and planning
