# Practical Guide

### Defining the State Machine

1. **Identify Steps**: List the distinct steps in your workflow (e.g., intro, teach, check, grade, advance, wrap).
2. **Define Transitions**: Specify the conditions for transitioning between steps.
3. **Implement Logic**: Write code to manage state transitions based on the model's outputs.

### Designing the Harness

1. **Create Framework**: Develop a framework that manages state transitions and validates model outputs.
2. **Integrate Model**: Use the harness to guide the model's actions, ensuring it adheres to neural contracts.
3. **Log Transitions**: Implement logging to track state transitions and model outputs.

### Implementing Neural Contracts

1. **Specify Inputs**: Define the input for each step.
2. **Define Outputs**: Specify the expected output for each step.
3. **Validate Outputs**: Ensure the model's outputs match the expected outputs.

### Using Smaller Models

1. **Select Model**: Choose a smaller, cost-effective model (e.g., Haiku 4.5).
2. **Guide Actions**: Use the harness to guide the model's actions, ensuring it performs at the expected level.

### Logging and Monitoring

1. **Implement Logging**: Add logging to track state transitions and model outputs.
2. **Monitor Logs**: Continuously monitor the logs to detect and fix any issues.

### Testing and Validation

1. **Unit Testing**: Test each state transition and neural contract individually.
2. **Integration Testing**: Run the entire workflow with various scenarios to ensure reliability.
3. **Continuous Monitoring**: Continuously monitor the workflow to ensure it runs as expected.

For more detailed information, refer to the [Core Concepts](references/core_concepts.md).