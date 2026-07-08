# Core Concepts of Task Fidelity Scaling

Task fidelity scaling is a methodology for improving AI model training by ensuring that the tasks used for training and benchmarking meet high-quality standards. The core premise is that the quality of data (and by extension, tasks) is critical to the performance improvements of AI models.

## Key Principles
1. **Task Quality Criteria**: Tasks must be:
   - Achievable: The task can be completed by the model
   - Non-trivial: The task presents meaningful difficulty
   - Functionally correct: The task logic works as intended
   - Environmentally reliable: The execution environment is stable

2. **Quality Impact**: High-quality tasks lead to:
   - More tool calls (demonstrating engagement)
   - Lower pass rates (indicating genuine difficulty)
   - More output tokens (showing deeper reasoning)
   - Cleaner failure modes (failures that provide meaningful signals)

3. **Empirical Validation**: The Snorkel team demonstrated that models trained with high-quality tasks showed 6% improvement compared to just 1% with low-quality tasks, proving the 5x uplift from quality focus.

## Implementation Context
This approach is particularly valuable for:
- Agentic terminal bench-style tasks
- Containerized environments
- Reproducible, isolated task execution
- Parallelized rollouts

The methodology emphasizes that while architectural changes and harness variations matter, data quality remains the central determinant of training outcomes.