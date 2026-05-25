# STREAMLINE RULES — team-ai-tools-report

**Owner:** see `config/owner.json` (gitignored — fill in your own identity)
**Last updated:** 2026-04-22
**Rules count:** 19
**Status:** Authoritative source of truth. Any agent rebuilding or editing index.html MUST honour these rules.

---

## The Golden Sentence

> [USER_NAME] first, team second, everything else collapsed. No charts (they don't render). No named peer embarrassment. Leaderboards open and high. Leader benchmarks in a collapsed section, not at the top. Fun stuff at the bottom. Keep it tight.

---

## Canonical Adoption Tiers ← single source of truth (overrides KEY FACTS system prompt)

All status chips, leaderboard ranks, and copy in the report MUST use these labels verbatim.
The KEY FACTS block in the system prompt lists `❌ None` for 0 requests — **that label is WRONG for display purposes. Rule 13 takes precedence: use 🌱 Getting started.**

| Tier | Threshold (90-day requests) | Display label | Display emoji |
|---|---|---|---|
| Power | ≥ 5,000 | Power user | 🔥 |
| Heavy | ≥ 500 | Heavy | ⚡ |
| Active | ≥ 100 | Active | 🟢 |
| Light | ≥ 10 | Light | 🌤 |
| Tried | 1 – 9 | Tried | 👋 |
| Getting started | 0 | Getting started | 🌱 |

**Code implementations (keep in sync — same logic, two locations):**
- `src/sections.py` → `status_chip(p)` — used in all leaderboard/team tables
- `src/me_section.py` → `_status_label(r)` — used in [USER_NAME]'s hero card only

Both must evaluate in threshold-descending order so higher tiers are matched first.
Neither may use `❌` or the label `None` for zero-request members.

---

## The 20 Rules (verbatim from command history, distilled)

**Rule 1 — Strip inactive leaders; thin out [SENIOR_LEADER] data**
> "remove Adoption by level from the whole report. remove inactive leaders from report. [SENIOR_LEADER] only put as inspirational note, but not the full data. remove inactive [SENIOR_LEADER]. put [COLLEAGUE] and team as Ex- under local My team section."
- **Interpretation:** Only active leaders in always-visible sections. [SENIOR_LEADER]-level peers = inspirational note only, not a full leaderboard.
- **Source:** command_history.txt L2242 · 2026-04-17 23:53

**Rule 2 — Focus = [USER_NAME] and her team. Rest takes a back seat**
> "focus the insights around me and my team. the rest can occupy less space. Don't say anything that may be hurtful to folks not adopting the tools as fast, retain suggestions to encourage traction."
- **Interpretation:** [USER_NAME]'s stats and direct team are primary. Broader org data is secondary and space-efficient. Never shame non-adopters.
- **Source:** command_history.txt L2312 · 2026-04-18

**Rule 3 — Standardise labels; scrub redundant icons**
> "Standardize on the labels you use on the report. Scrub the icons and redundant section names."
- **Interpretation:** Every section must have consistent naming. No duplicate icons, no inconsistent header styles.
- **Source:** command_history.txt L2627 · 2026-04-18 12:16

**Rule 4 — Leader Benchmarks OUT of always-visible; collapsed only**
> "removed leader benchmarks from the top section. combine all my team leads in one group whether functional or local. just lump a) Team drilldown b) Leader benchmarks."
- **Interpretation:** Leadership benchmark data ([SENIOR_LEADER], [OFFICE_LOCATION] peers) must live in a collapsed `<details>` block. Only the active leaderboard tables are always-visible.
- **Source:** command_history.txt L2681 · 2026-04-18 12:33

**Rule 5 — No named peer comparisons; aggregate insight only**
> "remove Benchmark vs [SENIOR_LEADER] peers — [COLLEAGUE] & [VP_LEADER] (click to expand) and instead give insights how I am performing against D+ associates across [SENIOR_LEADER] and [OFFICE_LOCATION] D+ PM org (under [PEER_LEAD]) but label it that way."
- **Interpretation:** Never call out individual peers by name in comparison framing. Use aggregate-level insights: "Top 25% of [SENIOR_LEADER]+ org" is fine; "[COLLEAGUE] Schechter — 419M tokens" as a direct comparison is not.
- **Source:** command_history.txt L2711 · 2026-04-18 12:48

**Rule 6 — Remove Team Recommendations as standalone section; merge into drilldown**
> "remove the section on Team Recommendations and within Team Drilldown, just make the insights and recommendations the first section."
- **Interpretation:** No standalone "Recommendations" section. Recommendations live inside Team Drilldown as the FIRST sub-section.
- **Source:** command_history.txt L2735 · 2026-04-18 13:03

**Rule 7 — Top hero = tool-agnostic; no PM/DA split at hero level**
> "first section isn't catchy — rework the overall Team AI usage snapshot, it's as much about which tools we are using than how much usage. Also no need to divide by functional and local or by PM and DA at the top hero metrics."
- **Interpretation:** The top-of-page stat strip should show unified numbers only. Don't split by role (PM/DA) or org type (functional/local) at the hero level — those go in drilldowns.
- **Source:** command_history.txt L2781 · 2026-04-18

**Rule 8 — No repetition; merge "What your team is building" into Full Team**
> "annoying repetitions. e.g. What your team is building with AI is unnecessary, just merge in with Full team and take the insights and recommendations outside of the drilldown."
- **Interpretation:** Zero duplicate section headings or content. "What your team is building" label is retired. Content folds into the Team section.
- **Source:** command_history.txt L2793 · 2026-04-18

**Rule 9 — Pro Tips → merge into Fun Stuff at the BOTTOM**
> "take out Pro Tips — across all tools combine with Fun Stuff and put right at the bottom of the report as its own section."
- **Interpretation:** Any "tips", "how to", or "fun facts" content belongs at the very bottom in the Fun Stuff section. Not mid-report.
- **Source:** command_history.txt L2823 · 2026-04-18

**Rule 10 — Team Drilldown: default OPEN. Fun Stuff: default COLLAPSED**
> "Team drilldown keep expanded as default. Fun Stuff keep collapsed by default."
- **Interpretation:** `<details open>` on Team Drilldown. `<details>` (no `open`) on Fun Stuff.
- **Source:** command_history.txt L2841 · 2026-04-18

**Rule 11 — Kill all charts. They don't render. Show insights as text only**
> "remove all charts, they occupy too much space and hardly ever render."
- **Interpretation:** Zero `<canvas>` or Chart.js elements in this report. Replace with stat cards and bulleted text insights.
- **Source:** command_history.txt L3547 · 2026-04-19 05:20

**Rule 12 — Agents + Share Puppy pages → top section with CTA**
> "Summarize and move Agents You've Built — Not Yet Published and My Share Puppy Pages to my main section at the top. Put a call to action to encourage people to try them."
- **Interpretation:** [USER_NAME]'s published agents and share-agent reports live in the about-me section. Must include a clear CTA ("Want to try these? …") so visitors know to install and use them.
- **Source:** command_history.txt L3547 · 2026-04-19 05:20

**Rule 13 — Zero-usage = 🌱 Getting Started. Consistent icon always**
> "people with zero usage, mark all as getting started with a consistent icon."
- **Interpretation:** Any team member with 0 requests in 90 days gets exactly one label: `🌱 Getting started`. No ad-hoc icon variations.
- **Source:** command_history.txt L3788 · 2026-04-19 08:09

**Rule 14 — Active leaderboards: default OPEN and placed HIGH for prominence**
> "keep the active leaderboards as open and maybe move them further up on the report to gain prominence."
- **Interpretation:** The `<details>` wrapper around the leaderboard tables MUST have the `open` attribute. The leaderboard sections sit directly in the about-me wrapper, NOT inside a collapsed parent. They are visible on page load.
- **Source:** command_history.txt L2546 + autosave session 20260417_200152 msg84 · 2026-04-17 20:47

**Rule 15 — [USER_NAME]'s section is #1. Team follows. Non-leaderboard drilldowns collapsed**
> "Create a top section just about me, then followed by the Team metrics. Keep the non-important drilldowns collapsed by default and focus mostly on me and my reportees. Default collapse all charts, drilldowns except the leaderboard."
- **Interpretation:** Page order: (1) about-me hero + AI Corner + active leaderboards (2) Team snapshot (3) Agents & Skills (4) Team Drilldown [open] (5) Fun Stuff [collapsed].
- **Source:** command_history.txt L2558+L2613 · 2026-04-17

**Rule 16 — [USER_NAME]'s exact rank must appear in the hero section**
> "state my rank up in the top section rather than saying [it somewhere buried]."
- **Interpretation:** The badge block in the about-me hero must include the specific number: "Rank #3 of 44 — [SENIOR_LEADER]+ org" (or equivalent current data). Not just "Top 25%" which is too vague.
- **Source:** command_history.txt L3871 · 2026-04-19

**Rule 17 — In [USER_NAME]'s section: motivate toward Power User tier. Show the gap**
> "In my section put my status and what will get me to Power users to encourage me. Also appreciate my standing across the D+ group."
- **Interpretation:** The about-me section must include a "next tier" nudge — how many more requests/tokens to reach the next adoption tier, and a positive acknowledgement of current D+ standing.
- **Source:** command_history.txt L2823 · 2026-04-18

**Rule 18 — No private or cross-org work shown on this report**
> "No private access work can be shown on this report."
- **Interpretation:** The `_puppy_work_block` and any other section of this report must ONLY show work that is publicly accessible to all ExampleCorp associates. This includes:
  - ❌ Reports built for other orgs (e.g. [VP_LEADER]-team-ai-tools-report) — internal work product
  - ❌ Private/unlisted share-agent pages
  - ❌ Agents or skills marked private that aren't accessible to the viewer
  - ✅ Published marketplace skills (public)
  - ✅ Share-agent pages with Business access (visible to all ExampleCorp associates)
  - ✅ Public decks and guides already linked openly
- **Applies to:** `_puppy_work_block()`, `_skills_block()`, any future "My Work" sections.
- **Source:** [USER_NAME] instruction · 2026-04-21

**Rule 19 — All tables sorted by token count (descending); ranks and status reflect token order**
> "order the tables by token usage not by reqs and mark status accordingly."
- **Interpretation:** Every leaderboard or member table in the report — team drilldown, local-leadership-net, leadership-net, [OFFICE_LOCATION] benchmark, peers — must be sorted by `tokens` descending, not by `modelRequests`. Any rank indicator (e.g. #1, #2, #3) and adoption-tier emoji (🔥 ⚡ 🟢 🌤 👋 ❌) displayed in those tables must be consistent with that token-based sort order. The tier thresholds in KEY FACTS remain request-based (as defined), but the displayed row order and any positional rank labels use tokens.
- **Applies to:** All `<table>` and `<ul>` leaderboard blocks in `build.py` and `index.html`.
- **Source:** [USER_NAME] instruction · 2026-04-22

**Rule 20 — Agent inventory: data-driven from skills.json; always pull fresh state**
> "meeting-room-agent is also on marketplace. Always pull the fresh state when generating this report and keep consistent."
- **Interpretation:** Marketplace skill cards are **fully data-driven from `static/data/skills.json`**. The file is refreshed by `src/fetch_skills.py` (step 8 of full rebuild). Badges and stats derive automatically from the file — no hardcoding of marketplace status in `me_section.py`.
- **Badge types — two active ones:**
  - `PUBLIC ✓` — skill is in skills.json with `skillStates: ["APPROVED"]` — on the marketplace
  - `PRIVATE 🔒` — internal only; hardcoded (private agents have no marketplace API)
  - ~~SHARED 🔗~~ — **retired**: a skill is either on the marketplace (PUBLIC) or private
- **Authoritative agent inventory (source of truth = skills.json + fetch_skills.py):**

  | Agent / Skill | Badge | On Marketplace? | Source |
  |---|---|---|---|
  | `meeting-room-agent` | PUBLIC ✓ | **Yes** | skills.json (data-driven) |
  | `storyteller` | PUBLIC ✓ | **Yes** | skills.json (manually seeded; fetch_skills.py keeps fresh) |
  | `ai-usage-tracker` | PRIVATE 🔒 | No | Hardcoded — private agents have no marketplace API |

- **How to keep fresh:** `src/fetch_skills.py` runs automatically in full rebuild. If marketplace API returns 401 (no session token), existing skills.json is preserved and build continues. To unlock: `export PUPPY_SESSION_COOKIE='...'` then re-run.
- **Stats strip — three labels only:**
  - **Agents & Skills** = total (`len(my_skills)` + private count)
  - **On Marketplace** = `len(my_skills)` — from skills.json author match, always current
  - **Private** = hardcoded count of private-only agents (currently 1)
  - ~~Deployed~~ — **banned**: ambiguous, meaningless
- **CTA must list all marketplace skills by name** so the team can find and install them.
- **Source:** [USER_NAME] instruction · 2026-04-22

---

## Inferred patterns

| Pattern | Evidence |
|---|---|
| **"If it doesn't render, kill it"** | Charts removed twice — org/lang chart in insights.py, all Chart.js Apr 19. Applies to any UI element that breaks silently. |
| **"Named peer comparisons feel uncomfortable"** | [COLLEAGUE] & [VP_LEADER] removed from [SENIOR_LEADER]-peers; [PEER_LEAD] reference removed; "nothing hurtful" constraint. Aggregate benchmarks only. |
| **"[USER_NAME]'s section = hero; everything else = supporting cast"** | Same request phrased three separate ways across different sessions. |
| **"If data is stale or noisy, trim it"** | Inactive leaders removed; [SENIOR_LEADER] thinned; [COLLEAGUE] moved to Ex-team. Don't show outdated or misleading numbers. |
| **"Collapsed by default = low priority"** | Fun Stuff, non-leaderboard drilldowns = collapsed. Only high-signal content is always-visible. |
| **"Sections at the bottom = fun/optional"** | Fun Stuff + Pro Tips explicitly sent to bottom in two separate commands. |

---

## Application checklist for any future edit

- [ ] [USER_NAME]'s "about me" section is the FIRST visible section
- [ ] [USER_NAME]'s rank (`Rank #3 of 44 — [SENIOR_LEADER]+ org`) appears in the about-me hero badges, not just the leaderboard
- [ ] Active leaderboards (`leadership-net`, `local-leadership-net`) have `<details open>` and are directly in the about-me wrapper — NOT inside a collapsed parent
- [ ] Skip-level peer data ([SENIOR_LEADER] / [EXEC_LEADER]'s org) is in its own collapsed `<details>` — never always-visible
- [ ] Leader benchmark data does NOT appear above the fold at the top of the page
- [ ] Team Drilldown `<details open>` — expanded by default
- [ ] Fun Stuff `<details>` (no `open`) — collapsed, at the bottom
- [ ] No `<canvas>` or Chart.js — text insights only
- [ ] No named peer comparisons ([COLLEAGUE], [VP_LEADER], [PEER_LEAD] individual callouts removed from benchmark context)
- [ ] Inactive members (0 requests) → `🌱 Getting started` chip — consistent icon
- [ ] [USER_NAME]'s AI Corner showcase has a CTA inviting team members to try the published agents
- [ ] No repetitive section labels ("What your team is building" → merged into Team section)
- [ ] No standalone "Recommendations" section — it's the first sub-section inside Team Drilldown
- [ ] Pro Tips merged into Fun Stuff at the bottom
- [ ] All leaderboard / member tables sorted by **tokens descending** (not requests); rank labels (#1, #2 …) and adoption-tier emojis reflect that order
- [ ] Zero-request members display as `🌱 Getting started` — never `❌ None`
- [ ] `status_chip` (sections.py) and `_status_label` (me_section.py) are kept in sync with the canonical tier table above
- [ ] All marketplace skill cards use `PUBLIC ✓`; only private agents use `PRIVATE 🔒`; `SHARED 🔗` is retired — Rule 20
- [ ] Stats: **On Marketplace** = `len(my_skills)` (data-driven from skills.json); **Private** = hardcoded count — Rule 20
- [ ] CTA lists all marketplace skills by name (`storyteller`, `meeting-room-agent`) — Rule 20
- [ ] `fetch_skills.py` is step 8 in the full rebuild sequence — Rule 20

---

## Where this is referenced

- `{workspace}/published-pages.json` → `team-ai-tools-report.streamline_rules_doc` points here
- `~/.agentrunner/agents/ai-usage-tracker.json` → `system_prompt` contains a `## STREAMLINE RULES` block pointing here
- **Canonical git history:** all 17 rules sourced verbatim from `~/.agentrunner/command_history.txt` (lines 2242–4782) and `autosave/auto_session_20260417_200152.pkl` msg 84.

---

*Generated by PersonalAgent · code-agent-726168 · 2026-04-19 · Never re-discover these again!* 🐾
