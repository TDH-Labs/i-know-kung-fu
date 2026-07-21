---
description: A comprehensive skill for using Claude Co-Work to automate and enhance
  academic research workflows including literature reviews, presentation creation,
  and research gap analysis.
name: Academic Research Assistant with Claude Co-Work
tags:
- academia
- research
- literature review
- presentation
- research gaps
---

# Academic Research Assistant with Claude Co-Work

> A comprehensive skill for using Claude Co-Work to automate and enhance academic research workflows including literature reviews, presentation creation, and research gap analysis.

## Overview
Claude Co-Work transforms academic research through agentic workflows, verified data connectors, and reusable skills. This skill document outlines how to leverage these features for literature reviews, presentation creation, and research gap analysis. For foundational concepts, see [Core Concepts](references/core_concepts.md).

## Step-by-Step Workflow

1. **Initial Setup**
   - Install Claude desktop app (ensure sufficient disk space)
   - Configure essential settings as detailed in [Practical Guide](references/practical_guide.md)
   - Add academic connectors (Consensus, PubMed)

2. **Project Creation**
   ```
   1. Click 'Projects' → 'New Project'
   2. Name (e.g., "OPV Devices Review")
   3. Add instructions:
      "Academic project focusing on recent literature about OPV devices for indoor use. Prioritize peer-reviewed sources and identify seminal papers."
   4. Upload reference materials:
      - University writing guidelines
      - Previous literature review examples
   ```

3. **Literature Review Execution**
   ```
   Prompt: "Create an academic literature review about [TOPIC]. Focus on recent literature and seminal papers. Use connected databases for sourcing."
   
   Best Practice: Wait for agent questions (e.g., "How deep should the search go?") to refine output
   Pitfall Avoidance: Verify all citations link properly to Consensus/PubMed
   ```

4. **Presentation Generation**
   ```
   1. Upload paper PDF (must be on same drive)
   2. Prompt: "Turn this into a 10-minute presentation for my group meeting"
   3. Expected Output:
      - Structured slide deck
      - Key findings extraction
      - Speaker notes
   ```

5. **Research Gap Analysis**
   ```
   Invoke skill: /research_gap_finder
   Input: "My PhD project in [FIELD] focuses on [SPECIFIC AREA]"
   Output: List of underexplored research questions with supporting evidence
   ```

6. **Skill Creation**
   After successful task completion:
   ```
   Prompt: "Capture this workflow as a skill for future use"
   Follow skill creator prompts to define:
   - Input parameters
   - Quality checks
   - Output formatting
   ```

## Code/Prompt Templates

**Literature Review Starter**
```
Create an academic literature review about [TOPIC]. Requirements:
1. Include 5-7 seminal papers
2. Focus on last 5 years of research
3. Organize by these themes: [THEME1], [THEME2], [THEME3]
4. Use Consensus connector for verified sources
5. Format citations in [STYLE] style
```

**Presentation Conversion**
```
Convert this paper into a [LENGTH] presentation for [AUDIENCE]. Include:
1. Key findings slide
2. Methods overview
3. 3-5 main results slides
4. Future work suggestions
5. Speaker notes for each slide
```

## Best Practices
1. **File Management**: Keep all research files on the same drive as Claude installation
2. **Skill Development**: Create skills after 2-3 successful manual executions of a workflow
3. **Validation**: Always spot-check 20% of citations in generated literature reviews
4. **Timing**: Schedule long-running tasks (like weekly literature updates) during off-hours

## Common Pitfalls
1. **Cross-Drive Access**: Files not on Claude's drive won't be accessible (transcript example)
2. **Output Time**: Complex tasks take significantly longer than chat (10+ minutes for 14-page review)
3. **Skill Overuse**: Don't create skills for one-off tasks - reserve for truly repetitive workflows

## Validation Steps
1. **Citation Verification**: Sample 5-10 citations to confirm they:
   - Exist in source databases
   - Match the context used
2. **Content Accuracy**: For presentations, verify:
   - Key findings match paper abstract
   - Methods description is technically correct
3. **Skill Testing**: Run new skills 3 times with varied inputs to check consistency

For detailed skill creation methods, see [Skill Creation](references/skill_creation.md).

## 📺 Source Videos

- [Claude Cowork for Academics: Full Setup & Use Cases](https://www.youtube.com/watch?v=ldwjRjx8xIQ) — Andy Stapleton

**Difficulty**: Intermediate

## Prerequisites

- Claude Co-Work desktop app installed
- Basic understanding of academic research processes
