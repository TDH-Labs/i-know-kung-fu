# Second Brain — System Evaluation & Build Plan

> Generated: 2026-07-24
> Skill installed: `AI Research OS Implementation` → `~/.agents/skills/ai-research-os-implementation/`

---

## Part 1: System Evaluation

### ✅ What's Already in Place

| Component | Status | Details |
|-----------|--------|---------|
| **Obsidian** | ✅ Installed | `/Applications/Obsidian.app` — Vault at `~/Documents/Obsidian Vault/` |
| **Obsidian Local REST API** | ✅ Installed & Configured | Plugin v3.6.1, port 27124, API key active |
| **Obsidian Sync** | ✅ Enabled | iCloud sync is on (core plugin) |
| **Vault Structure** | ⚠️ Partial | 5 folders (00-04), but sparse — 25 files total, mostly marketing daycare content |
| **Python + ML Stack** | ✅ Good | numpy, pandas, scikit-learn, openai, langchain, litellm |
| **Docker** | ✅ Available | v29.4.0 — can run vector DBs in containers |
| **Git** | ✅ Available | v2.50.1 |
| **Node.js** | ✅ Available | v22.22.3 |
| **Harbor Agent System** | ✅ Advanced | 11 rooms, 365+ skills, room-scoped agents |
| **Data Layer** | ✅ Good | `~/data/` directory with catalog, structured for queries |
| **Research Room** | ✅ Configured | Has arXiv, web search, polymarket skills |
| **Productivity Room** | ✅ Configured | Has 53 skills including databases, automation |
| **iCloud Sync** | ✅ Available | iCloud~md~obsidian present |
| **AI Research OS Skill** | ✅ Installed | `~/.agents/skills/ai-research-os-implementation/` |

### ❌ What's Missing

| Component | Status | Priority |
|-----------|--------|----------|
| **Vector Database** | ❌ Not installed | 🔴 Critical — needed for semantic search / RAG |
| **Embedding Model** | ❌ Not installed | 🔴 Critical — `sentence-transformers` not installed |
| **Readwise Integration** | ❌ Not installed | 🟡 Nice-to-have — highlights pipeline |
| **Obsidian Plugin Ecosystem** | ❌ Bare | Only 1 plugin (REST API); no Dataview, Templater, QuickAdd, Kanban |
| **Vault Index / MOC** | ❌ Missing | No Map of Content, no index.yaml, no cross-linking |
| **Scheduled Ingestion** | ❌ Missing | No cron jobs, no automated daily capture |
| **Research OS Scripts** | ❌ Missing | `ingest.py`, `research.py`, `query_engine` not created |
| **Automated Backups** | ⚠️ Partial | iCloud sync yes, but no local git-based versioning for notes |
| **Second Brain Dashboard** | ❌ Missing | No personalized dashboard for knowledge review |
| **Handoff Protocol** | ❌ Not configured | No session continuity between agents for knowledge work |

### 📊 Asset Inventory

**Existing Data:**
- **8,636 markdown files** in `~/workspace/` — project notes, docs, handoffs
- **2,792 markdown files** in `~/data/` — structured skill libraries, knowledge bases
- **25 files** in Obsidian vault — mostly marketing/business strategy content
- **200+ skills** in `~/data/i-know-kung-fu/` — AI skill reference library
- **Harbor agent system** with 11 room-scoped agents

**Key Infrastructure:**
- Docker available for vector DBs (ChromaDB, Qdrant)
- Python 3.9 with langchain, openai, liteLLM
- Obsidian REST API ready to be queried programmatically
- iCloud sync for mobile access

---

## Part 2: Build Plan — Second Brain for This Machine

### 🎯 Architecture Overview

```
┌─────────────────────────────────────────────────────────────┐
│                    SECOND BRAIN SYSTEM                        │
├─────────────────────────────────────────────────────────────┤
│                                                               │
│  ┌─────────────────────────────────────────────────────┐    │
│  │              INGESTION LAYER                         │    │
│  │  ┌─────────┐ ┌──────────┐ ┌────────┐ ┌──────────┐  │    │
│  │  │ Obsidian│ │ Workspace│ │ Data   │ │ External │  │    │
│  │  │ Vault   │ │ .md files│ │ Layer  │ │ Sources  │  │    │
│  │  └────┬────┘ └────┬─────┘ └───┬────┘ └────┬─────┘  │    │
│  └───────┼───────────┼───────────┼───────────┼────────┘    │
│          │           │           │           │              │
│  ┌───────▼───────────▼───────────▼───────────▼────────┐    │
│  │              INDEX LAYER                            │    │
│  │  ┌────────────────┐  ┌──────────────────────────┐  │    │
│  │  │  index.yaml    │  │  Vector DB (ChromaDB)    │  │    │
│  │  │  (metadata)    │  │  (semantic embeddings)   │  │    │
│  │  └────────────────┘  └──────────────────────────┘  │    │
│  └───────────────────────┬────────────────────────────┘    │
│                          │                                  │
│  ┌───────────────────────▼────────────────────────────┐    │
│  │              KNOWLEDGE LAYER (Wiki)                 │    │
│  │  ┌──────────┐ ┌──────────┐ ┌──────────────────┐   │    │
│  │  │ Concepts │ │Comparisons│ │ Research Questions│   │    │
│  │  └──────────┘ └──────────┘ └──────────────────┘   │    │
│  └───────────────────────┬────────────────────────────┘    │
│                          │                                  │
│  ┌───────────────────────▼────────────────────────────┐    │
│  │              QUERY LAYER                            │    │
│  │  ┌──────────┐ ┌──────────┐ ┌──────────────────┐   │    │
│  │  │ Obsidian │ │ Harbor   │ │ Handoff System   │   │    │
│  │  │ Graph    │ │ Agents   │ │ (session cont.)  │   │    │
│  │  └──────────┘ └──────────┘ └──────────────────┘   │    │
│  └─────────────────────────────────────────────────────┘    │
│                                                               │
└─────────────────────────────────────────────────────────────┘
```

### 📋 Phase 1: Foundation (Week 1)

**1.1 — Upgrade Obsidian Vault**
- [ ] Install core plugins: **Dataview**, **Templater**, **QuickAdd**, **Kanban**
- [ ] Create Map of Content (MOC) structure
- [ ] Set up folder structure per AI Research OS pattern:
  ```
  Obsidian Vault/
  ├── 00_MOC/              # Maps of Content
  ├── 01_Inbox/            # Quick capture
  ├── 02_Projects/         # Active projects
  │   ├── agent-environment/
  │   ├── bookkeeping/
  │   └── ...
  ├── 03_Areas/            # Ongoing responsibilities
  ├── 04_Resources/        # Reference material
  ├── 05_Archive/          # Completed/obsolete
  └── 06_Second_Brain/     # AI-generated wiki, concepts, comparisons
      ├── raw/
      ├── wiki/
      └── index.yaml
  ```

**1.2 — Install Vector DB + Embeddings**
- [ ] `pip install sentence-transformers chromadb`
- [ ] Set up ChromaDB as Docker container (or local)
- [ ] Create initial embedding pipeline

**1.3 — Create Ingestion Scripts**
- [ ] `ingest.py` — Scans workspace .md files, generates summaries, indexes
- [ ] `obsidian-sync.py` — Pulls vault via REST API, syncs to index
- [ ] Auto-update `index.yaml` with metadata

### 📋 Phase 2: Integration (Week 2)

**2.1 — Harbor Agent Integration**
- [ ] Route the AI Research OS skill to the **Research** room
- [ ] Route second brain query skills to **Productivity** room
- [ ] Create a `second-brain-agent` role in Harbor

**2.2 — Obsidian ↔ Agent Bridge**
- [ ] Script to query Obsidian via REST API from agents
- [ ] Auto-create Obsidian notes from agent research sessions
- [ ] Bidirectional link between vault and `~/data/`

**2.3 — Daily Capture Routine**
- [ ] Morning routine: summarize yesterday's work, link to vault
- [ ] Scheduled ingestion of new workspace files
- [ ] `open_questions/` directory auto-populated from unfinished threads

### 📋 Phase 3: Intelligence (Week 3)

**3.1 — AI Wiki Generation**
- [ ] Concept extraction from ingested notes
- [ ] Auto-linking between related topics
- [ ] Comparative analyses (e.g., "approaches to X")

**3.2 — Query Interface**
- [ ] `query.py` — Semantic search across all knowledge sources
- [ ] Progressive disclosure: summary → wiki → raw
- [ ] Integration with Harbor agents for context-aware responses

**3.3 — Dashboard**
- [ ] Weekly review dashboard (what's new, what's stale)
- [ ] Knowledge gap analysis (from `open_questions/`)
- [ ] Re-indexing alerts for stale content

### 📋 Phase 4: Maintenance (Ongoing)

**4.1 — Weekly Review**
- [ ] Review open questions → resolve or discard
- [ ] Prune stale wiki entries
- [ ] Re-index changed source files

**4.2 — Monthly Deep Clean**
- [ ] Archive inactive projects
- [ ] Update index.yaml
- [ ] Refresh embeddings if models changed

**4.3 — Quarterly**
- [ ] Full system audit
- [ ] Purge `research_archive/` of truly dead content
- [ ] Review and update this plan

---

## Part 3: Quick Wins — Get Started Today

### 🎯 Action 1: Install ChromaDB + Sentence Transformers
```bash
pip install chromadb sentence-transformers
```

### 🎯 Action 2: Create the Second Brain Directory Structure
```bash
mkdir -p ~/second-brain/{raw,index,wiki/{concepts,comparisons,entities},open_questions,research_archive}
```

### 🎯 Action 3: Create Initial index.yaml
```yaml
# ~/second-brain/index.yaml
version: 1.0
sources:
  - path: ~/Documents/Obsidian Vault/
    type: obsidian
    last_indexed: ~
  - path: ~/workspace/
    type: workspace
    last_indexed: ~
  - path: ~/data/
    type: data_layer
    last_indexed: ~
wiki:
  concepts: ~/second-brain/wiki/concepts/
  comparisons: ~/second-brain/wiki/comparisons/
  entities: ~/second-brain/wiki/entities/
open_questions: ~/second-brain/open_questions/
```

### 🎯 Action 4: Test Obsidian REST API
```bash
curl -k -H "Authorization: Bearer 6b5a60ada0346a5e19e8490a390fc74a83a314195d92be0a5219a46acee29f98" \
  https://localhost:27124/vault/
```

### 🎯 Action 5: Install Obsidian Community Plugins
Open Obsidian → Settings → Community plugins → Browse:
- **Dataview** — Query vault as a database
- **Templater** — Advanced templates
- **QuickAdd** — Quick capture workflows
- **Kanban** — Project boards

---

## Part 4: Recommended Tools & Configurations

### Vector Database: ChromaDB
- **Why**: Local, no infrastructure, Python-native, Docker-ready
- **Install**: `pip install chromadb`
- **Usage**: In-process or client-server mode

### Embedding Model: `all-MiniLM-L6-v2`
- **Why**: Fast, lightweight, good accuracy for general knowledge
- **Install**: `pip install sentence-transformers`
- **Usage**: `SentenceTransformer('all-MiniLM-L6-v2')`

### LLM Integration: LiteLLM
- **Why**: Already installed, supports 100+ providers
- **Usage**: `litellm.completion()` for query answering

### Obsidian Sync: iCloud (already set up)
- Mobile access via Obsidian iOS app
- Auto-syncs to vault

---

## Summary

**Current state**: You have excellent infrastructure (Harbor, Docker, Python, Obsidian, 11K+ markdown files) but no **unified knowledge system** connecting them. The Obsidian vault is small and underutilized.

**The opportunity**: With ~11,428 markdown files across your workspace and data directories, there's a massive knowledge base waiting to be indexed, linked, and queried. The AI Research OS skill provides the blueprint; this plan gives you the execution roadmap.

**First step**: Install ChromaDB + sentence-transformers, set up the directory structure, and connect Obsidian via the REST API. That's 30 minutes of work and unlocks the entire system.