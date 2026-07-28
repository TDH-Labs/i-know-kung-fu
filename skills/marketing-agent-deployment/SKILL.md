---
description: >-
  Step-by-step deployment walkthrough for the self-hosted marketing agent stack.
  From zero to a running agent that researches, creates, publishes, and optimizes
  Facebook ad campaigns — all on open-source infrastructure.
name: marketing-agent-deployment
tags:
- deployment
- self-hosted
- infrastructure
- devops
- Docker
- setup
- walkthrough
---

# Marketing Agent Deployment Guide

> From zero to a running marketing agent in ~2 hours. This is the **how** — concrete commands, config files, and wiring steps. Assumes the architecture from the `marketing-agents-are-too-good-now` skill.

## Prerequisites

| Requirement | Minimum | Recommended |
|------------|---------|-------------|
| VPS / Server | 4 GB RAM, 2 CPU, 50 GB disk | 16 GB RAM, 4 CPU, GPU |
| Docker + Compose | Docker 24+ | Docker 27+ |
| Facebook Ads account | Active with payment method | Established account (not new) |
| Domain (optional) | For Coolify/SearXNG | Any cheap domain |
| GPU (optional) | For ComfyUI image gen | NVIDIA with 8+ GB VRAM |

---

## Phase 1: Server Setup (30 min)

### 1A — Provision a VPS

```bash
# Option A: Hetzner (best value, ~€8/mo)
# Sign up at hetzner.com, create a CX22 or CAX22 instance
# Deploy Ubuntu 24.04

# Option B: DigitalOcean ($12/mo)
# Create a droplet with Docker pre-installed

# SSH in
ssh root@YOUR_SERVER_IP
```

### 1B — Install Docker

```bash
# Docker Engine (if not pre-installed)
curl -fsSL https://get.docker.com | sh

# Docker Compose plugin
sudo apt-get update && sudo apt-get install -y docker-compose-plugin

# Verify
docker --version && docker compose version

# Add your user
sudo usermod -aG docker $USER
newgrp docker
```

---

## Phase 2: Data Infrastructure (20 min)

### 2A — Deploy Airbyte + ClickHouse

```bash
mkdir -p ~/marketing-agent/data && cd ~/marketing-agent
```

Create `docker-compose.yml`:

```yaml
version: "3.8"
services:
  airbyte:
    image: airbyte/airbyte:latest
    ports: ["8000:8000"]
    volumes:
      - ./data/airbyte:/data
    restart: unless-stopped

  clickhouse:
    image: clickhouse/clickhouse-server:latest
    ports: ["8123:8123"]
    volumes:
      - ./data/clickhouse:/var/lib/clickhouse
    restart: unless-stopped
    ulimits:
      nofile:
        soft: 262144
        hard: 262144
```

```bash
docker compose up -d
```

### 2B — Create the Database Schema

```bash
# Connect to ClickHouse
docker compose exec -T clickhouse clickhouse-client << 'SQL'
CREATE DATABASE IF NOT EXISTS marketing_agent;

CREATE TABLE IF NOT EXISTS marketing_agent.facebook_ads_performance (
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

CREATE TABLE IF NOT EXISTS marketing_agent.pain_points (
    date Date,
    pain_point String,
    frequency UInt32,
    source String,
    quote String
) ENGINE = MergeTree()
ORDER BY (date, frequency);

CREATE TABLE IF NOT EXISTS marketing_agent.creative_patterns (
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

CREATE TABLE IF NOT EXISTS marketing_agent.agent_audit_log (
    timestamp DateTime,
    action String,
    ad_id String,
    reason String,
    metadata String
) ENGINE = MergeTree()
ORDER BY timestamp;
SQL
```

### 2C — Connect Data Sources via Airbyte

1. Open `http://YOUR_SERVER_IP:8000` in a browser
2. Set up each source connector:

| Source | Connector Name | What You Need |
|--------|---------------|--------------|
| Facebook Ads | `Facebook Marketing` | FB Access Token, Ad Account ID |
| Google Analytics 4 | `Google Analytics 4` | GA4 Property ID, Service Account JSON |
| Stripe | `Stripe` | Stripe Secret Key (restricted, read-only) |
| HubSpot | `HubSpot` | HubSpot Private App Token |

3. Set the destination to ClickHouse:
   - Host: `clickhouse` (Docker network name)
   - Port: `8123`
   - Database: `marketing_agent`
   - User: `default` (no password by default)

4. Set sync frequency to every 6 hours (manual trigger for initial sync)

---

## Phase 3: Creative Infrastructure (30 min)

### 3A — Deploy SearXNG + Ollama

Add to `docker-compose.yml`:

```yaml
  searxng:
    image: searxng/searxng:latest
    ports: ["4000:8080"]
    volumes:
      - ./data/searxng:/etc/searxng
    environment:
      - SEARXNG_BASE_URL=http://localhost:4000/
    restart: unless-stopped
```

```bash
docker compose up -d searxng

# Install Ollama (runs on host for GPU access)
curl -fsSL https://ollama.com/install.sh | sh
ollama pull llama3.2
ollama pull mxbai-embed-large  # For embeddings
```

### 3B — Deploy ComfyUI (with GPU)

If you have a GPU, add to `docker-compose.yml`:

```yaml
  comfyui:
    image: comfyui/comfyui:latest
    ports: ["8188:8188"]
    volumes:
      - ./models:/comfyui/models
      - ./output:/comfyui/output
      - ./custom_nodes:/comfyui/custom_nodes
    deploy:
      resources:
        reservations:
          devices:
            - driver: nvidia
              count: 1
              capabilities: [gpu]
    restart: unless-stopped
```

If no GPU, install on a machine that has one and expose the API endpoint.

Download models:

```bash
docker compose exec comfyui python3 -c "
from comfy_cli import model_download
model_download('https://huggingface.co/stabilityai/stable-diffusion-xl-base-1.0/resolve/main/sd_xl_base_1.0.safetensors')
"
```

### 3C — Test the Creative Pipeline

```bash
# Test SearXNG
curl 'http://localhost:4000/search?q=test&format=json' | head

# Test Ollama
curl http://localhost:11434/api/generate -d '{
  "model": "llama3.2",
  "prompt": "Say hello",
  "stream": false
}'

# Test ComfyUI
curl http://localhost:8188/system_stats
```

---

## Phase 4: Deploy the Agent (30 min)

### 4A — Create the Agent Project

```bash
mkdir -p ~/marketing-agent/agent && cd ~/marketing-agent/agent
```

Create the project structure:

```
agent/
├── agent.py              # Main loop
├── config.py              # Configuration
├── requirements.txt       # Python deps
├── Dockerfile             # Container definition
├── research/
│   ├── __init__.py
│   ├── pain_points.py     # SearXNG + Ollama research
│   └── competitor_analysis.py
├── creative/
│   ├── __init__.py
│   ├── static.py          # ComfyUI integration
│   └── video.py           # Wav2Lip + Coqui pipeline
├── publish/
│   ├── __init__.py
│   └── facebook_client.py # FB Ads API client
├── optimize/
│   ├── __init__.py
│   ├── analyzer.py        # ClickHouse queries
│   └── entropy.py         # Fresh ideas injection
└── data/
    └── queries/           # SQL query library
```

### 4B — Create the Agent Entry Point

```python
#!/usr/bin/env python3
"""agent.py — Marketing Agent Main Loop"""

import os, sys, json, time, logging
from datetime import datetime

# Config from environment
CONFIG = {
    "fb_token": os.environ["FB_ACCESS_TOKEN"],
    "ad_account_id": os.environ["FB_AD_ACCOUNT_ID"],
    "fb_page_id": os.environ["FB_PAGE_ID"],
    "target_audience": os.environ.get("TARGET_AUDIENCE", ""),
    "niche": os.environ.get("NICHE", ""),
    "brand_tone": os.environ.get("BRAND_TONE", "professional"),
    "landing_page_url": os.environ.get("LANDING_PAGE_URL", ""),
    "daily_budget_cap": float(os.environ.get("DAILY_BUDGET_CAP", "50")),
    "max_cpa": float(os.environ.get("MAX_CPA", "15")),
    "max_ads_per_batch": int(os.environ.get("MAX_ADS_PER_BATCH", "10")),
    "clickhouse_host": os.environ.get("CLICKHOUSE_HOST", "localhost"),
    "searxng_host": os.environ.get("SEARXNG_HOST", "http://localhost:4000"),
    "ollama_host": os.environ.get("OLLAMA_HOST", "http://localhost:11434"),
    "comfyui_host": os.environ.get("COMFYUI_HOST", "http://localhost:8188"),
    "human_review": os.environ.get("HUMAN_REVIEW", "true").lower() == "true",
}

logging.basicConfig(level=logging.INFO, format="%(asctime)s [%(levelname)s] %(message)s")
log = logging.getLogger("marketing-agent")


def weekly_cycle():
    """One full marketing cycle."""
    log.info("=== Starting weekly marketing cycle ===")

    from research.pain_points import research_pain_points
    from creative.static import generate_ad_creative
    from creative.video import generate_ad_script
    from publish.facebook_client import FacebookAdsClient

    fb = FacebookAdsClient(CONFIG)

    # Step 1: Research
    pain_points = research_pain_points(CONFIG)
    log.info(f"Found {len(pain_points)} pain points: {[p['pain_point'][:40] for p in pain_points[:3]]}")

    # Step 2: Generate creative
    ads = []
    for pp in pain_points[:3]:
        images = generate_ad_creative(pp, CONFIG)
        log.info(f"Generated {len(images)} images for: {pp['pain_point'][:40]}")
        ads.append({"pain_point": pp, "images": images})

    # Step 3: Publish (paused for review)
    if CONFIG["human_review"]:
        fb.publish_paused(ads)
        log.warning(f"Published {len(ads)} ads in PAUSED — human review needed")
        return

    # Step 4: Wait & optimize
    log.info("Waiting 48h for learning window...")
    time.sleep(48 * 3600)

    from optimize.analyzer import analyze_performance
    performance = analyze_performance(CONFIG)
    fb.optimize(performance, CONFIG)
    log.info(f"Optimization complete. Winners: {performance['winners']}")

    # Step 5: Entropy
    from optimize.entropy import entropy_injection
    entropy_injection(CONFIG)
    log.info("Entropy injection complete")

    log.info("=== Weekly cycle complete ===")


if __name__ == "__main__":
    log.info("Marketing Agent starting...")
    while True:
        try:
            weekly_cycle()
        except Exception as e:
            log.error(f"Cycle failed: {e}", exc_info=True)
            # Alert and retry in 1 hour
            try:
                import requests
                requests.post("http://localhost:8080/agent-alerts",
                    json={"topic": "marketing-agent-error", "message": str(e)})
            except:
                pass
            time.sleep(3600)
        log.info("Sleeping 7 days until next cycle...")
        time.sleep(7 * 24 * 3600)
```

### 4C — Create config.py

```python
"""config.py — Environment-based configuration loader."""

import os
from dataclasses import dataclass, field
from typing import Optional

@dataclass
class AgentConfig:
    # Facebook
    fb_token: str = field(default_factory=lambda: os.environ["FB_ACCESS_TOKEN"])
    ad_account_id: str = field(default_factory=lambda: os.environ["FB_AD_ACCOUNT_ID"])
    fb_page_id: str = field(default_factory=lambda: os.environ["FB_PAGE_ID"])

    # Targeting
    target_audience: str = os.environ.get("TARGET_AUDIENCE", "")
    niche: str = os.environ.get("NICHE", "")
    brand_tone: str = os.environ.get("BRAND_TONE", "professional")
    brand_guidelines: dict = field(default_factory=lambda: {
        "colors": os.environ.get("BRAND_COLORS", "#000000 #FFFFFF"),
        "style": os.environ.get("BRAND_STYLE", "modern minimal"),
        "fonts": os.environ.get("BRAND_FONTS", "Inter, sans-serif"),
    })

    # Budget
    daily_budget_cap: float = float(os.environ.get("DAILY_BUDGET_CAP", "50"))
    max_cpa: float = float(os.environ.get("MAX_CPA", "15"))
    max_ads_per_batch: int = int(os.environ.get("MAX_ADS_PER_BATCH", "10"))

    # Services
    clickhouse_host: str = os.environ.get("CLICKHOUSE_HOST", "localhost")
    searxng_host: str = os.environ.get("SEARXNG_HOST", "http://localhost:4000")
    ollama_host: str = os.environ.get("OLLAMA_HOST", "http://localhost:11434")
    comfyui_host: str = os.environ.get("COMFYUI_HOST", "http://localhost:8188")

    # Safety
    human_review: bool = os.environ.get("HUMAN_REVIEW", "true").lower() == "true"
```

### 4D — Deploy the Agent

```bash
# Create Dockerfile
cat > Dockerfile << 'DOCKER'
FROM python:3.12-slim
WORKDIR /app
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt
COPY . .
CMD ["python3", "agent.py"]
DOCKER

# Requirements
cat > requirements.txt << 'REQ'
requests>=2.31
clickhouse-driver>=0.2
Pillow>=10.0
REQ

# Build and run
docker build -t marketing-agent .
docker run -d --name marketing-agent \
  --env-file ../.env \
  --restart unless-stopped \
  marketing-agent
```

### 4E — Environment File

```bash
# ~/marketing-agent/.env
FB_ACCESS_TOKEN=YOUR_TOKEN_HERE
FB_AD_ACCOUNT_ID=act_XXXXXXXXX
FB_PAGE_ID=XXXXXXXXX
TARGET_AUDIENCE="WordPress site owners"
NICHE="WordPress"
BRAND_TONE="conversational, helpful"
LANDING_PAGE_URL=https://yourproduct.com
DAILY_BUDGET_CAP=50
MAX_CPA=15
MAX_ADS_PER_BATCH=10
HUMAN_REVIEW=true
CLICKHOUSE_HOST=clickhouse
SEARXNG_HOST=http://searxng:8080
OLLAMA_HOST=http://host.docker.internal:11434
COMFYUI_HOST=http://comfyui:8188
```

---

## Phase 5: Verification (10 min)

### Checklist

- [ ] Airbyte UI accessible at `http://YOUR_IP:8000`
- [ ] ClickHouse accepting queries: `docker compose exec clickhouse clickhouse-client -q "SELECT 1"`
- [ ] SearXNG responding: `curl http://localhost:4000/search?q=test`
- [ ] Ollama running: `curl http://localhost:11434/api/tags`
- [ ] ComfyUI running: `curl http://localhost:8188/system_stats`
- [ ] Facebook sandbox test ad created successfully
- [ ] Agent starts without errors: `docker logs marketing-agent`
- [ ] Data flowing from FB Ads into ClickHouse

### Test the Full Pipeline

```bash
# Trigger a dry-run cycle
docker exec marketing-agent python3 -c "
from agent import weekly_cycle
# Override for test
import os; os.environ['HUMAN_REVIEW'] = 'false'
weekly_cycle()
"
```

---

## Maintenance

### Daily Checks
- Check `docker logs marketing-agent --tail 20`
- Verify Airbyte syncs completed (Airbyte UI)

### Weekly Checks
- Review agent decisions in ClickHouse: `SELECT * FROM marketing_agent.agent_audit_log ORDER BY timestamp DESC LIMIT 20`
- Check spend vs budget
- Review winning creative patterns
- Update competitor ad library search terms if performance plateaus

### Monthly
- Pull latest ComfyUI model updates
- Update SearXNG engine config
- Review and update brand guidelines
- Tune CPA targets and budget caps

---

## Troubleshooting

| Symptom | Likely Cause | Fix |
|---------|-------------|-----|
| Agent won't start | Missing env vars | Check `.env` file, ensure all required vars set |
| FB API errors (403) | Token expired | Refresh FB access token |
| FB API errors (429) | Rate limit hit | Check `_rate_limit` in FB client, increase to 1s |
| No data in ClickHouse | Airbyte sync failed | Check Airbyte UI for sync errors |
| ComfyUI timeout | No GPU or OOM | Check GPU memory, reduce batch size |
| Ollama slow | CPU-only inference | Add `--numa` binding or switch to cloud API |
| Ads not spending | PAUSED status | Set `HUMAN_REVIEW=false` after initial verification |
| Bad ad performance | Wrong audience | Tune `TARGET_AUDIENCE` and `NICHE` in config |

---

## References
- **Architecture skill:** `npx skills add TDH-Labs/i-know-kung-fu --skill marketing-agents-are-too-good-now`
- **Source video:** https://youtu.be/U2hogriGmEw
- **Airbyte docs:** https://docs.airbyte.com
- **ClickHouse docs:** https://clickhouse.com/docs
- **ComfyUI docs:** https://docs.comfy.org
- **FB Marketing API:** https://developers.facebook.com/docs/marketing-apis
