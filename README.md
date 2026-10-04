# ai-retro

A retro for your LLM token usage. See what you burned, reflect on why, prompt lighter next week.

This is a home project — no tracking, no account, no guilt. Just a clearer picture of what your AI habits actually cost in energy and carbon.

## Try the calculator

Open [`index.html`](./index.html) in your browser (or wait for it to deploy to GitHub Pages). Pick a model, enter your token count, see what it translates to: bus kilometres, trees, planes, dinosaurs.

## What's coming

- **The Translator** *(live)* — model-aware impact calculator with playful comparables
- **The Mirror** *(next)* — OpenRouter import script, weekly reflection card, real-time nudge plugin
- **The Commons** *(later)* — optional community comparison, anonymized shared counter

## Methodology

Per-model energy figures come from the "How Hungry is AI?" inference benchmark (arXiv 2505.09598), using its 1k-input/1k-output column divided by two for a per-1K-token rate. Those figures are facility energy with datacenter overhead (PUE) already included, so no PUE factor is applied on top. Grid intensity defaults to 400 gCO₂/kWh (global average). We show ranges, not false precision — the spread is part of the story. See the [methodology section](./index.html#methodology) on the page for details.

## Why this exists

Estimates for the same query range wildly depending on methodology. Only two providers publish anything concrete (OpenAI ~0.34 Wh/query, Google ~0.24 Wh/prompt). Corporations aren't paying a carbon tax on their AI bills — the measurement burden is falling on users. This tool makes the invisible visible, transparently, without pretending precision that doesn't exist.

## License

MIT
