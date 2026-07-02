# Practical Guide to Claude Cowork Implementation

## Setting Up Projects
1. Click "Create New Project" in the sidebar
2. Choose setup method:
   - From scratch (manual context)
   - Import from old Claude chat project
   - Use existing folder (recommended)
3. For folder-based projects:
   - Select the relevant folder on your computer
   - Name your project
   - Add instructions for Claude (role, scope, file usage)
   - Specify important context files
   - Set rules for asset creation/saving

Example YouTube project setup:
```
You are my YouTube assistant. Help with YouTube-related tasks including:
- Ideation
- Packaging
- Intro writing
- Script assistance
- Presentations

You have access to:
- Past YouTube transcripts (for tone/style)
- YouTube strategy doc
- ICP document

Rules:
- Save all created assets directly to the folder
- Mimic my tone from transcripts when writing scripts
```

## Working with Connectors
### For Native Integrations:
1. Go to Customize > Connectors
2. Browse available connectors
3. Click to connect and authenticate

### For MCP Servers:
1. Search "[Tool Name] MCP server" in Google
2. Follow documentation for setup instructions
3. Two setup methods:
   - Add remote server URL via "Add Custom Connector"
   - Edit config JSON file (Settings > Developer > Edit Config)

### When No MCP Exists:
1. Use the MCP builder skill:
   ```
   Claude, use the MCP builder skill to create an MCP server for [Tool Name]
   ```
2. Follow generated instructions to install

## Browser vs. Computer Control
Only use browser/computer control when:
- No connector or MCP exists
- You need one-time access
- Working with local software with specific workflows

Best Practice: Always prefer native connectors or MCP servers for efficiency.