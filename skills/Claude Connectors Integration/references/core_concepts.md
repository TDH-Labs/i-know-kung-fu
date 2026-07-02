# Core Concepts of Claude Connectors

Claude Connectors are integration tools that allow Claude AI to interact with external services like email clients, calendars, and productivity apps. This enables Claude to perform actions like reading emails, scheduling events, or managing tasks directly within your conversations.

Key capabilities include:
- **Service Integration**: Connect to popular services like Gmail, Google Calendar, Notion
- **Data Access**: Read and summarize information from connected accounts
- **Action Automation**: Perform actions like drafting emails or creating calendar events
- **Extended Reach**: Through Zapier MCP, access 9,000+ additional apps

Architecture:
1. Authentication layer handles OAuth with services
2. Permission system controls data access levels
3. API translation layer converts between Claude's interface and service APIs

Security features include:
- Token-based authentication
- Session-limited access
- Explicit user permissions for each action

Common use cases:
- Email triage and response drafting
- Calendar management
- Task synchronization across platforms
- Data retrieval from connected apps