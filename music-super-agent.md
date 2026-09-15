# MusicSuperAgent

**Sauravi Rai · September 2026 · In active product discovery**

An AI pipeline that turns a song idea into a published, produced video in under an hour — built to test one specific hypothesis: that preserving a loved one's voice as a musical keepsake is a real product, not just a novelty of generative AI.

---

## The hypothesis

Most AI-music tools compete on generation quality — better prompts, better voices, faster iteration. That's a commodity race, and not the question this project set out to answer.

The actual question was narrower and harder to answer from a desk: who is this really for, and what would make them pay? Twelve videos, a friends-and-family survey, and a read of how people actually reacted — not how they said they'd react — were the instruments used to find out, not a conclusion assumed going in.

The findings below are what that process surfaced.

---

## What was built

An end-to-end pipeline, not a demo:

```
Song idea → AI audio generation → cover art → animated video
          → title/description/tags → YouTube publish
                        ↑
          One human checkpoint: sync approval before final render
```

- **Audio & voice**: AI music generation, including father's-voice recreation from home-video audio extraction
- **Video**: FFmpeg pipeline — Ken Burns motion, a generated waveform visualization, standardized artist branding, burned-in lyrics
- **Metadata & distribution**: automated YouTube title/description/tag generation and upload; cross-posted to Instagram
- **Cost-conscious by design**: lyric polishing routes to a small, cheap model (Claude Haiku) rather than a frontier model — this isn't a task that needs one. Per-video cost: **$0.02–0.69** depending on whether cover art comes free from the audio platform or needs a separate image-generation pass. All-in monthly cost at a 12-video/month pace: **~$145**, dominated by subscriptions, not usage.

## What the data said

12 videos in the first week; by the 28-day mark: **6,089 YouTube views**, 33 subscribers (from 3), ~1,250 unique viewers, 86% of traffic algorithm-delivered (Browse + Suggested) rather than search or shares.

Two findings mattered more than the headline numbers:

**Reach is borrowed, not earned.** The best-performing video by impressions — a cover of a well-known 1965 classic — pulled 45,307 impressions. An original composition, with a *better* engagement profile (27.7% first-day click-through, 99% average viewed — both far stronger than any cover), got roughly 300 lifetime views. The algorithm amplifies videos tied to already-searched songs; it doesn't amplify quality it can't route through an existing search pool. That's a hard ceiling on using YouTube discovery to validate an *original*-content product — the channel is a poor test bed for the thing actually being tested.

**There are two distinct audiences, and they want different things.** A reach audience (18–34, male-skewed, arrives via algorithm, watches partially, drawn to recognizable covers) and an engagement audience (35–54, women over-index heavily on watch time — this group is 14% of views but nearly 39% of total watch hours — NRI-inclusive, watches father's-voice content end-to-end). The second group looks like the actual buyer for a keepsake product. The first group is just reach.

Production spend didn't move either number: a Runway-produced cinematic cut of one video underperformed its plain sibling.

## The pivot

Twelve more videos wouldn't have resolved either finding — more content sharpens a distribution question, not a demand question. So the project paused shipping and started testing willingness-to-pay and required hand-holding directly: a short survey to friends and family, a structured read of informal reactions (WhatsApp, Instagram) bucketed by signal strength, and — the actual missing experiment — a small paid concierge run with real families.

One early, unprompted signal from that process: people didn't just want the *finished* thing — several said they'd want to try making one themselves, not have it made for them. That reframed the open question from "would you pay for this" to "do you want a service, a tool, or both."

## Legacy Edition — the current prototype

A guided intake experience — built to test that exact question. A visitor works through who the song is for, what they'd want to keep, and critically, whether they want it made for them or want to shape it themselves. It's deliberately not "self-service AI generation at scale" yet — no public music-generation API exists to build that safely on today — it's a structured brief that starts a real, produced project, dressed as a product rather than a form.

*Currently being tested one real person at a time before a public link goes up here.*

## Open, honestly

This is mid-discovery, not a finished case study:

- Willingness-to-pay is still unvalidated beyond a single-digit signal count
- Which specific use case resonates most is still an open read, not a settled conclusion
- Product shape — tool, service, or some mix — is still unresolved
- No public API exists yet for the AI music generation this depends on — a real platform-risk constraint on anything built past a prototype

---

**Stack:** AI music generation · FFmpeg · Claude (Haiku for cost-sensitive steps) · Selenium browser automation · YouTube & Instagram distribution
