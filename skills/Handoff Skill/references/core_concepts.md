# Core Concepts of Handoff Skill

The Handoff Skill is designed to facilitate seamless transitions between AI agents by creating a temporary document that captures the essence of the current conversation. This document serves as a bridge, allowing a fresh agent to continue work without losing context.

Key concepts:
1. **Temporary Nature**: The handoff document is not meant for long-term storage. It exists in a temporary directory with a standardized naming convention (e.g., mic_temp_t_handoff).
2. **Context Preservation**: The document must capture not just the content, but also the 'vibe' and intent of the original conversation.
3. **Skill Suggestion**: The handoff should recommend which skills the next agent should use to continue the work effectively.
4. **Artifact Referencing**: Instead of duplicating content, the handoff should reference existing artifacts by path or URL.
5. **Argument Handling**: If the user provides arguments, these should be treated as focus areas for the next session and the document should be tailored accordingly.

Example Use Cases:
- Moving from a planning session to implementation
- Transitioning between different types of work (e.g., from design to coding)
- Creating sub-agent workflows where specialized agents handle specific tasks