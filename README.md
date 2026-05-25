# sauravirai.github.io

🌐 **Live site:** https://sauravirai.github.io _(GitHub Pages — will go live when repo is made public, or you can deploy via Vercel/Cloudflare with the repo private)_

Personal portfolio for **Sauravi Rai** — Senior Director, Product Management. 23 years across Walmart, Amazon, Microsoft, Nordstrom, and Oracle. Bengaluru-based, open to opportunities.

## What's here

- **`index.html`** — single-page landing site: About, Selected Impact, Experience, How I Lead, AI Experiments, More Writing & Repos, Contact
- **`work/`** — nine deep-dive AI experiment pieces (sanitized, name-attributed)
  - architecture blueprints, runtime analysis, deployment postmortems, dashboards, narrative stories
- **`resume.pdf`** — drop-in résumé, linked from the landing page

## Stack

- Single-page static site (`index.html`) + individual deep-dive pages under `work/`
- [Tailwind CSS](https://tailwindcss.com) (via CDN)
- Inter / Inter Tight (Google Fonts)
- Chart.js for the dashboards
- WCAG 2.2 Level AA — skip-to-content, focus rings, semantic landmarks, alt text

## Hosting options

| Path | Cost | Privacy |
|---|---|---|
| GitHub Pages (public repo) | Free | Repo + history public |
| GitHub Pro + Pages (private repo) | $4/mo | URL public, repo private |
| Vercel free | Free | Repo private, URL shareable |
| Cloudflare Pages + Access | Free | Repo private, restrict viewers by email |

## Local preview

```bash
python3 -m http.server 8000
# open http://localhost:8000
```

## Sanitization

All `work/` pieces were derived from real engagements and run through a multi-pass sanitizer:
- Colleague names → role placeholders (`a colleague`, `the EA`, etc.)
- Internal vendor/system names → genericized (`the travel booking system`, etc.)
- Personality assessments → kept generic (`Hogan scale` without trait specifics)
- Verified zero placeholders, zero internal hostnames, zero PII

## License

Content © Sauravi Rai. Code under MIT — fork the structure if it's useful to you.
