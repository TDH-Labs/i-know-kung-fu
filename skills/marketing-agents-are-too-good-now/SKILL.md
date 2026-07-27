---
description: >-
  Build and deploy AI marketing agents that research, create, publish, and optimize
  ad campaigns autonomously — based on the Cody Schneider framework from the Greg Isenberg podcast.
name: marketing-agents-are-too-good-now
tags:
- marketing agents
- Facebook ads
- data pipeline
- data warehouse
- Facebook Marketing API
- ad creative generation
- autonomous decision-making
- agentic marketing
- agent jockey
- Andromeda
---

# Agentic Marketing Teams

> Build AI marketing agents that research pain points, generate ad creative, publish to Facebook Ads, and optimize in a continuous feedback loop — all powered by a unified data warehouse.

**By Cody Schneider** (CompaniesGraph) × **Greg Isenberg** — https://youtu.be/U2hogriGmEw

## What is a Marketing Agent?

A real marketing agent has **three essential components:**

1. **Unified data** — access to all business data via a data pipeline and warehouse (Airbyte → ClickHouse)
2. **Autonomous decision-making** — operates on a cadence with a thinking loop, making decisions off live data
3. **Cloud-hosted code** — code running in the cloud, not a linear Zapier workflow

## The Complete Agent Workflow

### Step 1: Research Pain Points
Scrape Reddit for real customer complaints. Use Perplexity for quick synthesis. Rank by frequency.

### Step 2: Generate Creative
Kai AI (images/video), Google Nano Banana (statics), HeyGen (AI avatar UGC), Seedance (emerging video). Verify brand compliance with a vision model.

### Step 3: Publish to Facebook Ads
Agent creates ad sets and ads via Marketing API. 2 ad sets/day, 5 ads/ad set.

### Step 4: Monitor & Optimize
2-3 day learning window. Turn off worst performers, keep winners live. Winners pool competes for budget.

### Step 5: Feedback Loop
Database of prompts, scripts, and performance data. Agent analyzes what's working and generates more like the best performers.

## Solving the Entropy Problem
Marketing agents get stuck thinking the same way. Two solutions:
1. **Competitor Ad Library** — Pull ads via Facebook Ads Library API, introduce new "DNA"
2. **YouTube/Podcast Transcripts** — Mine niche channels for fresh insights

## Infrastructure
- **Data Pipeline:** Airbyte (open source, self-hosted)
- **Data Warehouse:** ClickHouse (open source, self-hosted)
- **Agent Hosting:** Railway, Heroku, or any cloud provider
- **FB API:** Write-only (publish, turn off, promote). No bulk data pulls.

## Key Principles
1. Marketing is continuous, not campaign-based
2. Test 10-15-20 variations of the same ad with different positioning
3. Let the market tell you what works — don't impose ideas, test them
4. Start with a human in the loop, then graduate to full autonomy

## Quick Start
1. Research pain points
2. Set up Airbyte → ClickHouse
3. Connect data sources (FB Ads, GA, Stripe, CRM)
4. Build agent with thinking loop
5. Connect FB Marketing API (write-only)
6. Set creative pipeline (image + video)
7. Set 2-3 day optimization cadence
8. Implement entropy prevention
9. Start with 2 ad sets/day, 5 ads/ad set

## References
- **Cody Schneider** — CompaniesGraph (companiesgraph.com)
- **Source video:** https://youtu.be/U2hogriGmEw
