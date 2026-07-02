---
description: This skill enables you to create personalized dashboards with live data
  pulled from multiple software sources using Claude's live artifacts feature. It
  covers setup, best practices, pitfalls, and validation steps.
name: Building Live Artifacts with Claude
tags:
- live artifacts
- Claude
- dashboard
- data visualization
- AI insights
---

# Building Live Artifacts with Claude

> This skill enables you to create personalized dashboards with live data pulled from multiple software sources using Claude's live artifacts feature. It covers setup, best practices, pitfalls, and validation steps.

## Overview
Live artifacts in Claude allow you to build personalized dashboards that pull live data from multiple software sources. These dashboards automatically refresh with up-to-date data and can provide AI-driven insights. This skill will guide you through the process of creating these dashboards, avoiding common pitfalls, and validating their effectiveness.

## Step-by-Step Workflow
1. **Define the Purpose of Your Dashboard**: Clearly articulate what you want the dashboard to achieve. For example, a marketing dashboard might track conversions across different offers.
2. **Identify Data Sources**: Determine which software connectors (e.g., YouTube, Bitly, Posthog) you need to pull data from.
3. **Specify Data Requirements**: Define what specific data you need from each connector to avoid unnecessary scope creep.
4. **Set AI Interpretation Rules**: Decide how AI should interpret the data, such as providing strategic insights or prioritizing tasks.
5. **Build the Artifact**: Use Claude's built-in tool to create the live artifact by describing your requirements and connecting the necessary data sources.
6. **Test and Validate**: Ensure the dashboard updates correctly and provides the expected insights.

## Code/Prompt Templates
```markdown
**Prompt Template for Building a Live Artifact**
1. What is the purpose of this dashboard?
2. Which connectors should pull data?
3. What specific data do you need from each connector?
4. How should AI interpret the data?
5. What brand guidelines should it follow?
6. What actions should the artifact take?
7. What should this dashboard not do?
```

## Best Practices
- **Scope Narrowly**: Focus on specific use cases to avoid creating overly broad and slow dashboards.
- **Clear Communication**: Clearly communicate your requirements to Claude to avoid hard-coded dashboards that are not useful.
- **Regular Updates**: Ensure the dashboard refreshes regularly to provide up-to-date insights.

## Common Pitfalls
- **Overloading Data**: Pulling data from too many connectors can slow down the dashboard.
- **Unclear Requirements**: Failing to clearly define what you need can result in a dashboard that doesn't meet your needs.
- **Ignoring AI Interpretation**: Not setting rules for AI interpretation can lead to less useful insights.

## Validation Steps
1. **Check Data Accuracy**: Ensure the data pulled from each connector is accurate and up-to-date.
2. **Test AI Insights**: Verify that the AI provides meaningful and actionable insights.
3. **Monitor Performance**: Ensure the dashboard performs well and refreshes quickly.

For more detailed guidance, refer to the [Core Concepts](references/core_concepts.md), [Practical Guide](references/practical_guide.md), and [Code Examples](references/code_examples.md).

## 📺 Source Videos

- [Live Artifacts Just 10x'd Claude Cowork (Real Use Cases)](https://www.youtube.com/watch?v=PwLqKIGA25c) — Ben AI

**Difficulty**: Intermediate

## Prerequisites

- Basic familiarity with Claude
- Understanding of data connectors and MCPs
- Experience with dashboard creation
