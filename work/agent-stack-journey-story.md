Skip to deck01 / 07For the PM team
# PMAgentic Leverage
— a stack you canfork.
**5 composable agents · 1 orchestration pattern · ready to adopt.****Sauravi**Senior Director, Product Management · Walmart International
Walmart Bengaluru · May 20265📖📅🪢🏗️📊Set the frame in one breath: this isn't a personal showcase, it's a gift to the team. Five agents, one pattern, ready to fork. The whole deck takes about five minutes — open the repo at the end and pick which agent or pattern you'll try first.02 / 07The call to action
## What leadership calling for.
From his note to the PM org — the bar is now explicit.
> "If you are not yet at**3–5 agents impacting your day-to-day productivity**, that is the gap you need to close. This will be a defining part of the PM role. The teams that lean in early will move faster, make better decisions, and operate at a**very different level of leverage**."— leadership, SVP eCommerce Product1
#### Get to 3–5 agents
In daily use. Not demos, not prototypes — agents that change how your week runs.2
#### Publish, share, fork
Don't build in parallel. The org's leverage scales with reuse, not with re-invention.3
#### Compose into platform leverage
Multiple agents, shared patterns, working across surfaces. That's the unlock.Read the quote, then frame the three asks plainly. The bar is no longer "experiment with AI" — it's a measurable count and a publishing expectation. The rest of the deck is one PM's contribution toward that bar so others don't have to start from zero.03 / 07The stack
## 5 agents in this stack.
All live, all in daily use, all in the repo. Pick one, copy it in, run it tonight.📅
### Room Agent
Books M365 rooms with your prefs. Manages recurring series and conflicts.🪢
### Task Wrangler
One daily digest from Outlook, Jira, Confluence, OneNote.🏗️
### Org Change Agent
Re-org tracking: stakeholder maps, OKR resets, rewards & calibration.📊
### AI Usage Tracker
Live adoption stats. Exec-ready reports, no spreadsheet wrangling.📖
### Storyteller
Turns an associate journey into a branded slide deck. (Built this deck, in fact.)
Each one is a single JSON file plus a small backend. Standalone today — but they get more interesting when you compose them. ↓Walk the row left to right, one sentence each. The point isn't that these five are special — it's that every PM probably has the seeds of three or four already. The repo just makes them shareable. Land on the bridge to slide 4: the real gift is composition, not the agents themselves.04 / 07The actual gift
## The orchestration pattern.
Three composition primitives. This is what compounds into platform leverage.
### ① Shared preference profiles
One JSON describes you. Every agent reads it. Onboard once, behave consistently across surfaces.
**Example:**Room Agent and the Copilot plugin read the same`prefs.json`. Change "no meetings before 9am" in one place — both honor it.
### ② Cross-agent queries
Agents call each other instead of duplicating state. Single source of truth, decoupled lifecycles.
**Example:**Task Wrangler queries**Org Change Agent**for stakeholder priorities — no duplicated lookup tables, no drift.
### ③ Read-side projections
Source authoritative, views cheap. Render disposable HTML off durable upstream APIs.
**Example:**AI Usage Tracker pulls live from the**InternalAgentPlatform API**and renders disposable HTML reports. Throw the view away anytime.
**Pattern matters more than any individual agent.**Adopt the patterns and your stack composes too.Slow down here — this is the headline asset. Each pattern is one paragraph and one concrete example, on purpose. Encourage the room to pick the one most relevant to their work and skim ORCHESTRATION.md for the implementation. The patterns are the thing they should steal first.05 / 07How to leverage this
## 3 ways for your team to lean in.
Pick the one that matches where you are this week.1
#### Use it
Copy any`agents/*.json`into`~/.agentrunner/agents/`and run. Zero setup.2
#### Fork it
Personal data is gitignored. Example template provided. Make it yours in an afternoon.3
#### Compose it
Pick a pattern from the previous slide. Build your own agent that plugs into the stack. Open a PR.
Three doors, one room. Whichever you walk through, you're closer to leadership–5 bar by the end of the week.Make it easy to act. "Use it" is for the PM who wants a quick win. "Fork it" is for the PM with a specific workflow that's almost — but not quite — covered. "Compose it" is for the PM who wants to shape the platform. All three count.06 / 07Where the team can lead
## What's missing — and who's closest.
Three open lanes that align with leadership. Pick one and lead it.🧠
#### Persistent memory layer for decisions & context
A durable "what did we decide and why" surface across PRDs, reviews, and threads. A**PM Chief of Staff agent**is closest.leadership #1 · Memory🎙️
#### Always-on Voice of Customer
Continuous signal from support, NPS, and field — surfaced in PM workflows, not just dashboards.**Customer Compass agent**is live.leadership #2 · Customer intelligence🧪
#### Experiment monitor against PRD success criteria
Auto-watch live experiments and flag drift from the PRD's stated success bar.**Andrew & Nader**are exploring.leadership #4 · Metrics
These aren't gaps in one stack — they're**opportunities for the team**. Pick one, partner with the lead, and publish what you build.Frame these as opportunities, not deficiencies. Each one already has a credible owner closest to it — make the introduction rather than re-build. The takeaway: there's a clear roadmap toward leadership, and there's room for a few more PMs to put their name next to a lane.07 / 07Get started
## Take it. Use it. Make it better.
Four ways in — pick one before you close this tab.[🔗**Repo**internal.example.com/user-id/Sauravi-agent-stack](https://github.example.com aria-label=)[📊**Live tracker**internal.example.com/sharing/user-id/sauravi-agent-stack-tracker](https://agent-platform.example.com
          <span class=)💬**Slack thread**Drop in the thread leadership✉️**Email me**sauravi.rai@example.com
The PMs who lean in early operate at_very different leverage._Let's go.Close warm but with a clear ask: don't leave without committing to one of the four doors. Echo leadership deliberately — this is a continuation of his note, not a separate initiative. Then invite questions.