# sauravirai.github.io

🌐 **Live:** https://sauravirai.github.io

Personal portfolio site for **Sauravi Rai** — Global Product Leader · Walmart Inc. (eCommerce). 23 years across Walmart, Amazon, Microsoft, Nordstrom, and Oracle. Bengaluru-based, open to opportunities.

## Structure

| File / Directory | Purpose |
|---|---|
| `index.html` | Single-page landing site — About, What I Do, Career, Awards, Writing & Experiments, Contact |
| `resume.pdf` | Current résumé (May 2026) — linked from the homepage hero and the Writing section |
| `work/` | Nine deep-dive AI experiment pages — architecture blueprints, runtime portability analysis, deployment postmortems, dashboards, narrative stories. Indexed at `work/index.html`. |
| `design-patterns/` | Reference patterns for multi-agent system design and governance |
| `cost-analysis.md` | 90-day telemetry-backed breakdown of personal AI agent CLI costs across providers |
| `user-preferences-template.md` | Sanitized template of the agent assistant preferences file — fork for your own setup |

## Stack

- Single-page static site (`index.html`) + individual deep-dive pages under `work/`
- [Tailwind CSS](https://tailwindcss.com) via CDN
- Inter (Google Fonts)
- WCAG 2.2 Level AA — skip-to-content link, focus rings, semantic landmarks, color contrast checked
- No build step. No tracking. No external JS beyond Tailwind CDN.

## Local preview

```bash
python3 -m http.server 8000
# open http://localhost:8000
```

## Sanitization

All `work/` pieces and `user-preferences-template.md` were derived from real engagements and run through a multi-pass sanitizer:
- Colleague names → role placeholders (`a colleague`, `the EA`, etc.)
- Internal vendor/system names → genericized
- Personality assessments kept generic (no trait specifics)
- Zero placeholders, zero internal hostnames, zero PII verified

## License

Content © Sauravi Rai. Code (HTML/CSS structure) under MIT — fork if useful.

## Contact

- LinkedIn: [linkedin.com/in/sauravirai](https://www.linkedin.com/in/sauravirai/)
- Email: sauravi.rai@gmail.com
