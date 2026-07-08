---
description: A comprehensive skill for automating daily workflows using Claude Cowork,
  including email triage, content creation, research, and dashboard generation.
name: Claude Cowork Workflow Automation
tags:
- workflow automation
- Claude Cowork
- email triage
- content creation
- research automation
- dashboard generation
---

# Claude Cowork Workflow Automation

> A comprehensive skill for automating daily workflows using Claude Cowork, including email triage, content creation, research, and dashboard generation.

## Overview
This skill transforms Claude from a basic chatbot into an automated workflow assistant that handles email triage, content creation, research, and business intelligence. By implementing these workflows, you can shift from being a creator to an approver, saving hours each day. For foundational concepts, see [Core Concepts](references/core_concepts.md).

## Step-by-Step Workflow

1. **Initial Setup**
   - Connect Gmail and calendar via Manage Connectors (OAuth flow)
   - Create a 'content voice' project with your style guidelines
   - Upload 5-10 reference documents representing your best work

2. **Daily Brief Automation**
   - Create scheduled task for weekdays at 7:00 AM
   - Use prompt template from [Code Examples](references/code_examples.md)
   - Set output location to your daily brief folder

3. **Email Triage System**
   - Implement the email sorting prompt twice daily (7 AM and 1 PM)
   - Review and adjust categorization rules weekly
   - Keep 'draft only' mode enabled for first two weeks

4. **Content Creation Workflow**
   - Use /post_from_note skill within your content project
   - Provide raw notes or voice memo transcripts
   - Expect to perform one round of edits on first drafts

5. **Research Automation**
   - Create dedicated research project with Chrome integration
   - Use structured brief template for consistent results
   - Verify critical facts against primary sources

6. **Business Dashboard**
   - Connect data sources (CSV, Stripe, bank feeds)
   - Generate initial dashboard and validate numbers
   - Schedule monthly refreshes with new data

## Best Practices
- Start small with 1-2 automations before expanding (see [Common Pitfalls](references/common_pitfalls.md))
- Maintain a library of approved outputs as additional training data
- Schedule weekly reviews to refine prompts and workflows
- Use the mobile Dispatch feature for on-the-go task creation

## Validation Steps
1. For email drafts: Spot-check 20% of auto-generated replies for tone accuracy
2. For research reports: Verify 3-5 key facts against source material
3. For dashboards: Cross-check totals against original data sources
4. For content: Compare automated drafts to your manual work for style consistency

## Implementation Notes
- All prompt templates are available in [Code Examples](references/code_examples.md)
- For detailed setup instructions, consult the [Practical Guide](references/practical_guide.md)
- Be mindful of the limitations and solutions outlined in [Common Pitfalls](references/common_pitfalls.md)

## 📺 Source Videos

- [6 INSANE Claude Cowork Use Cases to Save Hours (AI Workflow Automation)](https://www.youtube.com/watch?v=skU1-k7_wWE) — AI Master

**Difficulty**: Intermediate

## Prerequisites

- basic familiarity with Claude Cowork
- access to Claude Cowork Pro or Max plan
- Gmail account for email automation
