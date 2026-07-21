### Common Pitfalls

This document outlines common pitfalls when designing and implementing secure agent sandboxes.

#### Noisy Neighbors

Using `fork` and `exec` directly can lead to noisy neighbor issues, where one sandbox consumes all resources, bringing down the entire node.

#### Kernel Exploits

Containers still share the host kernel, making them vulnerable to kernel exploits. Always prefer microVMs for hardware-level isolation.

#### Performance Overheads

MicroVMs introduce performance overheads, especially when switching between guest and host contexts. Be aware of these trade-offs and optimize accordingly.

#### Security Testing

Regularly test sandboxes for vulnerabilities, including kernel exploits and privilege escalation. Ensure that your sandboxes are secure before deploying them in production.

#### Persistence Testing

Verify that snapshots are correctly saved and restored, ensuring data durability across sessions. Implement incremental snapshotting to reduce storage and latency.

For more detailed information, refer to the [Practical Guide](references/practical_guide.md) and [Code Examples](references/code_examples.md).