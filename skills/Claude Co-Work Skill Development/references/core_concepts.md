# Core Concepts of Claude Co-Work

## File Access and Projects
Claude Co-Work revolutionizes AI interaction by allowing persistent file access. When you grant Claude access to a folder, it can:
- Read all documents in that folder for context
- Create and edit files directly in the folder
- Maintain project-specific memory

Projects are organizational units that bundle:
- Connected folders
- Project-specific memory
- Organized chat history
- Scheduled tasks

Example: A YouTube project might include:
- A folder with transcripts, strategy docs, and ICP
- Memory rules about tone of voice
- Scheduled content generation tasks

## Connectors and Integration
Claude connects to external tools through:
1. Native connectors (pre-built integrations)
2. MCP servers (bundled API packages)
3. Browser access (fallback option)
4. Computer control (least efficient)

Best practices:
- Always prefer native connectors first
- Search for MCP servers before using browser
- Reserve computer control for special cases

## Skills Architecture
Skills are modular capabilities that include:
- skill.md (core process instructions)
- Reference files (context, examples, style guides)
- Code scripts (for API calls or functions)

Skills use progressive disclosure:
1. Only metadata (name/description) is in memory
2. skill.md loads when triggered
3. Reference files load only when needed

This allows one agent to access thousands of skills without context overload.