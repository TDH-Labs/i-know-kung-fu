# Core Concepts

## Introduction to Claude Connectors
Claude Connectors are tools that allow Claude to interact with various external services such as Gmail, Google Calendar, Notion, and more. These connectors enable Claude to perform tasks like reading emails, summarizing threads, drafting responses, and more.

## Types of Connectors
There are over 200 different services available through Claude Connectors. Some of the most popular include Canva, Microsoft 365, Figma, Notion, Gmail, and Google Drive.

## Permissions and Security
By default, Claude has access to read-only tools. For actions that modify your account, such as creating an email draft, you'll need to grant explicit permission. It's important to review and adjust these settings as needed.

## Extending Functionality with Zapier MCP
Zapier MCP allows Claude to connect to thousands of additional apps and perform more complex actions. This includes sending emails directly, which is not possible with the native Gmail connector.

## Best Practices
- **Minimal Permissions**: Only grant the permissions necessary for the tasks you want Claude to perform.
- **Regular Reviews**: Regularly review the actions taken by Claude to ensure they align with your expectations.

## Common Pitfalls
- **Over-Permissioning**: Granting too many permissions can lead to unintended actions.
- **Ignoring History**: Failing to review the history of actions can result in unnoticed errors.

For more detailed information, refer to the [Practical Guide](references/practical_guide.md) and [Code Examples](references/code_examples.md).