---
description: Skill for connecting Claude AI to external services like Gmail, Google
  Calendar, and Notion through Claude Connectors and Zapier MCP to automate workflows
  and enhance productivity.
name: Claude Connectors Integration
tags:
- Claude
- Connectors
- Zapier
- Automation
- Gmail
- Google Calendar
- Notion
---

# Claude Connectors Integration

> Skill for connecting Claude AI to external services like Gmail, Google Calendar, and Notion through Claude Connectors and Zapier MCP to automate workflows and enhance productivity.

## Overview
This skill enables you to connect Claude to external services for enhanced automation capabilities. See [Core Concepts](references/core_concepts.md) for foundational knowledge.

## Step-by-Step Workflow
1. **Access Connectors Menu**
   - Click profile icon → Customize → Connectors

2. **Select Service to Connect**
   - Choose from available options (Gmail, Calendar, etc.)
   - For extended options, select Zapier MCP

3. **Authenticate Service**
   - Follow OAuth flow for each service
   - Example Gmail auth prompt:
     ```
     [Gmail Authentication]
     Please log in to your Google account to continue
     Allow Claude to:
     [✓] Read your emails
     [✓] Send emails on your behalf
     ```

4. **Verify Connection**
   - Test with simple query: "Are there any unread emails?"

5. **Begin Automation**
   - Use natural language prompts to interact with connected services
   - Sample prompt template:
     ```
     "Draft a professional response to [email subject] that includes:
     - Acknowledgement of their message
     - Answer to their question about [topic]
     - Availability for follow-up next week"
     ```

## Best Practices
- Start with read-only permissions before granting write access
- Use specific date ranges in calendar queries ("this week" vs "recently")
- For Zapier, pre-configure common workflows in your Zapier account

## Common Pitfalls
1. **Over-permissioning**: Granting full access when only read is needed
   - Fix: Adjust permissions in service settings
2. **Vague Queries**: "Check my emails" is less effective than "Show unread emails from boss"
3. **Zapier Timeouts**: Complex automations may exceed execution windows
   - Solution: Break into smaller Zaps

## Validation Steps
1. Test basic retrieval ("Show my next meeting")
2. Verify action commands ("Schedule a meeting")
3. Check error handling for:
   - Invalid queries
   - Service outages
   - Permission errors

For detailed implementation examples, see [Practical Guide](references/practical_guide.md).

## 📺 Source Videos

- [How to Use Claude Connectors](https://www.youtube.com/watch?v=1-Rr3iadlOs) — Kevin Stratvert

**Difficulty**: Intermediate

## Prerequisites

- Basic understanding of Claude AI
- Access to Claude Pro account
- Accounts on services to connect (e.g., Gmail, Notion)
