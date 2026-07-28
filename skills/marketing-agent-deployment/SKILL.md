---
description: Step-by-step deployment walkthrough for the self-hosted marketing agent
  stack — from zero to a running agent on open-source infrastructure.
name: marketing-agent-deployment
tags:
- deployment
- self-hosted
- infrastructure
- Docker
- setup
- walkthrough
- Airbyte
- ClickHouse
- SearXNG
- Ollama
- ComfyUI
---

# marketing-agent-deployment

> Step-by-step deployment walkthrough for the self-hosted marketing agent stack — from zero to a running agent on open-source infrastructure.

> From zero to a running marketing agent in ~2 hours. Concrete commands, config files, and wiring steps.

## Phase 1: Server Setup

```bash
# Provision a VPS (Hetzner CX22 ~8/mo or DigitalOcean $12/mo)
ssh root@YOUR_SERVER_IP
curl -fsSL https://get.docker.com | sh
sudo usermod -aG docker $USER && newgrp docker
```

## Phase 2: Data Infrastructure

```yaml
# docker-compose.yml
services:
  airbyte:
    image: airbyte/airbyte:latest
    ports: ["8000:8000"]
    volumes: ["./data/airbyte:/data"]
  clickhouse:
    image: clickhouse/clickhouse-server:latest
    ports: ["8123:8123"]
    volumes: ["./data/clickhouse:/var/lib/clickhouse"]
  searxng:
    image: searxng/searxng:latest
    ports: ["4000:8080"]
    volumes: ["./data/searxng:/etc/searxng"]
```

```bash
docker compose up -d
```

## Phase 3: Install Ollama + ComfyUI

```bash
curl -fsSL https://ollama.com/install.sh | sh
ollama pull llama3.2
pipx install comfy-cli
comfy --skip-prompt install --nvidia
comfy model download --url <SDXL_URL> --relative-path models/checkpoints
comfy launch --background
```

## Phase 4: Deploy the Agent

Create project structure, Dockerfile, agent.py with the weekly cycle loop. Build and run:

```bash
docker build -t marketing-agent .
docker run -d --name marketing-agent --env-file .env --restart unless-stopped marketing-agent
```

## Phase 5: Verification

- [ ] Airbyte at port 8000
- [ ] ClickHouse: `docker compose exec clickhouse clickhouse-client -q "SELECT 1"`
- [ ] SearXNG: `curl localhost:4000/search?q=test`
- [ ] Ollama: `curl localhost:11434/api/tags`
- [ ] ComfyUI: `curl localhost:8188/system_stats`

## Troubleshooting

| Symptom | Fix |
|---------|-----|
| Agent won't start | Check .env has all required vars |
| FB API 403 | Refresh access token |
| No data in ClickHouse | Check Airbyte sync status |
| Ads not spending | Set HUMAN_REVIEW=false after verification |

## References
- **Architecture:** `npx skills add TDH-Labs/i-know-kung-fu --skill marketing-agents-are-too-good-now`
- **Source video:** https://youtu.be/U2hogriGmEw

## 📺 Source Videos

- [Marketing Agents Are Too Good Now](https://www.youtube.com/watch?v=U2hogriGmEw) — Greg Isenberg

**Difficulty**: Intermediate

## Prerequisites

- Docker
- VPS or server with 4GB+ RAM
- Facebook Ads account
