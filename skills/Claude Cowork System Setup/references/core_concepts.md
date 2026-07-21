## Core Concepts

The Claude Cowork system revolves around three core concepts: persistent memory, context-aware responses, and efficient task management. Persistent memory is achieved through the `memory.md` file, which stores information between sessions. Context-aware responses are enabled by the `claude.md` file, which acts as the instruction manual for Co-work. Efficient task management is facilitated by organizing workstations, each with its own set of rules and resources.

### Persistent Memory
The `memory.md` file is crucial for maintaining continuity between sessions. It contains sections for active projects and general memory entries. When you tell Co-work to remember something, it writes that information to `memory.md`, ensuring it can be recalled in future sessions.

### Context-Aware Responses
The `claude.md` file governs how Co-work behaves. It includes instructions for reading `memory.md` at the start of each session and for routing tasks to the appropriate workstation. This ensures that Co-work always has the necessary context to provide relevant responses.

### Efficient Task Management
Workstations are specialized folders that handle specific areas of your life (e.g., email, personal finances). Each workstation has its own `claude.md`, `memory.md`, and `resources` folder, allowing for task-specific rules and resources. This modular approach keeps the system organized and efficient.