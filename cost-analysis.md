# 💸 Personal AI CLI Cost Analysis

How much would it cost to run an AI agent CLI setup personally — based on **actual measured 90-day usage**.

> 📅 Snapshot updated: May 2026
> 🧮 Pricing changes constantly — re-check provider sites before committing to a plan.

---

## 📊 Baseline: my actual 90-day usage

Pulled from a real telemetry-backed adoption tracker (live BigQuery numbers).

| Metric | Last 90 days | Per month (avg) |
|---|---|---|
| Model requests | 11,429 | ~3,810 |
| **Tokens consumed** | **1,000,000,000+** (1B+) | **~340M** |
| Code-completion requests | 5,479 | ~1,826 |
| Lines of code touched | 160,389 | ~53,463 |
| Distinct programming languages | 17 | — |
| Distinct models used | 5 | — |
| Tool-call success rate | 94% | — |

**~11M tokens/day, every day. The number speaks for itself.**

This sets the worst-case ceiling. Personal use will be a fraction (5–30%) of this — see scenarios below.

---

## 🧮 Pricing reference (per 1M tokens, blended 75% input / 25% output)

Blend ratio chosen to match agent workloads (lots of context input, smaller outputs).

### Anthropic Claude
| Model | Input $/1M | Output $/1M | Blended |
|---|---|---|---|
| Claude 3.5 Haiku | $0.80 | $4.00 | $1.60 |
| Claude 3.5 Sonnet | $3.00 | $15.00 | $6.00 |
| Claude Opus 4 | $15.00 | $75.00 | $30.00 |

### OpenAI GPT
| Model | Input $/1M | Output $/1M | Blended |
|---|---|---|---|
| GPT-5 nano | $0.05 | $0.40 | $0.13 |
| GPT-5 mini | $0.25 | $2.00 | $0.69 |
| GPT-5 | $1.25 | $10.00 | $3.44 |

### Google Gemini
| Model | Input $/1M | Output $/1M | Blended |
|---|---|---|---|
| Gemini 2.5 Flash | $0.30 | $2.50 | $0.85 |
| Gemini 2.5 Pro | $1.25 | $10.00 | $3.44 |

---

## 💰 Monthly cost if I replicated my full 340M-token volume on personal API

| Model | Monthly cost |
|---|---|
| Claude 3.5 Haiku | $544 |
| Claude 3.5 Sonnet | $2,040 |
| **Claude Opus 4** | **$10,200** 💀 |
| GPT-5 nano | $44 |
| GPT-5 mini | $235 |
| GPT-5 | $1,170 |
| Gemini 2.5 Flash | $289 |
| Gemini 2.5 Pro | $1,170 |

**Lesson:** raw API at this volume is brutal for top-tier models.

---

## 🎯 The smart move: subscriptions, not raw API

For heavy users, capped-but-generous subscriptions crush per-token API pricing.

| Plan | Monthly | What you get | Best for |
|---|---|---|---|
| Claude Pro | $20 | Web/desktop chat only, ~5x free limits | Light coding via web |
| **Claude Code Pro** | **$20** | CLI access, ~Sonnet 4 with hourly limits | Hobby coding |
| Claude Code Max 5x | $100 | ~5x Pro limits, includes Opus | Serious side projects |
| Claude Code Max 20x | $200 | ~20x Pro limits, heavy Opus | Replicate work-level use |
| Cursor Pro | $20 | 500 fast requests + IDE | If you like an IDE |
| GitHub Copilot Pro+ | $39 | Unlimited completions + agent mode | Code-completion focus |
| ChatGPT Plus | $20 | GPT-5, limited agent mode | General use |

---

## 🏠 Local (Ollama on Mac) — one-time hardware investment

| Tier | Cost | Capability |
|---|---|---|
| Mac Mini M4 32GB | ~$1,400 one-time | Llama 3.3 70B (slower than cloud) |
| Mac Studio M4 Max 64GB | ~$3,200 one-time | Qwen 72B / Llama 3.3 nicely |
| Mac Studio M3 Ultra 128GB | ~$5,500 one-time | Beast — 70B models fast |
| Electricity | ~$5–10/mo | — |

**Pros:** zero per-token cost, full privacy, no rate limits.
**Cons:** capability gap vs. frontier hosted models is real for complex multi-step agent work.

---

## 📈 Realistic personal usage scenarios

I won't actually use 340M tokens/month for hobby work. Here's what's likely:

| Scenario | Tokens/mo | Best fit | Monthly cost |
|---|---|---|---|
| **Light hobby** — recipe agent, occasional Qs | ~5M | Gemini 2.5 Flash API or free tier | **$0–5** |
| **Weekend coder** — 1–2 personal projects | ~25M | GPT-5 mini API OR Claude Code Pro | **$17–20** |
| **Active hacker** — multi-agent stack at home | ~75M | Claude Code Max 5x | **$100** |
| **Replicate work-level use** | ~340M | Claude Code Max 20x or Mac Studio | **$200/mo** OR one-time **$3,200** |
| **Open-source purist** | unlimited | Ollama + Mac Studio | **~$5/mo + $3,200 hardware** |

---

## 🐶 Recommendations (pick your path)

### ✅ Start here — **Claude Code Pro @ $20/mo**
- Same model family I'm already wired into
- CLI experience nearly identical to corporate setup
- Plenty for nights/weekends
- **Year 1 total: $240**

### ⏫ Upgrade if needed — **Claude Code Max 5x @ $100/mo**
- Handles serious personal projects without token-bill anxiety
- **Year 1 total: $1,200**

### 💡 Smart hybrid — **~$20–25/mo total**
- Claude Code Pro ($20/mo) for everyday coding
- Free Gemini AI Studio for big bulk tasks (1M tokens/day free tier)
- Local Ollama for privacy-sensitive stuff
- Best flexibility-to-cost ratio

### 🚫 Don't
- Pay raw API for Opus-class models = $6,800/mo to replicate full usage 💀
- Buy $5K hardware just for hosted-model preference — subscriptions are cheaper unless you have a strong privacy/offline requirement

---

## 🎓 Free / nearly-free fallbacks (always good to know)

| Provider | Free allowance | Catch |
|---|---|---|
| **Google AI Studio** | 1M tokens/day on Gemini 2.5 Flash | 15 RPM limit, data may train models |
| **Groq** | 14,400 requests/day | Limited model selection |
| **Together AI** | $5 free credit | Then pay-per-use (cheap) |
| **OpenRouter** | Free models available | Quality varies; rate-limited |
| **Ollama (local)** | Unlimited | Local hardware required |

For occasional personal use, free tiers may be entirely sufficient.

---

## 🔄 Revisit this analysis quarterly

Provider pricing drops fast (Gemini Flash is ~5x cheaper than 18 months ago, GPT-4 → GPT-5 dropped costs ~3x). Re-run the math every quarter.

### Pricing references
- https://www.anthropic.com/pricing
- https://openai.com/api/pricing
- https://ai.google.dev/pricing
- https://groq.com/pricing
- https://www.together.ai/pricing
- https://ollama.com (free, local)

### Tools to track personal API spend
- All providers have built-in usage dashboards in their consoles
- [LiteLLM](https://github.com/BerriAI/litellm) proxy gives unified usage tracking across providers
- [Helicone](https://www.helicone.ai/) for richer observability if you go heavy

---

🐶 *Generated alongside the sanitized agent stack. Update freely as your own usage evolves.*
