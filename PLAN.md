# ai-retro — Product Plan

## What it is

A personal, mindful accounting tool for LLM token usage. Not a guilt meter, not a corporate compliance dashboard — a mirror with memory. The goal is to make invisible compute costs visible enough that people naturally prompt lighter, without preaching.

## Core insight

Awareness alone doesn't change behavior (GPTFootprint study, 2025). But **immediate, concrete feedback** does — the student CO₂ feedback study cut tokens per prompt significantly. The product must translate raw numbers into something graspable *at the moment of prompting* and give a surface for *looking back*.

## Three layers

### 01 — The Translator (live)
Every session/prompt converted into concrete equivalents. Model-aware (GPT-4o ≠ Claude Haiku ≠ reasoning models). Rotating playful comparables: bus kilometres, trees, planes, dinosaurs, phone charges. Shows methodology and uncertainty range openly. This is the "one prompt = bus driving all night" moment.

### 02 — The Mirror (next)
Real-time nudge while prompting (plugin or API middleware), plus a weekly/monthly retrospective view: trends, what changed, which sessions were heavy and why. Import from OpenRouter's analytics API first; unique-key plugin later. The reflection loop where durable behavior shift happens.

### 03 — The Commons (later)
Optional community comparison. Contribute anonymized totals to a shared counter, or compare your week against the cohort. Not a leaderboard — a mirror held up collectively. Secondary feature, not the identity.

## Data ingestion (priority order)

1. **OpenRouter script** — clean Analytics API returns token counts per model/day. Lowest friction, real data, no account needed on our side.
2. **Unique API key + lightweight plugin** — we issue a key, their client sends anonymized records. Works for any provider.
3. **Provider-specific integrations** — Anthropic, Google, local (Ollama) adapters.

## Methodology (transparent by design)

- Per-model Wh/1K-token figures from arXiv 2505.09598 ("How Hungry is AI?"), 1k-in/1k-out column ÷ 2. Facility energy, PUE already baked into the source figures — do not apply another PUE factor.
- Grid carbon intensity: 400 gCO₂/kWh (IEA global average) as default; configurable per user region.
- Show the ±range, not a false-precise number. The spread is part of the story.
- Known limits of the current figures: assume a 50/50 input-output mix, and deployment hardware swings results up to 5× for identical weights.

## Design principles

- The calculator IS the hero, not a marketing headline.
- Numbers large and mono; labels small and quiet.
- Playful comparables keep it mindful, not preachy.
- No gradients, no glassmorphism, no SaaS card kit.
- Feels like a well-made CLI tool someone made a nice website for.
- Dark theme, warm amber accent (the glow of compute), sage green for positive equivalents.

## Distribution

- Home project, word-of-mouth among AI-using developers.
- Viral unit: the personal receipt / shareable retro card.
- GitHub Pages hosting (static, no server, no tracking).
- No account required for basic use.

## Tech stack (target, post-scaffold)

- Frontend: static HTML/CSS/JS (GH Pages compatible) → possibly a small SPA
- Backend (when Mirror layer lands): minimal — a single endpoint accepting anonymized POSTs, SQLite storage
- Plugin: thin HTTP client, one config line (your key), fires-and-forgets token counts
- OpenRouter import: standalone script (Node or Python), reads their Analytics API, generates a local retro report

## Repo structure (planned)

```
ai-retro/
├── index.html          ← this scaffold (GH Pages)
├── PLAN.md             ← this file
├── README.md           ← public-facing intro
├── scripts/
│   └── openrouter-import.mjs   ← pull token history, generate retro
├── plugin/             ← (later) unique-key logging plugin
└── api/                ← (later) minimal backend for Mirror/Commons
```

## Naming rationale

"ai-retro" borrows the agile retrospective ritual: look back at what happened, identify what was heavy, adjust the next iteration. Speaks fluent developer. Frames the product as habit-improvement rather than guilt-accounting. Free on GitHub (no collisions found in AI/carbon/blockchain namespaces).

## Carbon tax context (for the explainer page)

Corporations are NOT paying a carbon tax specifically on their AI bills. Canada removed the consumer carbon tax in 2025; industrial pricing (~$95/t in 2026) hits fuel/facility emissions. Data centers get caught via electricity procurement and provincial rate classes (Ontario drafting new rates so big DCs don't raise existing customers' bills). Real pressure is Scope 3 disclosure (California SB 253, 2027+) pushing companies to measure purchased-AI emissions. The measurement burden is falling on users → hence the need for a public, transparent tool.
