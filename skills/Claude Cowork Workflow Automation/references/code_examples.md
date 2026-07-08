# Code Examples and Prompt Templates for Claude Cowork

## Email Triage Prompt
```
Sort the last 12 hours of unread mail into three categories:
1. Reply Today: Requires response today. Draft a reply in my voice (concise, professional but friendly). Include:
   - Acknowledgment of their message
   - Clear answer to their question
   - Any necessary follow-up questions
2. FYI: Important but doesn't require immediate response
3. Noise: Low-priority or promotional content that can be archived

Present results in a table with columns: Category, Sender, Subject, Action (draft reply or none)
```

## Content Creation Skill (/post_from_note)
```
Transform this raw note into a polished blog post draft:
- Use my established voice from project references
- Structure with: compelling hook, 3-5 key points, strong conclusion
- Avoid: corporate jargon, cliché openings, fluff
- Target length: 800-1000 words

Raw note: [paste content here]
```

## Research Brief Template
```
Research Topic: [clear subject]
Audience: [describe who will consume this]
Depth Level: [overview, intermediate, deep dive]
Key Questions to Answer:
1. [primary question 1]
2. [primary question 2]
3. [primary question 3]

Requirements:
- Only use sources from the last 90 days
- Cross-check facts against official documentation
- Highlight any conflicting information
- Format as HTML report with: executive summary, key findings, comparison tables, sources
```

## Dashboard Generation Prompt
```
Create an interactive HTML dashboard from this data with:
1. 12-month revenue trend chart
2. Top customer segments by growth
3. Anomaly detection highlighting unusual patterns
4. 'Watch This Week' section flagging 3 key metrics

Design Requirements:
- Mobile-responsive layout
- Hover tooltips on all charts
- Tab navigation between sections
- Visual highlights on important trends

Data: [attach CSV or connect to data source]
```