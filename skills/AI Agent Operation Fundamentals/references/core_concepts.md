# Core Concepts of AI Agent Operation

Modern AI agents operate through five fundamental components that enable autonomous task execution:

1. **agents.md**: A markdown configuration file that defines project-specific rules and commands for the agent. This acts as a README specifically for AI agents, containing instructions like test commands to run before commits or code style guidelines. Multiple agents.md files can exist in nested directories, with closer files overriding parent configurations.

2. **Agent Skills**: Modular task capabilities stored in folders containing a skill.md file and supporting resources. Each skill has metadata describing when it should be invoked (e.g., "when user wants to create PowerPoint slides"). Skills remain dormant until needed, preserving context window space.

3. **Model Context Protocol (MCP)**: A standardized interface for connecting agents to external tools and data sources. MCP servers wrap APIs (like Notion or Stripe) into a uniform interface that any MCP-compatible agent can use, eliminating the need for custom connectors per tool.

4. **Agent-to-Agent (A2A)**: A communication protocol where agents publish 'agent cards' describing their capabilities. This enables seamless delegation between specialized agents (e.g., a procurement agent handing contracts to a finance agent for approval).

5. **Subagents**: Child agents spawned by a main agent to handle parallelizable work or tasks requiring separate context windows. Each subagent operates independently and returns results to the parent, enabling scalable processing of large workloads.

These components work together to create flexible, powerful agent systems capable of complex workflows while maintaining clean context management and standardized interfaces.