# 🧠 Orchestration Pattern

How the five agents in this stack compose. The interesting leverage is here, not in any single agent.

---

## Three composition patterns

### 1. Shared preference profiles

Two agents touch calendar/meeting flows: the **Room Agent** (AgentRunner subagent) and the **Copilot Studio meeting plugin**. Both read the same per-user JSON profile.

```
~/.config/meeting-prefs/<userId>.json
       ↑                ↑
       │                │
   Room Agent      Copilot Plugin
```

**Why:** onboard once, behave consistently across surfaces. New surfaces (Slack bot, mobile shortcut) plug into the same profile. No duplicate rules.

### 2. Cross-agent queries (decoupled, single source of truth)

The **Task Wrangler** does not store re-org context. It queries the **Org Change Agent** when assembling the daily digest.

```
Outlook ─┐
Jira  ───┼──→ Task Wrangler ──→ Daily digest
Confluence┤        │
OneNote ─┘         │  query("priority stakeholders this week?")
                   ▼
            Org Change Agent ──→ stakeholder map + active OKRs
                   │
                   └─ owns the source of truth
```

**Why:** the org-change context belongs to one agent. The task agent just *asks*. Update the org structure once, every downstream digest reflects it.

### 3. Read-side projections (disposable views, durable upstream truth)

The **AI Usage Tracker** stores nothing. Each invocation pulls live from the InternalAgentPlatform API and renders a flat HTML report, published via the `share-agent` service.

```
InternalAgentPlatform API ──→ AI Usage Tracker ──→ flat HTML ──→ share-agent ──→ internal.example.com
   ↑                                                                    │
   └────────────────── (re-pull anytime) ──────────────────────────────┘
```

**Why:** reports go stale; the API doesn't. Keep the source authoritative, treat reports as cheap, regenerate on demand. Same pattern the **Storyteller** uses for slide decks.

---

## A meta-pattern: agents that tend the stack itself

The **Stack Shepherd** (agent #6) operates on the stack rather than alongside it — it edits the README, pushes to GHE, regenerates the dashboard, re-invokes Storyteller when the deck goes stale, and onboards new agents into this very file.

```
          ┌────────────── Stack Shepherd ────────┐
          │                                          │
          ▼                                          ▼
  README.md, ORCHESTRATION.md          invokes: daily-task-agent,
  agents/, services/, PLAN.md                   share-agent,
          │                                     storyteller,
          ▼                                     agent-creator
   git push → GHE
          │
          ▼
   share-agent → internal.example.com
```

**Why it matters:** every published stack eventually rots without a steward. Embedding the steward as an agent (rather than a calendar reminder or a doc you'll forget) means maintenance is a tool call, not a chore. This is the pattern that makes a community-of-practice sustainable: each PM's stack has its own shepherd.

---

## Why this matters at the platform level

Most "PM agent" implementations are point solutions: one agent, one workflow, opaque state. That doesn't compound.

The patterns above let you:
- **Add new agents** without rewriting old ones (cross-agent queries)
- **Add new surfaces** (Slack, mobile) without rewriting agents (shared profiles)
- **Regenerate reports/decks at zero cost** (read-side projections)

This is what [SENIOR_LEADER] by "platform level leverage" — agents that *compose* instead of accumulate.

---

## What's NOT here yet (roadmap)

- **Persistent memory layer** — currently each agent has its own context window. Eval Gana's PM Chief of Staff for upstream decision capture (see PLAN.md Phase 4)
- **Always-on customer intelligence** — no VoC agent in the stack yet (Phase 4)
- **Experiment monitor** — A/B test outcome tracking against PRD criteria (Phase 4)

These are the gaps targeted by the published plan.

---

## How to extend this stack

1. **Build your agent** as a normal AgentRunner subagent (`~/.agentrunner/agents/<name>.json`)
2. **Pick a composition pattern** from above (or invent a new one)
3. **Document the contract** — what does it own, what does it query, what does it project?
4. **Open a PR** against this repo with the JSON config + a brief addition to this file

Forks welcome. PRs welcomer.
