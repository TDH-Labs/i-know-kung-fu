### Core Concepts of Hermes Agent
Hermes Agent is built on five main pillars that define its functionality and capabilities:

1. **Memory**: Hermes carries small, durable context across sessions using `user.md` and `memory.md` files. These files store user preferences, environments, and project contexts, ensuring Hermes wakes up with relevant information.

2. **Skills**: Skills are reusable playbooks for tasks. They are stored in `skill.md` files and invoked based on the task at hand. Skills ensure consistent execution of tasks, much like following a recipe.

3. **Soul**: The `soul.md` file shapes the personality of Hermes Agent. It allows customization of the assistant's tone and behavior, making it unique for different users or tasks.

4. **Cron**: Cron jobs turn Hermes from reactive to proactive by scheduling automations. These jobs run isolated sessions at specified times, executing tasks without inheriting current session context.

5. **Self-Improving Loop**: Hermes improves over time by persisting useful experiences as memory, skills, and searchable history. This loop ensures continuous enhancement based on user feedback and task execution.

Understanding these pillars is crucial for effectively managing and leveraging Hermes Agent's capabilities. For practical applications and examples, refer to [Practical Guide](references/practical_guide.md) and [Code Examples](references/code_examples.md).