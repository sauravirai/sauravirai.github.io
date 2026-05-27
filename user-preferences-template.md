# [USER_NAME]'s AI agent CLI Preferences 🐾

> **Future AI agent CLI: read this first at session start!**
> Last updated: 2026-05-05

## 🏠 Default Workspace
**ALL new project work goes under `/Users/USER_ID/workspace/`**

- Never create projects in `~` (home root) — warn and redirect to `~/workspace/<name>/`
- `cd ~/workspace/<project>` BEFORE running file ops, git, or `uv venv`
- New projects: `~/workspace/<kebab-case-name>/` + `git init` + `.gitignore`

## 📦 Existing Projects (don't blow away)
| Path | Purpose |
|---|---|
| `~/workspace/avatars/` | Avatar assets |
| `~/workspace/[VP_LEADER]-team-report/` | [VP_LEADER] team report |
| `~/workspace/code-agent-team-report/` | AI agent CLI adoption report |
| `~/workspace/meeting-room-bridge/` | Meeting room bridge |
| `~/workspace/meeting-room-copilot-studio/` | Copilot Studio meeting agent |
| `~/workspace/org-context-agent/` | Org change agent + ground truth |
| `~/workspace/[USER_NAME]-agent-stack/` | Published agent stack mono-repo |

## 🚫 Hands Off
- `~/.agent-runner-venv/` (install dir — auto-updated)
- `~/.agentrunner/agents/*.json` (custom agent configs — only edit when explicitly asked)
- `~/.agentrunner/agentrunner.cfg` (only edit `default_workspace` line if user asks)

## 🛠️ Stack Defaults
- Python: `uv venv` + `--index-url https://pypi.example.com/internal/simple --allow-insecure-host pypi.ci.internal.example.com`
- Default web stack: FastAPI + HTMX + Tailwind + SQLite
- Frontend: WCAG 2.2 AA, ExampleCorp colors (blue.100=#0053e2 primary, spark.100=#ffc220 accent)
- Reports: flat HTML + HTMX + Tailwind + Chart.js, daily/monthly/quarterly + exec insights top & bottom

## 🗂️ Custom Agent Locations
- Local agents folder: `~/.agentrunner/agents/`
- [USER_NAME]'s custom agents: `ai-usage-tracker`, `meeting-room-agent`, `[USER_NAME]-org-context-agent`, `stack-shepherd`, `storyteller`, `daily-task-agent`
