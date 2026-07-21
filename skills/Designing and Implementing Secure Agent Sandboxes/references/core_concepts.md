### Core Concepts

Agent sandboxes are isolated environments designed to securely execute untrusted code. They are crucial in AI-driven applications like ChatGPT and Codex, where models may generate and execute code to solve tasks. The primary goal of a sandbox is to ensure that the executed code cannot exploit vulnerabilities in the host system or access unauthorized data.

#### Isolation Mechanisms

- **Containers**: Use namespaces and cgroups to isolate resources. While containers provide some level of isolation, they still share the host kernel, making them vulnerable to kernel exploits.
- **MicroVMs**: Provide hardware-level isolation by running a separate Linux kernel in a virtual machine. This ensures that even if the guest kernel is compromised, the host remains secure.

#### Persistence

Persistence is essential for maintaining state across sandbox sessions. Incremental snapshotting allows efficient saving and restoring of sandbox states, ensuring data durability and reliability.

#### Orchestration

Orchestration involves managing sandboxes across multiple nodes in a cloud environment. A control plane and scheduler are used to route sandboxes based on load and region, ensuring low latency and high reliability.

For more detailed information, refer to the [Practical Guide](references/practical_guide.md) and [Code Examples](references/code_examples.md).