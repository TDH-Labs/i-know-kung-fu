---
description: >-
  Build and deploy AI marketing agents that autonomously research, create, publish,
  and optimize ad campaigns — entirely self-hosted using open-source infrastructure.
  Replaces Kai AI, Nano Banana, HeyGen, Seedance, Perplexity, and Railway/Heroku
  with free, self-hosted alternatives while keeping the full Cody Schneider framework.
name: marketing-agents-are-too-good-now
tags:
- marketing agents
- Facebook ads
- data pipeline
- open-source
- self-hosted
- ComfyUI
- Stable Diffusion
- Airbyte
- ClickHouse
- Coolify
- agentic marketing
- Andromeda
- ad automation
---

# Agentic Marketing Teams — Fully Self-Hosted Edition

> Build AI marketing agents that research pain points, generate ad creative, publish to Facebook Ads, and optimize in a continuous feedback loop — all on **self-hosted, open-source infrastructure**. No vendor lock-in, no surprise bills, no API dependency.

**Based on:** Cody Schneider (CompaniesGraph) × Greg Isenberg — https://youtu.be/U2hogriGmEw

---

## Architecture Overview

```
┌──────────────────────────────────────────────────────────────────┐
│                     AGENT ORCHESTRATOR                           │
│          (Python loop — hosted on Coolify / Docker VPS)          │
└──────────────────────────────────────────────────────────────────┘
         │                      │                      │
         ▼                      ▼                      ▼
┌─────────────────┐  ┌────────────────────┐  ┌──────────────────┐
│   DATA LAYER    │  │   CREATIVE LAYER   │  │  PUBLISH LAYER   │
│                 │  │                    │  │                  │
│  Airbyte ──►    │  │  ComfyUI ──►       │  │  FB Marketing    │
│  ClickHouse     │  │  Stable Diffusion  │  │  API (write-only)│
│  (self-hosted)  │  │  FLUX / SDXL       │  │                  │
│                 │  │  AnimateDiff       │  │                  │
│  SearXNG ──►    │  │  Wav2Lip + Coqui   │  │                  │
│  Research       │  │  TTS (self-hosted) │  │                  │
└─────────────────┘  └────────────────────┘  └──────────────────┘
```

**Key principle:** The only non-switchable dependency is the Facebook Marketing API — because that's the ad channel itself. Everything else runs on your own hardware.

---

## What is a Marketing Agent? (Refresher)

A real marketing agent has **three essential components:**

| Component | Description | Self-Hosted Solution |
|-----------|-------------|---------------------|
| **Unified data** | All business data in one place | Airbyte → ClickHouse (both open-source) |
| **Autonomous decision loop** | Thinking cadence off live data | Your own Python/LLM agent code |
| **Cloud-hosted code** | Runs 24/7, not on your laptop | Coolify / Docker on a $5–$20 VPS |

> Not a Zapier workflow. Not a one-shot script. A loop that reads data, makes decisions, publishes, observes results, and adjusts.

---

## Infrastructure Stack — Fully Open Source

### Data Pipeline & Warehouse

| Tool | Role | License | Alternative To | Why Open Source |
|------|------|---------|----------------|-----------------|
| **Airbyte** | Data pipeline (pre-built connectors) | MIT / ELv2 | Fivetran, Stitch | Self-hosted, no per-row cost, 300+ connectors |
| **ClickHouse** | Columnar data warehouse | Apache 2.0 | Snowflake, BigQuery | 100-1000x faster than row-based for analytics, runs on $5 VPS |

**Data sources to unify:**

```
Facebook Ads API ──┐
Google Analytics ──┤
PostHog ───────────┤──► Airbyte ──► ClickHouse ──► Agent reads via SQL
Stripe ────────────┤
HubSpot/CRM ───────┘
```

**Deployment (Docker Compose):**

```yaml
# docker-compose.yml — Airbyte + ClickHouse
version: "3.8"
services:
  airbyte:
    image: airbyte/airbyte
    ports: ["8000:8000"]
    volumes: ["./airbyte_data:/data"]
  clickhouse:
    image: clickhouse/clickhouse-server
    ports: ["8123:8123"]
    volumes: ["./clickhouse_data:/var/lib/clickhouse"]
```

The agent queries ClickHouse via SQL to answer questions like: *"Which specific ad creative drove the most revenue last week?"* — joining Facebook Ads spend, Google Analytics conversions, and Stripe payment data.

### Agent Hosting

**Replace Railway/Heroku with:** Coolify (open-source PaaS) or plain Docker on a VPS.

| Option | Cost | Effort | Best For |
|--------|------|--------|----------|
| **Coolify** | Free (self-hosted) | Medium | Multiple agents, UI management |
| **Docker Compose** | Free | Low | Single agent, simple setup |
| **DigitalOcean App Platform** | $5–$12/mo | Low | If you want managed but not locked in |
| **Hetzner VPS** | €4–€8/mo | Medium | Best value bare metal |

**Coolify deploy:** 1-click from GitHub repo. Your agent is just a Docker container that runs the Python loop.

### Creative Generation — Replacing Proprietary Tools

#### Replace Kai AI / Nano Banana → ComfyUI + Stable Diffusion / FLUX

| Proprietary Tool | Open-Source Replacement | Setup |
|-----------------|------------------------|-------|
| **Kai AI** (image gen) | **ComfyUI** + Stable Diffusion XL / FLUX | `comfy-cli install --nvidia` (or `--m-series` for Mac) |
| **Google Nano Banana** (statics) | **ComfyUI** + SDXL + ControlNet | Same ComfyUI install, different workflow |
| **HeyGen** (AI avatar video) | **Wav2Lip** + **Coqui TTS** | `docker pull ghcr.io/wav2lip` + `pip install TTS` |
| **Seedance** (video gen) | **Stable Video Diffusion** / **AnimateDiff** | Via ComfyUI AnimateDiff nodes |

**ComfyUI setup (one-time):**

```bash
# Install comfy-cli
pipx install comfy-cli

# Install ComfyUI (takes ~2 min)
comfy --skip-prompt install --nvidia  # or --m-series for Mac

# Download models
comfy model download \
  --url "https://huggingface.co/stabilityai/stable-diffusion-xl-base-1.0/resolve/main/sd_xl_base_1.0.safetensors" \
  --relative-path models/checkpoints

# Launch
comfy launch --background

# Verify
curl http://127.0.0.1:8188/system_stats
```

**Bulk creative generation script:**

```python
import requests
import json
import os

COMFY_HOST = "http://127.0.0.1:8188"
WORKFLOW_FILE = "workflows/sdxl_ad_creative.json"
OUTPUT_DIR = "generated_ads"

def generate_ad_creative(pain_point: str, brand_guidelines: dict,
                         variations: int = 5) -> list[str]:
    """Generate ad creatives for a specific pain point."""
    with open(WORKFLOW_FILE) as f:
        workflow = json.load(f)

    # Inject prompt
    prompt = (
        f"Professional ad creative for: {pain_point}. "
        f"Brand colors: {brand_guidelines.get('colors', 'modern, clean')}. "
        f"Style: {brand_guidelines.get('style', 'professional, minimal')}. "
        f"Text overlay area kept clear."
    )

    workflow["6"]["inputs"]["text"] = prompt  # CLIP text encode node
    workflow["3"]["inputs"]["seed"] = hash(pain_point + str(variations)) % (2**32)

    # Submit to ComfyUI
    resp = requests.post(f"{COMFY_HOST}/api/prompt", json={"prompt": workflow})
    prompt_id = resp.json()["prompt_id"]

    # Poll for completion
    while True:
        history = requests.get(f"{COMFY_HOST}/history/{prompt_id}").json()
        if prompt_id in history:
            outputs = history[prompt_id]["outputs"]
            break
        time.sleep(1)

    # Return saved image paths
    images = []
    for node_id, node_output in outputs.items():
        for img in node_output.get("images", []):
            images.append(os.path.join(OUTPUT_DIR, img["filename"]))
    return images
```

#### Replace Perplexity → SearXNG + Local LLM

**SearXNG** is a self-hosted, privacy-respecting metasearch engine. Combined with a local LLM (via Ollama), it replaces Perplexity for research.

```bash
# Deploy SearXNG
docker run -d --name searxng -p 4000:8080 \
  -v ./searxng-data:/etc/searxng \
  searxng/searxng

# Install Ollama for local LLM
curl -fsSL https://ollama.com/install.sh | sh
ollama pull llama3.2  # or mistral, or your model of choice
```

**Research pipeline (open-source Perplexity replacement):**

```python
import requests
from ollama import Client

def research_pain_points(target_audience: str, niche: str) -> list[dict]:
    """
    Research customer pain points using self-hosted search + local LLM.
    No API keys, no rate limits, no cost.
    """
    # 1. Search Reddit via SearXNG
    searxng_url = "http://localhost:4000/search"
    queries = [
        f"site:reddit.com/r/{niche} frustrated with",
        f"site:reddit.com/r/{niche} wish there was",
        f"site:reddit.com/r/{niche} problem with",
        f"site:reddit.com/r/{niche} how to fix",
    ]
    all_results = []
    for q in queries:
        resp = requests.get(searxng_url, params={"q": q, "format": "json"})
        all_results.extend(resp.json().get("results", []))

    # 2. Extract pain points via local LLM
    ollama = Client(host="http://localhost:11434")
    text = "\n".join([r.get("content", "") for r in all_results[:50]])

    response = ollama.chat(model="llama3.2", messages=[{
        "role": "user",
        "content": f"""Extract the top 10 customer pain points and desired outcomes from these Reddit posts about {target_audience}.
Return as JSON array: [{{"pain_point": "...", "frequency": N, "quote": "..."}}]

Posts:
{text}"""
    }])

    return json.loads(response["message"]["content"])
```

#### Replace HeyGen → Wav2Lip + Coqui TTS

**Wav2Lip** syncs lip movements to audio. **Coqui TTS** generates natural speech from text. Together they create AI avatar videos:

```bash
# Coqui TTS (text-to-speech)
pip install TTS
tts --text "Your ad copy here" --model_name tts_models/en/ljspeech/tacotron2-DDC \
    --out_path output.wav

# Wav2Lip (lip sync — via Docker)
docker run --gpus all -v $(pwd)/input:/input -v $(pwd)/output:/output \
  ghcr.io/wan-h/wav2lip:latest \
  --face /input/avatar.mp4 \
  --audio /output/audio.wav \
  --outfile /output/ad_video.mp4
```

For higher quality, train a Coqui voice clone on a 30-second sample of your brand's voice actor:

```bash
# Voice cloning (one-time)
tts --model_name tts_models/en/ljspeech/tacotron2-DDC_ss \
    --speaker_wav brand_voice_sample.wav \
    --text "Welcome to our brand" \
    --out_path clone_test.wav
```

### Facebook Marketing API — Write-Only Safety

The **Facebook Marketing API** is the only external dependency you cannot replace — it's the channel itself. Use it safely:

**DO:**
- Create ad creatives, ad sets, campaigns
- Turn off underperforming ads
- Promote winning ads
- Pull performance metrics via the data warehouse (not the API)

**DO NOT:**
- Bulk-pull millions of rows of ad data via the API (gets accounts banned)
- Spam the API with rapid requests (>10 req/s gets rate-limited)
- Store API tokens in code (use environment variables)

**Safety wrapper:**

```python
class FacebookAdsClient:
    """Rate-limited, write-only Facebook Marketing API client."""

    def __init__(self, access_token: str, ad_account_id: str):
        self.base = f"https://graph.facebook.com/v22.0/act_{ad_account_id}"
        self.token = access_token
        self._rate_limit = 0.5  # seconds between calls

    def _call(self, endpoint: str, method: str = "POST", data: dict = None):
        time.sleep(self._rate_limit)
        url = f"{self.base}/{endpoint}"
        params = {"access_token": self.token}
        if method == "POST":
            resp = requests.post(url, params=params, json=data or {})
        else:
            resp = requests.get(url, params={**params, **(data or {})})
        resp.raise_for_status()
        return resp.json()

    def create_ad(self, creative_id: str, ad_set_id: str, name: str):
        """Publish one ad. Never bulk-pull data through this route."""
        return self._call("ads", data={
            "name": name,
            "adset_id": ad_set_id,
            "creative": {"creative_id": creative_id},
            "status": "PAUSED",  # Start paused for human review
        })

    def turn_off(self, ad_id: str):
        """Turn off an underperforming ad."""
        return self._call(ad_id, data={"status": "PAUSED"})

    def promote(self, ad_id: str):
        """Promote a winning ad."""
        return self._call(ad_id, data={"status": "ACTIVE"})

    def get_performance_summary(self, campaign_id: str) -> dict:
        """
        Get minimal performance data for decision-making only.
        Full analytics come from ClickHouse, not this API.
        """
        return self._call(f"{campaign_id}/insights", method="GET", data={
            "fields": "spend,impressions,clicks,ctr,cpc,cpm,cpa,actions",
            "level": "ad",
            "date_preset": "last_7d",
        })
```

---

## The Complete Agent Workflow

### Phase 1: Data Foundation (Week 1)

```
Day 1-2: Deploy infrastructure
  ├── Airbyte (docker-compose up)
  ├── ClickHouse (docker-compose up)
  ├── ComfyUI (comfy launch --background)
  ├── SearXNG (docker run)
  └── Ollama (curl -fsSL https://ollama.com/install.sh | sh)

Day 3-4: Connect data sources
  ├── Facebook Ads → Airbyte connector
  ├── Google Analytics → Airbyte connector
  ├── Stripe → Airbyte connector
  └── Verify all data flowing into ClickHouse

Day 5-7: Build agent code
  ├── Python agent with thinking loop
  ├── SQL queries for performance analysis
  ├── Creative generation pipeline
  └── Facebook API integration (write-only)
```

### Phase 2: Research & Generate (Weekly Cycle)

#### Step 1: Research Pain Points (Monday)

```python
def weekly_research_cycle():
    """Monday morning: research fresh angles for ad creative."""
    pain_points = research_pain_points(
        target_audience="WordPress site owners",
        niche="WordPress"
    )

    # Rank by frequency
    pain_points.sort(key=lambda x: x["frequency"], reverse=True)
    top_3 = pain_points[:3]

    # Save to ClickHouse for reference
    clickhouse.execute(
        "INSERT INTO pain_points (pain_point, frequency, date) VALUES",
        [(p["pain_point"], p["frequency"], date.today()) for p in top_3]
    )
    return top_3
```

**Prompt template for the LLM-powered pain point extraction:**

```
You are a marketing researcher analyzing Reddit conversations about {TARGET_AUDIENCE}.

Extract the top 10 specific pain points people are expressing. For each one:
1. The exact pain point (e.g., "Spending $1000/mo on agency for simple WordPress changes")
2. How many times it was mentioned (frequency count)
3. A direct quote from a real person expressing this frustration
4. The desired outcome (e.g., "Want to make changes myself without needing a developer")

Focus on pain points that a {PRODUCT_NAME} could solve. Ignore generic complaints.
Be specific — vague pain points make bad ad copy.
```

#### Step 2: Generate Ad Creative (Tuesday–Wednesday)

```python
def weekly_creative_cycle(pain_points: list[dict], brand_guidelines: dict):
    """Generate 10 ads per pain point using self-hosted ComfyUI."""
    all_ads = []

    for pain_point in pain_points[:3]:
        # Generate static images
        images = generate_ad_creative(
            pain_point["pain_point"],
            brand_guidelines,
            variations=5
        )

        # Generate avatar video
        script = generate_ad_script(pain_point, brand_guidelines["tone"])
        video = generate_avatar_video(
            script=script,
            avatar_path="assets/brand_avatar.mp4",
            voice_sample="assets/brand_voice.wav"
        )

        all_ads.append({
            "pain_point": pain_point["pain_point"],
            "statics": images,
            "video": video,
            "headline": generate_headline(pain_point),
            "primary_text": script,
        })

    return all_ads
```

**Ad script generation prompt:**

```
Write a 30-second direct-response Facebook ad script for {PRODUCT_NAME}.

Target customer: {TARGET_AUDIENCE}
Pain point: {PAIN_POINT}
Desired outcome: {DESIRED_OUTCOME}
Brand tone: {BRAND_TONE}

Structure:
- Hook (first 3 seconds — grab attention with the pain point)
- Problem elaboration (seconds 3-10 — make them feel understood)
- Solution introduction (seconds 10-18 — present the product)
- Social proof / results (seconds 18-25)
- Call to action (seconds 25-30)

Write in natural, conversational language. No corporate speak. Use "you" not "we".
```

#### Step 3: Publish & Optimize (Thursday–Sunday)

```python
def weekly_publish_cycle(ads: list[dict], fb_client: FacebookAdsClient):
    """Publish ads, monitor for 48 hours, optimize."""
    ad_ids = []

    # Publish all ads (start paused for safety review)
    for ad in ads:
        # Create creative
        creative = fb_client._call("adcreatives", data={
            "name": f"creative_{uuid.uuid4().hex[:8]}",
            "object_story_spec": {
                "page_id": PAGE_ID,
                "link_data": {
                    "link": LANDING_PAGE_URL,
                    "message": ad["primary_text"],
                    "name": ad["headline"],
                    "call_to_action": {"type": "LEARN_MORE"},
                }
            }
        })
        ad_ids.append(fb_client.create_ad(creative["id"], AD_SET_ID, ad["headline"]))

    # Wait 48 hours for signal
    time.sleep(48 * 3600)

    # Get performance data from ClickHouse (not FB API)
    results = clickhouse.execute("""
        SELECT ad_id, spend, cpa, ctr, conversions
        FROM facebook_ads_performance
        WHERE date >= now() - INTERVAL 2 DAY
        ORDER BY cpa ASC
    """)

    # Turn off bottom 30%
    threshold = int(len(results) * 0.7)
    winners = results[:threshold]
    losers = results[threshold:]

    for ad in losers:
        fb_client.turn_off(ad["ad_id"])
        log(f"Turned off underperformer: {ad['ad_id']} (CPA: ${ad['cpa']})")

    # Promote winners
    for ad in winners[:3]:  # Top 3 get extra budget
        fb_client.promote(ad["ad_id"])
        log(f"Promoted winner: {ad['ad_id']} (CPA: ${ad['cpa']})")

    # Store winning creatives for feedback loop
    store_winning_creative_patterns(winners)
```

---

## Solving the Entropy Problem

Marketing agents naturally converge on the same creative patterns. Counteract this with:

### Self-Hosted Competitor Research

```python
def entropy_injection():
    """Inject fresh creative DNA from competitors and trending content."""

    # 1. Competitor ad library (Meta's public API — free, no token needed)
    fb_lib_url = "https://graph.facebook.com/v22.0/ads_archive"
    resp = requests.get(fb_lib_url, params={
        "search_terms": "'WordPress' OR 'website builder'",
        "ad_type": "ALL",
        "ad_active_status": "ALL",
        "limit": 50,
    })

    # 2. Trending content via SearXNG (self-hosted search)
    trends = requests.get("http://localhost:4000/search", params={
        "q": f"trending marketing {niche} 2026",
        "categories": "news",
        "format": "json",
        "language": "en",
        "time_range": "month",
    })

    # 3. YouTube transcript mining (via youtube-transcript-api)
    from youtube_transcript_api import YouTubeTranscriptApi
    yt_ids = ["CHANNEL_VIDEO_1", "CHANNEL_VIDEO_2"]  # Niche YouTube channels
    for vid in yt_ids:
        transcript = YouTubeTranscriptApi.fetch(vid)
        text = " ".join(s.text for s in transcript.snippets)
        insights = local_llm.analyze_trends(text)
        store_insights(insights)

    return merge_creatives(competitor_ads, trends, insights)
```

---

## Budget Controls & Safety

### Spend Limits

```python
# Hard-coded safety limits in the agent
BUDGET = {
    "daily_cap": 50.00,          # Never spend more than $50/day
    "max_cpa": 15.00,            # Turn off ads exceeding $15 CPA
    "max_ads_per_batch": 10,     # Never create more than 10 ads at once
    "cooldown_hours": 48,        # Minimum learning window before optimization
    "human_review": True,        # Start ads in PAUSED for human approval
}
```

### Human-in-the-Loop Gates

| Gate | What Happens | Trigger |
|------|-------------|---------|
| **Creative review** | Ads created in PAUSED status | Every Monday |
| **Budget escalation** | Pause all spend, notify human | Daily spend > $50 |
| **CPA threshold** | Kill ad, notify human | CPA > $15 |
| **New audience** | Flag for manual approval | First time targeting a new segment |
| **Platform change** | Full pause | Facebook API version bump or policy change |

### Alerting (Self-Hosted)

```python
# Simple email/SMS alert via self-hosted ntfy or Gotify
import requests

def alert_human(message: str, level: str = "warning"):
    """Send alert to the operator via self-hosted ntfy."""
    requests.post(
        "http://localhost:8080/agent-alerts",
        json={"topic": "marketing-agent", "message": message, "priority": level}
    )
```

---

## Data Schema

### ClickHouse Tables

```sql
-- Ad performance (populated by Airbyte from Facebook Ads)
CREATE TABLE facebook_ads_performance (
    date Date,
    ad_id String,
    campaign_id String,
    ad_set_id String,
    impressions UInt64,
    clicks UInt64,
    spend Float64,
    ctr Float64,
    cpc Float64,
    cpm Float64,
    cpa Float64,
    conversions UInt64,
    creative_id String
) ENGINE = MergeTree()
ORDER BY (date, ad_id);

-- Pain point research log
CREATE TABLE pain_points (
    date Date,
    pain_point String,
    frequency UInt32,
    source String,
    quote String
) ENGINE = MergeTree()
ORDER BY (date, frequency);

-- Creative performance (feedback loop data)
CREATE TABLE creative_patterns (
    date Date,
    creative_hash String,
    prompt_used String,
    visual_style String,
    color_palette String,
    cpa Float64,
    ctr Float64,
    is_winner Boolean
) ENGINE = MergeTree()
ORDER BY (date, cpa);

-- Agent decisions (audit trail)
CREATE TABLE agent_audit_log (
    timestamp DateTime,
    action String,
    ad_id String,
    reason String,
    metadata String  -- JSON blob
) ENGINE = MergeTree()
ORDER BY timestamp;
```

---

## Agent Code Structure

```
marketing-agent/
├── agent.py                  # Main loop — orchestrates weekly cycle
├── config.py                 # Budget limits, brand guidelines, FB credentials
├── research/
│   ├── pain_points.py        # SearXNG + Ollama research pipeline
│   └── competitor_analysis.py
├── creative/
│   ├── static.py             # ComfyUI integration
│   ├── video.py              # Wav2Lip + Coqui TTS pipeline
│   └── prompt_templates/     # Ad script, headline, CTA templates
├── publish/
│   ├── facebook_client.py    # Rate-limited, write-only FB API client
│   └── ad_campaign.py        # Campaign structure management
├── optimize/
│   ├── analyzer.py           # Read ClickHouse, determine winners/losers
│   ├── entropy.py            # Fresh creative DNA injection
│   └── budget_manager.py     # Spend caps, alerts
├── data/
│   ├── airbyte_docker.yml    # Airbyte deployment
│   ├── clickhouse_schema.sql # Table definitions
│   └── queries/              # SQL queries for analytics
├── infrastructure/
│   ├── docker-compose.yml    # All self-hosted services
│   └── coolify.json          # Coolify deployment config
└── deploy.sh                 # One-command deploy
```

### Main Agent Loop

```python
#!/usr/bin/env python3
"""Marketing Agent — autonomous weekly cycle."""

import time
from research.pain_points import research_pain_points
from creative.static import generate_ad_creative, generate_ad_script
from creative.video import generate_avatar_video
from publish.facebook_client import FacebookAdsClient
from optimize.analyzer import analyze_performance
from optimize.entropy import entropy_injection
from optimize.budget_manager import BudgetManager

def weekly_cycle():
    """One full marketing cycle: research → create → publish → optimize."""
    config = load_config()
    fb = FacebookAdsClient(config["fb_token"], config["ad_account_id"])
    budget = BudgetManager(config["budget"])

    # Step 1: Research
    pain_points = research_pain_points(
        config["target_audience"],
        config["niche"]
    )
    log(f"Found {len(pain_points)} pain points")

    # Step 2: Generate creative
    ads = []
    for pp in pain_points[:3]:
        images = generate_ad_creative(pp, config["brand_guidelines"])
        video = generate_avatar_video(
            script=generate_ad_script(pp, config["brand_tone"]),
            avatar_path=config["avatar_path"],
            voice_sample=config["voice_sample"]
        )
        ads.append({"pain_point": pp, "images": images, "video": video})
    log(f"Generated {len(ads)} ad variations")

    # Step 3: Publish (paused for review)
    if config.get("human_review", True):
        fb.publish_paused(ads)
        alert_human(f"{len(ads)} ads ready for review", "info")
        return  # Wait for human to activate

    # Step 4: Wait & optimize (2-3 day learning window)
    time.sleep(48 * 3600)
    performance = analyze_performance(config["clickhouse_host"])
    budget.optimize(performance, fb)

    # Step 5: Entropy prevention
    entropy_injection(config["niche"])

    log("Cycle complete. Schedule next run in 7 days.")

if __name__ == "__main__":
    while True:
        weekly_cycle()
        time.sleep(7 * 24 * 3600)  # Weekly cadence
```

---

## Deployment

### One-Command Deploy

```bash
# 1. Clone the agent repository
git clone https://github.com/your-org/marketing-agent && cd marketing-agent

# 2. Deploy infrastructure
docker compose -f infrastructure/docker-compose.yml up -d

# 3. Configure
cp .env.example .env
# Edit .env with your Facebook credentials and brand settings

# 4. Run
python3 agent.py
```

### Docker Compose (Full Stack)

```yaml
version: "3.8"
services:
  airbyte:
    image: airbyte/airbyte:latest
    ports: ["8000:8000"]
    volumes: ["./data/airbyte:/data"]

  clickhouse:
    image: clickhouse/clickhouse-server:latest
    ports: ["8123:8123"]
    volumes: ["./data/clickhouse:/var/lib/clickhouse"]

  comfyui:
    build:
      context: .
      dockerfile: infrastructure/Dockerfile.comfy
    ports: ["8188:8188"]
    volumes: ["./models:/comfy/models"]
    deploy:
      resources:
        reservations:
          devices:
            - driver: nvidia
              count: 1
              capabilities: [gpu]

  searxng:
    image: searxng/searxng:latest
    ports: ["4000:8080"]
    volumes: ["./data/searxng:/etc/searxng"]

  ollama:
    image: ollama/ollama:latest
    ports: ["11434:11434"]
    volumes: ["./data/ollama:/root/.ollama"]

  agent:
    build: .
    env_file: .env
    depends_on: [clickhouse, comfyui, searxng, ollama]
```

---

## Cost Comparison

| Component | Proprietary Path | Monthly Cost | Self-Hosted Path | Monthly Cost |
|-----------|-----------------|-------------|-----------------|-------------|
| Data pipeline | Fivetran | $500+ | Airbyte | $0 |
| Data warehouse | Snowflake | $200+ | ClickHouse | $0 (on existing VPS) |
| Image generation | Midjourney/Kai | $60+ | ComfyUI + SDXL | $0 (GPU already owned) |
| Video avatars | HeyGen | $120+ | Wav2Lip + Coqui | $0 |
| Research | Perplexity Pro | $20 | SearXNG + Ollama | $0 |
| Hosting | Railway/Heroku | $20+ | Coolify / Docker VPS | $5–$20 |
| **Total** | | **$920+/mo** | | **$5–$20/mo** |

---

## Key Principles

1. **Marketing is continuous, not campaign-based** — the agent runs weekly cycles, not one-off pushes
2. **Test 10-15-20 variations** of the same ad with different positioning before giving up
3. **Let the market tell you what works** — don't impose ideas, test them via the agent loop
4. **Start with a human in the loop** (ads start PAUSED), graduate to full autonomy as trust builds
5. **The agent is a virtual employee** — focused on one channel with all data it needs
6. **Self-host everything you can** — the only unavoidable external dependency is the ad channel itself

---

## Quick Start

```bash
# 30-minute deploy
git clone https://github.com/your-org/marketing-agent
cd marketing-agent
docker compose up -d                              # 5 min
cp .env.example .env && vim .env                   # 2 min (add FB token, brand info)
python3 -c "from infrastructure.setup import verify; verify()"  # 3 min
docker compose exec comfyui bash -c "comfy model download --url https://huggingface.co/stabilityai/stable-diffusion-xl-base-1.0/resolve/main/sd_xl_base_1.0.safetensors --relative-path models/checkpoints"  # 10 min
python3 agent.py                                  # Run first cycle
```

## References
- **Source video:** https://youtu.be/U2hogriGmEw — Cody Schneider × Greg Isenberg
- **Cody Schneider** — CompaniesGraph (companiesgraph.com)
- **Airbyte:** https://airbyte.com (open-source data pipeline)
- **ClickHouse:** https://clickhouse.com (open-source columnar database)
- **ComfyUI:** https://github.com/comfyanonymous/ComfyUI (open-source node-based image gen)
- **Coolify:** https://coolify.io (open-source PaaS, self-hosted)
- **SearXNG:** https://docs.searxng.org (self-hosted metasearch engine)
- **Ollama:** https://ollama.com (local LLM runner)
- **Wav2Lip:** https://github.com/Rudrabha/Wav2Lip (lip-sync video gen)
- **Coqui TTS:** https://github.com/coqui-ai/TTS (open-source text-to-speech)
- **AnimateDiff:** https://github.com/guoyww/AnimateDiff (video generation)
- **Facebook Marketing API:** https://developers.facebook.com/docs/marketing-apis
