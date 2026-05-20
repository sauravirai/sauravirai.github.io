# 🎨 Portfolio Pieces

Nine self-contained HTML artifacts, sanitized for public viewing. Each demonstrates a different facet of building AI agents in production — from architecture blueprints to engineering postmortems to live dashboards to practical how-to guides.

> All corporate identifiers, real names, internal hostnames, and product codes have been scrubbed. Safe for public sharing.

---

## 📁 What's in here

### 🌟 Architecture & Strategy

| File | Size | What it shows |
|---|---|---|
| [`digital-twin-blueprint.html`](./digital-twin-blueprint.html) | 124 KB | **The flagship.** Three-tier digital-twin agent architecture: 6 domain agents, 11+ capabilities, 6 implementation phases, memory & identity model, "twin earns autonomy" framing |
| [`agent-runtime-portability.html`](./agent-runtime-portability.html) | 21 KB | Scorecard analysis of 6 agents evaluating whether each should be ported from Runtime A → Runtime B. Includes a reusable decision framework |
| [`agent-stack-journey-story.html`](./agent-stack-journey-story.html) | 29 KB | The "why" behind building a personal multi-agent stack, with progress over time |

### 🛠️ Engineering Practice

| File | Size | What it shows |
|---|---|---|
| [`copilot-studio-postmortem.html`](./copilot-studio-postmortem.html) | 50 KB | Engineering postmortem: platform pivot, DLP wrangling, debugging a sneaky `operationId` typo, honest writeup of abandoned plans |
| [`scheduling-llm-agents-guide.html`](./scheduling-llm-agents-guide.html) | 17 KB | Practical how-to: scheduling LLM agents to run automatically (cloud CI/CD + macOS `launchd`), including the IST↔UTC cron cheat sheet |
| [`first-agent-with-video.html`](./first-agent-with-video.html) | 137 KB + 12 MB video | "My first agent" walkthrough with embedded HeyGen avatar. Includes the **X-Frame-Options workaround** (inline `<video>` instead of `<iframe>`) |

### 📊 Dashboards & Storytelling

| File | Size | What it shows |
|---|---|---|
| [`ai-tools-adoption-dashboard.html`](./ai-tools-adoption-dashboard.html) | 177 KB | **Team AI-tools adoption tracker dashboard.** Live methodology for measuring per-tool usage across a team, with leaderboards, trend lines, and per-person breakdowns. Heavily-iterated (v73 in the original) |
| [`personal-agent-stack-dashboard.html`](./personal-agent-stack-dashboard.html) | 22 KB | Personal multi-agent stack status dashboard — visualizes which agents exist, their maturity, and how they compose |
| [`virtual-ea-story.html`](./virtual-ea-story.html) | 45 KB | End-to-end story of building a Virtual EA agent — problem → architecture → outcome |

---

## 🎯 Which one should you look at first?

| If you're a... | Start with... |
|---|---|
| Hiring manager assessing system design | **`digital-twin-blueprint.html`** |
| Engineer who wants to see real debugging | **`copilot-studio-postmortem.html`** |
| Manager curious about team AI adoption | **`ai-tools-adoption-dashboard.html`** |
| Builder evaluating agent runtimes | **`agent-runtime-portability.html`** |
| Someone trying to schedule their own agents | **`scheduling-llm-agents-guide.html`** |
| Product person who wants a narrative | **`virtual-ea-story.html`** |

---

## 🖼️ Viewing the files

Each HTML file is **fully self-contained** (or self-contained + `assets/` neighbor). Just open in any browser:

```bash
# Mac — open any file
open portfolio/digital-twin-blueprint.html
open portfolio/ai-tools-adoption-dashboard.html

# Or serve the whole folder with a simple local web server:
cd portfolio
python3 -m http.server 8000
# Then visit http://localhost:8000
```

---

## 🛠️ How these were sanitized

Each piece went through:
1. **Asset extraction** — inline base64 video/images pulled out into `assets/` and replaced with `<video src="...">` / `<img src="...">` references (HTML stayed small, GitHub-diffable)
2. **Pattern-based scrubbing** — using `../_sanitizer-script.py` plus piece-specific extra patterns for:
   - Real names (replaced with role placeholders like `[COLLEAGUE]`, `[SENIOR_LEADER]`)
   - Corporate emails (replaced with `[EMAIL_REDACTED]`)
   - Phone numbers, LinkedIn URLs, user IDs
   - Internal vendor/system names (travel-desk vendors, HRIS, expense systems, etc. → role placeholders)
   - Internal CI/CD platform names → `[CI_PLATFORM]`, `[CLOUD_PLATFORM]`
   - Personal psychometric scores (abstracted to `[PERSONALITY_TRAIT]`)
3. **Multi-pass leak verification** — automated regex scan across 7 categories of leaks; zero hits in any of the 9 final files
4. **Total substitutions applied**: **~550 across 9 files**

---

## 📤 Optional: publish as a GitHub Pages site

Since these are all self-contained HTML, host publicly with zero build step:

```
Settings → Pages → Source: main branch / portfolio folder
```

Then they're live at:
```
https://sauravirai.github.io/ai-experiments/portfolio/<filename>
```

(Requires the repo to be public, or GitHub Pro for private-repo Pages.)

---

## 🚫 What's NOT included (and why)

From the larger pool of internal share-pages and local artifacts:
- **Daily/weekly team status updates** — too internal, not generalizable
- **Working drafts and planning scratchpads** — half-baked thinking
- **HeyGen script packs** — personal-brand content, not technical work
- **Org-change methodology page** — contains 15+ real colleague names, work-authorization references, internal HR system details; would need a semantic rewrite (not just regex sanitization) to be safe. *Deferred.*

---

🐶 *Curated and sanitized by Code Puppy on 2026-05-18.*
