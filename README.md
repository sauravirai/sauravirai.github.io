# sauravirai.github.io

🌐 **Live:** https://sauravirai.github.io

Personal portfolio for **Sauravi Rai** — product leader, 23 years across Walmart, Amazon, Microsoft, Nordstrom, Oracle. Building AI agents and evals frameworks.

- LinkedIn: [linkedin.com/in/sauravirai](https://www.linkedin.com/in/sauravirai/)
- Email: sauravi.rai@gmail.com

---

## Contents

| File | What it is |
|------|-----------|
| [index.html](index.html) | Portfolio homepage (live site) |
| [work/keel.html](work/keel.html) | Keel — an anonymous team-diagnostic tool built end to end and handed over: privacy by architecture, tests, clean transfer |
| [music-super-agent.html](music-super-agent.html) | MusicSuperAgent → Keepsake Studio — AI music-video pipeline, 28-day data, the pivot to a private self-serve tool; includes [overview deck](assets/keepsake-studio-overview.pdf) and walkthrough video |
| [cost-analysis.html](cost-analysis.html) | Real 90-day telemetry: what it costs to run an enterprise-grade AI agent stack personally |
| [work/](work/) | AI work: Keel case, virtual EA, digital twin, agent stack story |
| [design-patterns/](design-patterns/) | Multi-agent orchestration, governance, and composition patterns |
| [resume.pdf](resume.pdf) | Current résumé |

---

## Site

Static, self-contained HTML pages (`index.html` + one styled page per project/pattern). No framework, no build step, no tracking. Media lives in `assets/`.

```bash
python3 -m http.server 8000   # local preview
```

## Sanitization

All `work/`, `design-patterns/` and project pieces were derived from real engagements and sanitized:
- Colleague names → role placeholders
- Internal system/vendor names → genericized
- No PII, no internal hostnames, no placeholders

## Archive

Older or less central pieces were retired from the site in Oct 2026 and are kept privately; they remain in this repo's git history.
