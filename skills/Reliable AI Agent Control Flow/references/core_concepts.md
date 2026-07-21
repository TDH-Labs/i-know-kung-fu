# Core Concepts

### State Machines

A state machine is a mathematical model used to design systems with a finite number of states. In the context of AI agents, a state machine helps manage the control flow by defining distinct steps and transitions between them.

### Harness Engineering

Harness engineering involves creating a framework that directs the actions of an AI model. Instead of letting the model decide the next steps, the harness manages state transitions and validates the model's outputs. This ensures reliability and efficiency.

### Neural Contracts

Neural contracts specify the input and expected output for each step in the workflow. They confine the model to performing specific actions, reducing the risk of deviations.

### Smaller Models

Using smaller, cost-effective models guided by a harness can save costs and improve latency. The harness ensures the model performs at the expected level, even with reduced reasoning capabilities.

### Logging and Monitoring

Comprehensive logging helps track state transitions and model outputs, making it easier to debug and ensure the workflow runs as expected.

### Validation

Unit testing, integration testing, and continuous monitoring are essential for validating the reliability of the control flow.

For practical implementation, refer to the [Practical Guide](references/practical_guide.md).