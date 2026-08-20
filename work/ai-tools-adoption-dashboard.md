📋
**Methodology demo with synthetic data.**Real names, titles, reporting lines, and per-person usage numbers from the original
        live dashboard (which tracked many colleagues across 6 AI tools) have been replaced
        with fictional placeholders. The layout, charts, sections, and methodology shown
        here mirror the production dashboard exactly.
AI Tools Adoption Tracker
# 🐶 Team AI Tools Report
Team snapshot · 90-day window · ~80 contributors · 6 AI tools tracked📅 Refreshed daily🤖 Auto-published via scheduled agent🔁 v73 (heavily iterated)
## Top-line metrics
People tracked
~80
across 4 org depths
Active users (90d)
62
78% adoption
Tokens consumed
4.2B
across all models
Tools tracked
6
CLI + IDE + chat
### Model mix (by tokens)
Distribution across the LLMs the team uses
### Active users by week
Weekly unique users over 12 weeks
## Group breakdowns
The live dashboard renders one leaderboard per group. The original tracked 7 groups; one sample shown below.MeSenior Leader+ NetworkOffice PM BenchmarkSenior Leader GroupTeamFull TeamLicensed AI Tools Coverage
| Depth | Person | Role (placeholder) | Reports to | Requests ↓ | Tokens | Status | Streak · Rank |
|---|---|---|---|---|---|---|---|
| d2 | [Person A] | [Senior Director] | via [Manager X] | 10,977 | 813.96M | Power user | 🔥 12w · #1 |
| d2 | [You] | [Your Role] | via [Your Manager] | 11,441 | 1,024.5M | Power user | 🔥 12w · #1 |
| d2 | [Person B] | [Senior Director, Product] | via [Manager X] | 10,099 | 516.56M | Power user | 🔥 11w · #3 |
| d3 | [Person C] | [Director, Product] | via [Person B] | 6,228 | 348.50M | Steady | 🔥 8w · #7 |
| d3 | [Person D] | [Eng Manager] | via [Manager Y] | 1,876 | 112.30M | Steady | 🔥 4w · #18 |
| d4 | [Person E] | [Senior PM] | via [Person C] | 412 | 24.80M | Light | — · #44 |
| d4 | [Person F] | a PM | via [Person C] | 0 | 0 | Inactive | — |

💡 The original live table had ~80 rows across 4 reporting depths (d1–d4), grouped into the 7 tabs above.
## Licensed AI Tools Coverage
Tracks which licensed AI tools each person has activated and is actively using.
| Tool | Type | Licensed | Active 90d | Adoption |
|---|---|---|---|---|
| [AI CLI Tool A] | Terminal coding agent | 80 | 62 | 78% |
| [IDE Copilot] | IDE code completion | 80 | 71 | 89% |
| [Chat Assistant B] | Browser chat | 80 | 58 | 73% |
| [Enterprise LLM Gateway] | API + chat | 80 | 34 | 43% |
| [Agent Builder Studio] | Low-code agents | 80 | 11 | 14% |
| [Voice Avatar Tool] | Avatar video | 80 | 5 | 6% |

## 🛠️ Methodology
- **Data sources.**Per-tool usage APIs (request counts, token counts, model names) + org reporting graph from the company directory.
- **Roll-up.**Each person's raw usage joined with their reporting depth (d1–d4 below me) and their direct manager.
- **Grouping.**Renders 7 tabs (Me / Senior Leader+ Network / Office PM Benchmark / Senior Leader Group / Team / Full Team / Licensed Tools Coverage), each a filtered leaderboard.
- **Status buckets.**Power user / Steady / Light / Inactive — based on weekly request count thresholds.
- **Streaks.**Consecutive weeks of activity, surfaced as a 🔥 badge to drive friendly competition.
- **Publishing.**A scheduled agent regenerates this HTML daily, drops it into a shared location, and pings the team channel on material rank changes.**Why it works**
Visibility + light gamification surface the natural champions, who then mentor lighter users. Adoption rose from ~40% to ~78% over the iteration cycle.**What I'd change**
Add per-tool quality signals (not just volume) — high-token, low-value usage shouldn't beat high-leverage agent runs.