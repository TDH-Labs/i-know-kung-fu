---
description: Build and deploy AI marketing agents that autonomously research, create,
  publish, and optimize ad campaigns — entirely self-hosted using open-source infrastructure.
  Replaces Kai AI, Nano Banana, HeyGen, Seedance, Perplexity, and Railway/Heroku with
  free, self-hosted alternatives.
name: marketing-agents-are-too-good-now
tags:
- marketing agents
- Facebook ads
- open-source
- self-hosted
- ComfyUI
- Stable Diffusion
- Airbyte
- ClickHouse
- Coolify
- SearXNG
- Ollama
- Andromeda
- data pipeline
- ad automation
- agentic marketing
---

# marketing-agents-are-too-good-now

> Build and deploy AI marketing agents that autonomously research, create, publish, and optimize ad campaigns — entirely self-hosted using open-source infrastructure. Replaces Kai AI, Nano Banana, HeyGen, Seedance, Perplexity, and Railway/Heroku with free, self-hosted alternatives.

> Build AI marketing agents that research pain points, generate ad creative, publish to Facebook Ads, and optimize in a continuous feedback loop — all on **self-hosted, open-source infrastructure**. No vendor lock-in.

**Based on:** Cody Schneider (CompaniesGraph) × Greg Isenberg — https://youtu.be/U2hogriGmEw

---

## Architecture Overview

```
┌──────────────────────────────────────────────────────────────┐
│              AGENT ORCHESTRATOR                              │
│   (Python loop — hosted on Coolify / Docker VPS)             │
└──────────────────────────────────────────────────────────────┘
         │                      │                      │
         ▼                      ▼                      ▼
┌─────────────────┐  ┌────────────────────┐  ┌──────────────────┐
│   DATA LAYER    │  │   CREATIVE LAYER   │  │  PUBLISH LAYER   │
│  Airbyte ──►    │  │  ComfyUI ──►       │  │  FB Marketing    │
│  ClickHouse     │  │  SDXL / FLUX       │  │  API (write-only)│
│  SearXNG        │  │  Wav2Lip + Coqui   │  │                  │
│  Ollama (LLM)   │  │  AnimateDiff       │  │                  │
└─────────────────┘  └────────────────────┘  └──────────────────┘
```

The only non-switchable dependency is the Facebook Marketing API — the ad channel itself.

---

## What is a Marketing Agent? (Three Components)

1. **Unified data** — all business data in one place (Airbyte → ClickHouse, both open-source)
2. **Autonomous decision loop** — thinking cadence off live data (your Python agent code)
3. **Cloud-hosted code** — runs 24/7 (Coolify or Docker on a $5–$20/mo VPS)

> Not a Zapier workflow. A loop that reads data, decides, publishes, observes, adjusts.

---

## Proprietary Tool Replacements

| Proprietary Tool | Cost | Open-Source Replacement | Setup |
|----------------|------|------------------------|-------|
| Kai AI | $$/mo | ComfyUI + Stable Diffusion XL | `comfy --skip-prompt install` |
| Google Nano Banana | $$/mo | ComfyUI + SDXL + ControlNet | Same ComfyUI install |
| HeyGen | $120/mo | Wav2Lip + Coqui TTS | `docker pull` + `pip install TTS` |
| Seedance | $$/mo | Stable Video Diffusion / AnimateDiff | Via ComfyUI AnimateDiff nodes |
| Perplexity Pro | $20/mo | SearXNG + Ollama | `docker run searxng` + `ollama pull` |
| Railway / Heroku | $20+/mo | Coolify / Docker VPS | `docker compose up -d` |
| **Total proprietary** | **$920+/mo** | **$5–$20/mo (VPS only)** | |

---

## Infrastructure Stack

### Data Pipeline: Airbyte + ClickHouse

```bash
docker run -d --name airbyte -p 8000:8000 airbyte/airbyte
docker run -d --name clickhouse -p 8123:8123 clickhouse/clickhouse-server
```

Connect: Facebook Ads, Google Analytics, PostHog, Stripe, CRM → Airbyte → ClickHouse.

### Creative Generation: ComfyUI

```bash
pipx install comfy-cli
comfy --skip-prompt install --nvidia
comfy model download --url "https://huggingface.co/stabilityai/stable-diffusion-xl-base-1.0/resolve/main/sd_xl_base_1.0.safetensors" --relative-path models/checkpoints
comfy launch --background
```

### Research: SearXNG + Ollama

```bash
docker run -d --name searxng -p 4000:8080 searxng/searxng
curl -fsSL https://ollama.com/install.sh | sh
ollama pull llama3.2
```

### Avatar Video: Wav2Lip + Coqui TTS

```bash
pip install TTS
docker pull ghcr.io/wan-h/wav2lip:latest
tts --text "Your ad copy" --model_name tts_models/en/ljspeech/tacotron2-DDC --out_path output.wav
```

### Agent Hosting: Coolify or Docker VPS

Coolify is an open-source PaaS (Heroku alternative) you self-host. One-click deploy from GitHub.

---

## Weekly Agent Cycle

### Monday: Research Pain Points

Scrape Reddit via SearXNG → Extract pains via Ollama LLM → Rank by frequency

### Tuesday-Wednesday: Generate Creative

ComfyUI for images (5 per pain point) + Wav2Lip for avatar video → Brand compliance check via vision model

### Thursday-Sunday: Publish & Optimize

Ads created in PAUSED status → 48-hour learning window → Kill bottom 30% → Promote top winners → Store winning patterns

---

## Facebook Marketing API Safety

**DO:** Create ads, turn off losers, promote winners (write-only)
**DO NOT:** Bulk-pull millions of rows of data (gets accounts banned)

Rate limit: 0.5s between calls. Start ads in PAUSED for human review.

---

## Budget Controls

- Daily cap: $50/day
- Max CPA: $15
- Max ads per batch: 10
- Learning window: 48 hours minimum
- Human review gate: ads start PAUSED

---

## Monthly Cost Comparison (Self-Hosted)

| Component | Proprietary | Self-Hosted |
|-----------|------------|-------------|
| Data pipeline | $500+ (Fivetran) | $0 (Airbyte) |
| Warehouse | $200+ (Snowflake) | $0 (ClickHouse) |
| Image gen | $60+ (Kai/Midjourney) | $0 (ComfyUI) |
| Video avatars | $120+ (HeyGen) | $0 (Wav2Lip) |
| Research | $20 (Perplexity) | $0 (SearXNG) |
| Hosting | $20+ (Railway) | $5-20 (VPS) |
| **Total** | **$920+/mo** | **$5-20/mo** |

---

## Key Principles

1. Marketing is continuous, not campaign-based
2. Test 10-15-20 variations before giving up
3. Let the market tell you what works — test everything
4. Start with human review, graduate to autonomy
5. Self-host everything you can

## 📺 Source Videos

- [Marketing Agents Are Too Good Now](https://www.youtube.com/watch?v=U2hogriGmEw) — Greg Isenberg

**Difficulty**: Advanced

## Prerequisites

- Docker
- Python 3.10+
- Facebook Ads account
- GPU recommended for ComfyUI
