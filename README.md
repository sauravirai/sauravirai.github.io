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
| [music-super-agent.md](music-super-agent.md) | AI music pipeline — concept, week-1 results, open questions |
| [ai-pm-learning-path.md](ai-pm-learning-path.md) | 12-week plan to close the technical depth gap for frontier AI roles |
| [cost-analysis.md](cost-analysis.md) | Real 90-day telemetry: what it costs to run an enterprise-grade AI agent stack personally |
| [work/](work/) | AI experiment write-ups: virtual EA, digital twin, agent stack story |
| [design-patterns/](design-patterns/) | Multi-agent orchestration, governance, and composition patterns |
| [resume.pdf](resume.pdf) | Current résumé |

---

## Site

Static HTML (`index.html`) + Markdown content files. Tailwind CSS via CDN. WCAG 2.2 AA. No tracking. No build step.

```bash
python3 -m http.server 8000   # local preview
```

## Sanitization

All `work/` and `design-patterns/` pieces were derived from real engagements and sanitized:
- Colleague names → role placeholders
- Internal system/vendor names → genericized
- No PII, no internal hostnames, no placeholders
