### Practical Guide

This guide provides step-by-step instructions for implementing secure agent sandboxes, focusing on microVMs and persistence.

#### Step 1: Understand the Need for Sandboxes

Sandboxes are necessary for securely executing untrusted code. Traditional methods like `fork` and `exec` are insufficient due to security vulnerabilities.

#### Step 2: Choose the Right Isolation Mechanism

Decide between containers and microVMs based on your security and performance needs. Containers offer resource isolation but still share the host kernel, while microVMs provide hardware-level isolation.

#### Step 3: Implement MicroVM-Based Sandboxes

Use microVMs for enhanced security. Follow these steps:

1. Fork a Cloud Hypervisor binary process.
2. Expose an API over a Unix domain socket.
3. Call the `create` API to set up the root FS, kernel, CPU, and memory.
4. Start the microVM.

#### Step 4: Enable Persistence

Implement disk persistence to ensure data durability across sandbox sessions. Use incremental snapshotting to efficiently save and restore sandbox states.

#### Step 5: Orchestrate Sandboxes Across Nodes

Use a control plane to manage sandboxes across multiple nodes. Implement a scheduler to route sandboxes based on load and region.

For more detailed information, refer to the [Core Concepts](references/core_concepts.md) and [Code Examples](references/code_examples.md).