# 🐾 [USER_NAME]'s Agent Stack

> Five composable agents that take the coordination overhead off a PM's plate so the human can do product thinking.

Built by **[USER_NAME]** · Senior Director, Product Management ([BUSINESS_UNIT]) · ExampleCorp [OFFICE_LOCATION]

---

## ⚡ TL;DR

Most "PM productivity AI" pitches give you one bot for one workflow. This stack is different: **five agents that share state and compose**, so context moves with the work — across calendar, tasks, org-change, adoption metrics, and storytelling.

| Agent | What it does for me | Tools |
|---|---|---|
| 📅 **[Meeting Room Agent](agents/meeting-room-agent.json)** | Books M365 rooms respecting per-user prefs, manages recurring series, onboards new users | 12 |
| 🪢 **[Task Wrangler](agents/daily-task-agent.json)** | One daily digest pulling action items from Outlook, Jira, Confluence, OneNote, and the org-change agent. Drafts polite follow-ups | 26 |
| 🏗️ **[Org Change Agent](agents/[USER_NAME]-org-context-agent.json)** | Re-org transitions: stakeholder maps, hierarchy tracking, OKR resets, Rewards & Calibration guidance | 4 |
| 📊 **[AI Usage Tracker](agents/ai-usage-tracker.json)** | Live 90-day AgentRunner + InternalAgentPlatform adoption stats; benchmarks against [SENIOR_LEADER]+ network and the [OFFICE_LOCATION] PM cohort | 6 |
| 📖 **[Storyteller](agents/storyteller.json)** | Turns an associate's AgentRunner journey into a self-contained, branded HTML slide deck | 7 |
| 🐑 **[Stack Shepherd](agents/stack-shepherd.json)** | Tends this stack itself — keeps artifacts fresh, pushes updates to GHE, drafts community comms, onboards new agents | 9 |

**Headcount of agents in daily use: 6** — well past [SENIOR_LEADER] "3–5 per PM" bar.

---

## 🧠 The orchestration pattern (this is the actual asset)

Single agents are easy. The leverage comes from how they share state. This stack uses three composition patterns:

### 1. Shared preference profiles
The Room Agent and the Copilot Studio meeting plugin both read the same per-user preference JSON. Onboard once, behave consistently across surfaces.

### 2. Cross-agent queries
The Task Wrangler doesn't try to *know* about my re-org context — it **queries the Org Change Agent** for stakeholder priorities and surfaces them in the daily digest. Decoupled, single-source-of-truth.

### 3. Read-side projections
The AI Usage Tracker doesn't store its own state — it pulls live from the InternalAgentPlatform API and renders a flat HTML report (published via share-agent). Disposable views, durable upstream truth.

📖 Full pattern doc: **[ORCHESTRATION.md](ORCHESTRATION.md)** *(in progress)*

---

## 🚀 Quick start (use any agent)

```bash
# In AgentRunner:
/agent meeting-room-agent
/agent daily-task-agent
/agent [USER_NAME]-org-context-agent
/agent ai-usage-tracker
/agent storyteller
```

Each agent's JSON config lives in [`agents/`](agents/) and is portable — drop into `~/.agentrunner/agents/` and it's wired in.

---

## 🗂 Repo layout

```
[USER_NAME]-agent-stack/
├── README.md                        ← you are here
├── ORCHESTRATION.md                 ← how agents compose
├── agents/                          ← agent contracts (JSON configs)
├── services/
│   ├── meeting-room-bridge/         ← M365 backend for Room Agent
│   ├── meeting-room-copilot-studio/ ← Copilot Studio surface
│   ├── org-context-agent/            ← re-org tracking app
│   └── ai-usage-reports/            ← adoption report tooling
└── docs/
    ├── examples/
    └── adoption-stories.md
```

---

## 🎯 Why this exists

[SENIOR_LEADER]'s note (May 2026) anchored a community-of-practice around PM-built agents. He wrote:

> *"[USER_NAME]'s stack is one of the closest examples of multiple agents running together across workflows. This is where agents start to compound into platform level leverage."*

This repo is the open invitation: **fork it, plug in, improve it, share back.** If you're a PM trying to get to 3–5 agents in your day-to-day, start here.

---

## 🤝 Use it, fork it, contribute

- **Use it:** copy any `agents/*.json` into your `~/.agentrunner/agents/` and run
- **Fork it:** strip my ground-truth files, swap in yours, you're off
- **Contribute:** open a PR with a new agent that fits the orchestration pattern
- **Talk:** find me in the [AgentRunner Teams channel](https://teams.example.com/channel/redacted)

---

## 📖 The journey story

🖥️ **[How this stack came to be — 7-slide deck](docs/journey-story.html)** (also published on internal.example.com)

What [SENIOR_LEADER] calling for, the 5 agents, the orchestration pattern, and 3 ways your team can leverage this. Built by the [Storyteller](agents/storyteller.json) agent itself — dogfooding all the way down.

---

## 📊 Live tracker

I'm tracking my own adoption + roadmap publicly:
**Agent Stack Tracker** (published via share-agent)

---

_Built on [AgentRunner](https://agent-platform.example.com ExampleCorp-internal._
