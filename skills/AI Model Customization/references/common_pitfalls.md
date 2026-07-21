## Common Pitfalls
When customizing AI models, several common pitfalls can hinder performance.

### Overfitting
Fine-tuning on a narrow dataset can lead to overfitting, where the model performs well on training data but poorly on new data. Ensure the dataset is diverse and representative of the task.

### Latency Issues
Real-time applications may suffer from latency with reasoning models. Fine-tuning can reduce latency, but it's essential to balance performance and responsiveness.

### Cost and Maintenance
Fine-tuning involves costs in collecting examples, evaluating results, and avoiding regressions. Maintaining custom models as frontier models evolve can be challenging. Consider parameter-efficient methods like LoRA to mitigate these costs.

### Programmatic Grading
Reinforcement fine-tuning (RFT) requires programmatic grading of outputs. This method only works when there's a definitive right answer, limiting its applicability.

### Context Engineering
Poorly assembled context can mislead the model. Ensure context includes system prompts, relevant data, and format guidelines to guide the model effectively.

Avoiding these pitfalls ensures the customized model performs optimally for its intended use case.