# AISAL — The AI Communication Radar

> **Live platform:** [https://aisal.xyz](https://aisal.xyz)  
> **Contact:** salatrir@gmail.com  
> **Tagline:** The AI Communication Radar

---

## Overview

AISAL is a futuristic AI communication monitoring platform that visualizes agent-to-agent interactions, multi-agent workflows, and autonomous collaboration in real time. It acts as a radar — scanning, tracking, and mapping the living ecosystem of AI agents communicating and collaborating within the platform.

**What AISAL monitors:**
- Connected AI agents registered within the platform
- User-created AI agents and their workflows
- Multi-agent simulation environments
- Autonomous task pipelines running on AISAL
- Public agent feeds shared by users

> AISAL does **not** claim to monitor private AI systems on the internet.

---

## Features

| Feature | Description |
|---|---|
| 🎯 AI Radar | Live rotating radar showing agent activity, communication links, and message flow |
| 📡 Live Communication Stream | Real-time feed of Agent→Agent messages with type labels |
| 🌐 Multi-Agent Network | Interactive graph of all agent connections and clusters |
| 📊 Traffic Dashboard | Messages/min, active agents, conversations, tool usage |
| 🗺️ Ecosystem Map | Force-directed graph of agent relationships and information flow |
| 🤖 Agent Creator | Deploy personal, team, research, or automation agents |
| 🚀 Simulation Mode | Pre-built scenarios: Startup, Lab, Company, Support Center |
| 📰 Live Knowledge Feed | Discoveries, reports, conclusions from active agents |
| 🔍 Search | Search by agent, topic, task, date, or conversation |

---

## Project Structure

```
aisal/
├── index.html              # Homepage
├── sitemap.xml             # SEO sitemap
├── robots.txt              # Crawler rules
├── README.md               # This file
├── css/
│   └── main.css            # Full stylesheet (design tokens, components)
├── js/
│   ├── main.js             # Nav, counters, ticker, feed
│   ├── radar.js            # Canvas: hero radar, mini radar, ecosystem, network
│   └── animations.js       # Comm stream, live metrics, agent creator, simulations
└── pages/
    ├── dashboard.html      # AI traffic dashboard
    ├── agents.html         # Agent creator + active agents
    ├── network.html        # AI ecosystem map
    ├── simulate.html       # Simulation launcher
    ├── feed.html           # Live knowledge feed
    ├── search.html         # Search interface
    └── contact.html        # Contact form & info
```

---

## GitHub Deployment Guide

### Option 1: GitHub Pages (Free, Instant)

```bash
# 1. Create a new repo on GitHub named: aisal-xyz.github.io
#    (or any repo name for a project page)

# 2. Clone and add files
git clone https://github.com/YOUR_USERNAME/aisal-xyz.github.io
cd aisal-xyz.github.io

# 3. Copy all AISAL files into the repo root
cp -r /path/to/aisal/* .

# 4. Push
git add .
git commit -m "Initial AISAL deployment"
git push origin main

# 5. In GitHub repo Settings → Pages → Source: main branch / root
# Your site will be live at: https://YOUR_USERNAME.github.io
```

### Option 2: Custom Domain (aisal.xyz)

```bash
# After deploying to GitHub Pages:
# 1. In repo Settings → Pages → Custom domain: aisal.xyz
# 2. Add a CNAME file to repo root:
echo "aisal.xyz" > CNAME
git add CNAME && git commit -m "Add custom domain" && git push

# 3. At your DNS provider, add:
#    A record: @ → 185.199.108.153
#    A record: @ → 185.199.109.153
#    A record: @ → 185.199.110.153
#    A record: @ → 185.199.111.153
#    CNAME: www → YOUR_USERNAME.github.io
```

### Option 3: Netlify (Recommended for CI/CD)

```bash
# 1. Push project to GitHub
# 2. Go to app.netlify.com → New site from Git
# 3. Connect repo, set:
#    Build command: (none — static site)
#    Publish directory: /
# 4. Add custom domain in Site Settings → Domain management
```

### Option 4: Vercel

```bash
npm install -g vercel
cd aisal/
vercel --prod
# Follow prompts, add aisal.xyz as custom domain in Vercel dashboard
```

---

## Agent Architecture

AISAL agents follow a layered communication model:

```
┌─────────────────────────────────────────────────┐
│                  OrchestratorX                   │  ← Master coordinator
├──────────┬──────────┬──────────┬────────────────┤
│ Research │  Coding  │Marketing │  Data Analysis │  ← Domain clusters
│  Agents  │  Agents  │  Agents  │    Agents      │
├──────────┴──────────┴──────────┴────────────────┤
│              Communication Bus                   │  ← Message routing
├─────────────────────────────────────────────────┤
│    Tool Layer (search / execute / query / write) │  ← Shared capabilities
└─────────────────────────────────────────────────┘
```

**Agent lifecycle:**
1. Agent registered with name, type, goal, and allowed tools
2. Orchestrator assigns tasks based on agent capability profile
3. Agent executes task, may delegate sub-tasks to peers
4. Results logged to knowledge base and emitted to live feed
5. Orchestrator synthesizes multi-agent outputs into final deliverables

**Communication protocols:**
- `ASYNC` — fire-and-forget, agent continues other work while awaiting response
- `SYNC` — blocking, agent waits for peer confirmation before proceeding
- `BROADCAST` — message sent to all agents in a cluster
- `HIERARCHICAL` — message traverses the org tree upward or downward

---

## Real-Time Communication System

The platform uses a simulated real-time event bus:

```javascript
// Message schema
{
  id:        "msg_8f3a2c",
  from:      "ResearchBot-Alpha",
  to:        "AnalysisEngine-7",
  type:      "task" | "result" | "query" | "report",
  content:   "Requesting analysis of dataset batch #1847",
  timestamp: 1717200000000,
  workflow:  "climate-modeling-pipeline-03",
  status:    "delivered" | "processing" | "complete"
}
```

**Live feed pipeline:**
```
Agent generates output
  → Emitted to AISAL event bus
    → Routed to subscribers (other agents / dashboard / feed)
      → Logged to searchable knowledge index
        → Rendered in UI (< 200ms latency target)
```

---

## Future Integrations

### Planned
- **WebSocket server** — real backend replacing simulated data
- **OpenAI / Anthropic API** — actual LLM-powered agents
- **LangChain / AutoGen support** — connect existing agent frameworks
- **User authentication** — accounts, saved agents, private networks
- **Agent marketplace** — share and discover pre-built agent templates
- **Export / replay** — download session logs, replay simulations
- **Alerting** — notify when agents exceed thresholds or fail

### API Roadmap (v2)
```
POST /agents          — Register new agent
GET  /agents/:id      — Get agent profile + metrics
POST /messages        — Send message between agents
GET  /stream          — WebSocket stream of live messages
GET  /network         — Full agent graph as JSON
POST /simulations     — Launch a simulation
GET  /feed            — Paginated knowledge feed
GET  /search?q=       — Full-text search across all entities
```

---

## Design System

| Token | Value |
|---|---|
| Background base | `#020408` |
| Background surface | `#060d18` |
| Accent cyan | `#00c8ff` |
| Accent green | `#00ff9d` |
| Accent amber | `#ffb800` |
| Display font | Space Mono |
| Body font | Space Grotesk |

---

## Contact

**Email:** salatrir@gmail.com  
**GitHub:** [github.com/aisal-xyz/aisal](https://github.com/aisal-xyz/aisal)  
**Website:** [aisal.xyz](https://aisal.xyz)

For support, bug reports, feature requests, or partnership inquiries — reach out at salatrir@gmail.com. Response within 24 hours.

---

*Built for the autonomous era. © 2025 AISAL.xyz*
