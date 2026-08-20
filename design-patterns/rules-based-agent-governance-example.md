Design Pattern · Agent Governance
# 📋 Rules-Based Agent Governance
20 rules — sourced verbatim from real iteration history — baked into an AI agent
      to ensure consistent, respectful, and signal-rich adoption reporting.
Sauravi Rai · AI Tools Adoption Tracker · April 2026
## What this is
When an AI agent generates a recurring report for a real team, "it worked this time" isn't enough.
        The agent needs to behave consistently across every run — even when the model changes, even when data is noisy,
        even when someone who's never edited the code regenerates the report six months later.
This document captures the 20 governance rules encoded into the AI Tools Adoption Tracker agent —
        distilled from 73 real iteration cycles. Each rule is sourced verbatim from the session history
        that produced it. Nothing invented retroactively.
## The Golden Sentence
> 
"[User] first, team second, everything else collapsed. No charts (they don't render).
        No named peer embarrassment. Leaderboards open and high. Leader benchmarks in a collapsed section,
        not at the top. Fun stuff at the bottom. Keep it tight."
This sentence overrides any competing instruction. Every rule below is a specific elaboration of it.
## Canonical Adoption Tiers
Single source of truth — overrides anything in the system prompt. All status chips, leaderboard ranks, and copy must use these labels verbatim.
| Tier | Threshold (90-day requests) | Display label | Emoji |
|---|---|---|---|
| Power | ≥ 5,000 | Power user | 🔥 |
| Heavy | ≥ 500 | Heavy | ⚡ |
| Active | ≥ 100 | Active | 🟢 |
| Light | ≥ 10 | Light | 🌤 |
| Tried | 1 – 9 | Tried | 👋 |
| Getting started | 0 | Getting started | 🌱 |
**Note:**The system prompt may list`❌ None`for 0 requests. That label is wrong for display. Rule 13 always takes precedence: use**🌱 Getting started**.
## The 20 Rules
Verbatim from command history, distilled. Each rule includes the originating verbatim quote that generated it.1Strip inactive leaders; thin out senior-leader data▾
> "remove inactive leaders from report. senior leader — only put as inspirational note, not the full data."
Only active leaders in always-visible sections. Senior-leader peers = inspirational note only, not a full leaderboard row.2Focus = user and their team. Rest takes a back seat▾
> "focus the insights around me and my team. Don't say anything that may be hurtful to folks not adopting the tools as fast."
User's stats and direct team are primary. Broader org data is secondary. Never shame non-adopters.3Standardise labels; scrub redundant icons▾
> "Standardize on the labels you use on the report. Scrub the icons and redundant section names."
Every section uses consistent naming. No duplicate icons, no inconsistent header styles.4Leader benchmarks OUT of always-visible; collapsed only▾
> "removed leader benchmarks from the top section. just lump a) Team drilldown b) Leader benchmarks."
Leadership benchmark data must live in a collapsed`<details>`block. Active leaderboard tables are always-visible.5No named peer comparisons — aggregate insight only▾
> "remove Benchmark vs [senior peers] — instead give insights how I am performing against the org, but label it that way."
Never call out individual peers by name in comparison framing. "Top 25% of org" = fine. "[Name] — 419M tokens" as a direct comparison = not fine.6No standalone Recommendations section — fold into Team Drilldown first▾
> "remove the section on Team Recommendations and within Team Drilldown, just make the insights and recommendations the first section."
Recommendations live inside Team Drilldown as the FIRST sub-section — not a standalone page element.7Top hero = tool-agnostic; no PM/DA split at hero level▾
> "the overall Team AI usage snapshot — it's as much about which tools we are using than how much usage. no need to divide by functional and local or by PM and DA at the top."
Top stat strip shows unified numbers only. Role splits go in drilldowns.8Zero repetition — merge duplicate sections▾
> "annoying repetitions. e.g. What your team is building with AI is unnecessary, just merge in with Full team."
Zero duplicate section headings or content. "What your team is building" is retired — folds into Team section.9Pro Tips → merge into Fun Stuff at the bottom▾
> "take out Pro Tips — across all tools combine with Fun Stuff and put right at the bottom of the report."
Any "tips" or "how to" content belongs at the very bottom. Not mid-report.10Team Drilldown: default OPEN. Fun Stuff: default COLLAPSED▾
> "Team drilldown keep expanded as default. Fun Stuff keep collapsed by default."
`<details open>`on Team Drilldown.`<details>`(no`open`) on Fun Stuff.11Kill all charts — text insights only▾
> "remove all charts, they occupy too much space and hardly ever render."
**Zero`<canvas>`or Chart.js elements.**Replace with stat cards and bulleted text insights. If it doesn't render reliably — kill it.12Agents + published pages → top section with a CTA▾
> "move Agents You've Built and My Share Pages to my main section at the top. Put a call to action to encourage people to try them."
Published agents and reports live in the about-me section with a clear CTA so visitors know to install and use them.13Zero-usage = 🌱 Getting Started, always consistent▾
> "people with zero usage, mark all as getting started with a consistent icon."
Any team member with 0 requests in 90 days gets exactly one label:**🌱 Getting started**. No ad-hoc icon variations.14Active leaderboards: default OPEN and placed HIGH▾
> "keep the active leaderboards as open and maybe move them further up on the report to gain prominence."
Leaderboard`<details>`MUST have the`open`attribute. Placed directly in the about-me wrapper — NOT inside a collapsed parent.15Page order: user #1 → team → drilldowns → fun stuff▾
Canonical page order: (1) about-me hero + AI Corner + leaderboards · (2) Team snapshot · (3) Agents & Skills · (4) Team Drilldown [open] · (5) Fun Stuff [collapsed].16Exact rank must appear in the hero section▾
> "state my rank up in the top section rather than saying it somewhere buried."
The hero must show the specific rank ("Rank #3 of 44 — org+"), not just a vague "Top 25%".17Show the gap to the next tier — motivate, don't just report▾
> "In my section put my status and what will get me to Power users to encourage me."
About-me section must include a "next tier" nudge — how many more requests to reach Power User — plus a positive acknowledgment of current standing.18No private or cross-org work shown on the report▾
> "No private access work can be shown on this report."
Only publicly accessible work appears. No private reports, no cross-org content, no unlisted pages.19All tables sorted by token count descending▾
> "order the tables by token usage not by reqs and mark status accordingly."
Every leaderboard and member table sorted by tokens descending, not requests. Rank indicators reflect that token-based sort order.20Agent inventory: data-driven from skills.json, always fresh▾
> "meeting-room-agent is also on marketplace. Always pull the fresh state when generating this report."
Marketplace skill cards are fully data-driven from a live JSON file refreshed on each rebuild. No hardcoding of marketplace status.
## Inferred Meta-Patterns
| Pattern | Evidence |
|---|---|
| "If it doesn't render, kill it" | Charts removed twice — org/lang chart, then all Chart.js. Applies to any UI element that breaks silently. |
| "Named peer comparisons feel uncomfortable" | Removed from peer benchmarks in three separate sessions. Aggregate benchmarks only. |
| "User's section = hero; everything else = supporting cast" | Same request phrased three separate ways across different sessions. |
| "If data is stale or noisy, trim it" | Inactive leaders removed; thin out senior-leader data. Don't show outdated or misleading numbers. |
| "Collapsed by default = low priority" | Fun Stuff, non-leaderboard drilldowns = collapsed. Only high-signal content is always-visible. |

## The Actual Lesson
Building an AI agent that generates recurring reports for real people requires more than prompting.
      It requires**governance**— explicit, versioned, sourced rules that an agent will honour
      even when the model changes, the data shifts, or someone new re-runs the script.
The 20 rules above weren't designed upfront — they were discovered through 73 iterations of building
      the actual product. The discipline is to capture them the moment they emerge, before they're forgotten.
      That's what makes the next build faster and the output consistent.