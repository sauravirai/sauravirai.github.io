Design Pattern · Multi-Agent Systems
# 🧠 How My Agent Stack Composes
Three reusable patterns — and one meta-pattern — that let five agents share state, delegate context,
      and serve new surfaces without rewriting each other.
Sauravi Rai · Personal agent stack · May 2026
Single agents are easy. The leverage is in**how they compose**.
      Most "PM agent" stacks are point solutions: one agent, one workflow, opaque state — they don't compound.
      These patterns are what change that.Pattern 1
## Shared Preference Profiles
Two agents touch the same workflow — the**Room Agent**and the**Copilot Studio meeting plugin**both read the same per-user JSON preference file.
        Onboard once, behave consistently across every surface.
        New surfaces (Slack shortcut, mobile) plug into the same profile without touching any existing agent.
```
~/.config/meeting-prefs/<userId>.json
       ↑                ↑
       │                │
   Room Agent      Copilot Plugin
   (AgentRunner)   (Teams surface)
```
**Why it matters:**The profile is the contract. Add a new surface — Slack bot, mobile shortcut, web widget —
        without writing a single new rule.Pattern 2
## Cross-Agent Queries — Decoupled, Single Source of Truth
The**Task Wrangler**doesn't_store_re-org context — it_queries_the**Org Change Agent**when assembling the daily digest. Update the org structure once;
        every downstream digest reflects it. Each agent owns its domain. No agent duplicates another's state.
```
Outlook    ─┐
Jira       ─┼──→ Task Wrangler ──→ Daily digest
Confluence ─┤         │
OneNote    ─┘         │  query("priority stakeholders this week?")
                      ▼
               Org Change Agent ──→ stakeholder map + OKRs
                      │
                      └─ owns the source of truth
```
**Why it matters:**This is microservice composition applied to LLM agents.
        The org-change context belongs to one agent. Everything else just_asks_.Pattern 3
## Read-Side Projections — Disposable Views, Durable Truth
The**AI Usage Tracker**stores nothing. Each invocation pulls live from the platform API
        and renders a flat HTML report, published via the share agent.
        Reports go stale; APIs don't. Keep the source authoritative — treat reports as cheap, regenerate on demand.
        The**Storyteller**uses the same pattern for slide decks.
```
Platform API ──→ AI Usage Tracker ──→ flat HTML ──→ share-agent ──→ published URL
   ↑                                                      │
   └───────────────── (re-pull anytime) ─────────────────┘
```
**Why it matters:**Zero stale data problem. Any report is disposable. Pull fresh, publish, move on.Meta-Pattern
## 🐑 The Stack Shepherd — An Agent That Tends the Stack Itself
Agent #6 operates_on_the stack rather than alongside it. It edits READMEs, pushes to GHE,
        regenerates the dashboard, re-invokes Storyteller when the deck goes stale, and onboards new agents
        into the config itself. Maintenance becomes a tool call — not a calendar reminder you'll ignore.
```
        ┌──────── Stack Shepherd ────────┐
        │                               │
        ▼                               ▼
README, ORCHESTRATION.md       invokes: task-agent,
agents/, PLAN.md                        share-agent,
        │                               storyteller,
        ▼                               agent-creator
 git push → GHE
        │
        ▼
 share-agent → published URL
```
**Why it matters:**Every published stack rots without a steward.
        Embedding the steward_as_an agent makes maintenance automatic.
        This is the pattern that makes a community-of-practice sustainable long term.
## Why This Matters at Platform Level🔌
### Add agents without rewriting old ones
Cross-agent queries mean new agents just ask existing ones for what they need.
          No agent needs to know about every other agent.📱
### Add surfaces without rewriting agents
Shared profiles mean a new Slack shortcut or mobile surface inherits the exact same
          per-user behaviour with zero new code.🔄
### Regenerate reports at zero cost
Read-side projections make every report disposable.
          Pull fresh, publish, move on. No stale data debt accumulates.
## What's Not Here Yet◻Persistent memory layer
Each agent currently has its own context window. Evaluating a PM Chief of Staff agent for shared decision capture across the stack.◻Always-on customer intelligence
No Voice-of-Customer agent in the stack yet. Evaluating existing tools before building.◻Experiment monitor
A/B test outcome tracking against PRD criteria — planned for A/B-heavy cycles.
## How to Extend This Stack
- 1.**Build your agent**as a normal subagent config — one capability, one JSON file.
- 2.**Pick a composition pattern**from above — or document a fourth one.
- 3.**Document the contract:**what does this agent_own_, what does it_query_, what does it_project_?
- 4.**Open a PR**with the config + a brief addition to this doc. Forks welcome. PRs welcomer.