# Core Concepts of Claude Cowork

## File Access
Claude Cowork allows direct access to folders on your computer, enabling persistent context for your projects. This means:
- Claude can read, create, edit, and update files directly in your designated folders
- No more manual copying and pasting of context documents
- Changes made by Claude are saved directly to your filesystem

Example: When working on YouTube content, you can give Claude access to a folder containing your YouTube strategy, past transcripts, and ICP documents. This provides automatic context for tasks like ideation, scripting, and research.

## Projects
Projects in Claude Cowork are containers for related tasks with shared context and memory. Each project can:
- Be connected to a specific folder
- Maintain project-specific memory (like tone of voice rules)
- Organize all related chats in one place
- Include scheduled tasks

Projects differ from standard chats by providing persistent, organized context that carries across multiple sessions.

## Connectors
Connectors enable Claude to interact with external software and services. There are several types:
1. Native connectors (built-in integrations)
2. MCP servers (bundled API calls for specific tools)
3. Browser access (less efficient fallback option)
4. Computer control (vision-based, token-heavy)

The hierarchy of preference is: native connectors > MCP servers > browser > computer control.

## Skills
Skills are instruction sets that teach Claude how to perform specific processes. They consist of:
- A skill.md file (core instructions)
- Optional reference files (context, examples, style guides)
- Optional code scripts (for API calls or functions)

Skills use progressive disclosure to manage context, only loading relevant parts when needed. This allows a single agent to access thousands of specialized skills.

## Testing and Optimization
Claude includes tools for skill evaluation and improvement:
- Eval Viewer agents for analyzing skill performance
- Benchmarking scripts
- AB testing capabilities

These tools help optimize skills for specific criteria like speed, token usage, or output quality.