Personal Agent Stack · PM Productivity
# 🐾 Personal Agent Stack
Six composable agents that take the coordination overhead off a PM's plate —
      so the human can do product thinking.🤖6 agents · 64 combined tools · daily use
Sauravi Rai · Senior Director, Product Management · May 2026
## ⚡ TL;DR
Most "PM productivity AI" pitches give you one bot for one workflow.
      This stack is different:**six agents that share state and compose**,
      so context moves with the work — across calendar, tasks, org-change, adoption metrics, and storytelling.
| Agent | What it does | Tools |
|---|---|---|
| 📅 Meeting Room Agent | Books M365 rooms respecting per-user prefs, manages recurring series, onboards new users | 12 |
| 🪢 Task Wrangler | Daily digest pulling action items from Outlook, Jira, Confluence, OneNote, and the org-change agent. Drafts polite follow-ups. | 26 |
| 🏗️ Org Change Agent | Re-org transitions: stakeholder maps, hierarchy tracking, OKR resets, Rewards & Calibration guidance | 4 |
| 📊 AI Usage Tracker | Live 90-day AI-tools adoption stats; benchmarks against director+ network and local PM cohort | 6 |
| 📖 Storyteller | Turns an associate's agent journey into a self-contained, branded HTML slide deck | 7 |
| 🐑 Stack Shepherd | Tends this stack itself — keeps artifacts fresh, pushes updates to GHE, onboards new agents | 9 |

## The Agents📅
### Meeting Room Agent
Books M365 conference rooms while respecting per-user preferences — buffer times, room size, AV needs.
          Manages recurring series updates. Onboards new users with a one-time setup flow.On marketplace · Multi-tenant🪢
### Task Wrangler (Daily Digest)
Aggregates action items from Outlook, Jira, Confluence, and OneNote into one ranked daily brief.
          Queries the Org Change Agent for stakeholder context. Drafts polite follow-up messages.26 tools · Personal instance🏗️
### Org Change Agent
Single source of truth for re-org transitions. Owns stakeholder maps, hierarchy tracking,
          OKR resets, and Rewards & Calibration guidance. Queried by the Task Wrangler — never duplicated.Keep-local · HR-adjacent context📊
### AI Usage Tracker
Live 90-day AI-tools adoption stats for the team. Benchmarks against Director+ network
          and the local PM cohort. Publishes a flat HTML report on demand — zero stored state.Read-side projection pattern📖
### Storyteller
Interviews an associate over 3 rounds, then generates a self-contained branded HTML slide deck
          of their agent-building journey — published and shareable in minutes. On the marketplace.On marketplace · 7 tools🐑
### Stack ShepherdMeta
Tends the stack itself. Edits READMEs, pushes to GHE, regenerates dashboards, re-invokes Storyteller
          when decks go stale. Maintenance as a tool call — not a forgotten calendar reminder.Operates on the stack · 9 tools
## 🧠 The Orchestration Pattern
Single agents are easy. The leverage comes from how they share state.
      This stack uses three composition patterns —full pattern doc ↗1. Shared Preference Profiles
Room Agent and Copilot Plugin both read the same per-user preference JSON. Onboard once, consistent across every surface.2. Cross-Agent Queries
Task Wrangler doesn't store re-org context — it queries the Org Change Agent for stakeholder priorities. Decoupled, single source of truth.3. Read-Side Projections
AI Usage Tracker stores nothing — pulls live from the platform API and renders a fresh HTML report. Disposable views, durable upstream truth.
## 🗂 Repo Layout
```
agent-stack/
├── README.md                        ← you are here
├── ORCHESTRATION.md                 ← how agents compose
├── agents/                          ← agent contracts (JSON configs)
│   ├── meeting-room-agent.json
│   ├── daily-task-agent.json
│   ├── org-context-agent.json
│   ├── ai-usage-tracker.json
│   ├── storyteller.json
│   └── stack-shepherd.json
├── services/
│   ├── meeting-room-bridge/         ← M365 backend for Room Agent
│   ├── meeting-room-copilot-studio/ ← Copilot Studio surface
│   ├── org-context-agent/           ← re-org tracking app
│   └── ai-usage-reports/            ← adoption report tooling
└── docs/
    ├── examples/
    └── adoption-stories.md
```

## 🎯 Why This Exists
> "This stack is one of the closest examples of multiple agents running together across workflows.
      This is where agents start to compound into platform-level leverage."
— Note from senior leadership that anchored a community-of-practice around PM-built agents, May 2026
This repo is the open invitation:**fork it, plug in, improve it, share back.**If you're a PM trying to get to 3–5 agents in your day-to-day, start here.
## 🚀 Quick Start
Each agent's JSON config is portable — drop into your agent runner's config directory and it's wired in.
```
# Copy any agent config into your local agent runner:
cp agents/meeting-room-agent.json ~/.agentrunner/agents/
cp agents/daily-task-agent.json   ~/.agentrunner/agents/
cp agents/storyteller.json        ~/.agentrunner/agents/

# Then invoke:
/agent meeting-room-agent
/agent daily-task-agent
/agent storyteller
```

## 🤝 Use it · Fork it · Contribute📦
### Use it
Copy any`agents/*.json`into your agent runner config and start running immediately. No setup ceremony.🍴
### Fork it
Strip my ground-truth files, swap in yours. The composition patterns are yours to keep — the personal context is easy to replace.🔧
### Contribute
Open a PR with a new agent that fits one of the three composition patterns. Document the contract: what it owns, queries, or projects.
## Related Portfolio PiecesDesign PatternMulti-Agent Orchestration Patterns ↗
Full writeup of the three composition patterns with architecture diagrams.Design PatternRules-Based Agent Governance ↗
20 governance rules baked into the AI Tools Adoption Tracker — from 73 real iteration cycles.