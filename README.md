# gtm-research

Research any go-to-market model using Claude Code.

Three AI-powered research skills that help you understand how companies go to market — drops, subscriptions, community-led growth, product-led growth, marketplaces, and more — and whether those models could work for your business.

## What it does

1. **`/research-init`** — Set your research context: which GTM model, which category, which companies inspire you
2. **`/research-social`** — Map social channels to understand how the model works in practice: community dynamics, engagement patterns, consumer sentiment
3. **`/research-competitive`** — Map operators of the model across categories, analyze their mechanics, identify what transfers to your category

## Quick start

```bash
git clone <repo-url>
cd gtm-research
```

Open in Claude Code, then:

1. Run `/research-init` and answer the questions about your GTM model and category
2. Run `/research-social` for social channel analysis
3. Run `/research-competitive` for competitive landscape mapping

Reports are saved to `reports/`.

## Prerequisites

- [Claude Code](https://claude.ai/claude-code) with WebSearch and WebFetch access

## How it works

The skills are **generic** — they adapt at runtime based on your research context. When you run `/research-init`, you describe what GTM model you're studying and for what category. The social and competitive skills then identify the right channels, extraction dimensions, and analysis frameworks for YOUR research.

No templates to customize, no code to generate. Just describe what you're researching and the tools adapt.

## Supported GTM models

Works well for researching:

- **Drops/scarcity** — limited releases, time-gated access, hype-driven
- **Subscriptions** — recurring revenue, retention mechanics, tier structures
- **Community-led growth** — organic advocacy, user communities, network effects
- **Product-led growth** — self-serve, viral loops, freemium-to-paid
- **Marketplace** — two-sided platforms, supply/demand dynamics
- **Freemium** — feature gating, upgrade triggers, usage-based
- **Direct/referral** — word-of-mouth, referral programs, ambassador models

And others — the skills adapt to whatever model you describe.

## Example output

See [`examples/drops/`](examples/drops/) for a complete worked example researching how drops-based marketing (MSCHF, Supreme, WHYN) could apply to a fine jewelry brand.

## Methodology

Read [`guide/methodology.md`](guide/methodology.md) for the thinking framework behind these tools — why GTM model research matters, the two-layer principle, and how to go from research to strategy.

## License

MIT (or your preferred license — update before publishing)
