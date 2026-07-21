---
description: A comprehensive system for transforming personal research notes and external
  sources into a queryable, evolving knowledge base using AI agents and file-based
  indexing.
name: AI Research OS Implementation
tags:
- knowledge management
- second brain
- research assistant
- vector database alternative
- obsidian integration
- personal wiki
---

# AI Research OS Implementation

> A comprehensive system for transforming personal research notes and external sources into a queryable, evolving knowledge base using AI agents and file-based indexing.

## Overview

This skill transforms scattered research materials into an organized, queryable knowledge base using a file-based approach. Unlike traditional RAG systems, it emphasizes:

- **Personal Context**: Anchors research in your existing notes and values ([Core Concepts](references/core_concepts.md))
- **Progressive Disclosure**: Minimizes token usage through hierarchical data access
- **Living Documentation**: Evolves with each interaction through automatic wiki updates

## Workflow

1. **Initialize Project**
   - Create project directory with standard structure ([Workflow Guide](references/workflow_guide.md#1-initial-setup))
   - Connect relevant data sources (Obsidian, Readwise, GitHub)

2. **Ingest Sources**
   - Add materials via CLI or API:
     ```bash
     python ingest.py --type=youtube --url=https://youtu.be/agent_tutorial
     ```
   - System generates summaries and updates index.yaml

3. **Conduct Research**
   - Run targeted queries with depth control:
     ```python
     research("attention mechanisms", depth="light")
     ```
   - Agent follows [query protocol](references/core_concepts.md#progressive-disclosure)

4. **Review Outputs**
   - Check generated wiki pages in Obsidian
   - Verify automatic concept linking
   - Monitor open_questions/ directory

5. **Iterate**
   - Add follow-up questions to expand wiki
   - Re-index when adding significant new sources

## Best Practices

- **Start Small**: Begin with 2-3 key sources before scaling up
- **Depth Control**: Use 'light' research mode for 80% of cases
- **Source Diversity**: Combine codebases, articles, and videos
- **Regular Review**: Audit open questions weekly

## Common Pitfalls

1. **Over-Indexing**
   - Example: Running 'deep' research on broad topics
   - Fix: Scope topics narrowly ("Transformer memory" vs "AI")

2. **Stale Derivatives**
   - Example: Not updating comparisons when new research emerges
   - Fix: Set calendar reminders for key topics

3. **Source Overload**
   - Example: Adding 100+ papers without curation
   - Fix: Pre-filter with [ranking algorithm](references/code_examples.md#source-ranking-algorithm)

## Validation

1. **Completeness Check**
   - Verify all expected concepts appear in wiki/
   - Confirm bidirectional links between related topics

2. **Freshness Test**
   - Check ingested_date in index.yaml for key sources
   - Run timestamp comparison:
     ```python
     if (now - ingested_date) > timedelta(days=90):
         trigger_reindex()
     ```

3. **Query Accuracy**
   - Compare agent responses against source material
   - Track precision/recall for sample questions

## Maintenance

- Archive stale projects to `/research_archive/`
- Prune low-value derivatives quarterly
- Update connectors when APIs change

For complete implementation details, see:
- [Core Architecture](references/core_concepts.md)
- [Workflow Examples](references/workflow_guide.md)
- [Code Templates](references/code_examples.md)

## 📺 Source Videos

- [Turn 10,994 Notes Into Memory - Paul Iusztin, Decoding AI & Louis-François Bouchard, Towards AI](https://www.youtube.com/watch?v=ZRM_TfEZcIo) — AI Engineer

**Difficulty**: Advanced

## Prerequisites

- Basic Python knowledge
- Familiarity with markdown
- Experience with CLI tools
- Understanding of RAG concepts
