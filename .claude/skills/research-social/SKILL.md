---
name: research-social
description: Analyze social channels to understand how a go-to-market model works in practice — mechanics, community dynamics, engagement patterns, and transferability. Adapts channels and extraction dimensions at runtime based on research context.
allowed-tools: Read, Write, WebFetch, WebSearch, AskUserQuestion
---

# Social Channel Analysis

You are helping analyze social channels to understand how a go-to-market model works in practice — its mechanics, community dynamics, engagement patterns, and what could transfer to the user's category.

## Project Selection

Resolve the active project before doing anything:

1. List directories under `projects/`
2. If the user passed a project name as an argument, use it
3. If only one project exists, use it
4. If multiple exist, ask the user which one

## Context Check

First, check for:
1. `projects/<project>/context.md` — Research context (required)
2. `projects/<project>/reports/competitive-analysis.md` — Competitive landscape (optional, enriches analysis)

If context.md doesn't exist, ask the user to run `/research-init` first, or gather minimal context directly.

## Your Task

Analyze relevant social channels across two layers:
- **Layer 1:** The GTM model broadly — how does it work across categories?
- **Layer 2:** The model in the user's specific category — who's already doing it? What hasn't been tried?

## Channel Identification

Based on the research context (model + category), identify the most relevant channels. Don't use a fixed list — determine what matters for THIS model and category.

**Guidance by platform:**

### Reddit
Find subreddits where practitioners and customers of this GTM model discuss it. Search for the model name, key brands, and related terms. Also find subreddits for the user's specific category.

### Twitter/X
Find accounts and conversations around this model — brand accounts, practitioners, critics, industry commentators.

### Instagram/TikTok
Find content creators covering this model's outputs — unboxings, reviews, hauls, behind-the-scenes, commentary.

### Discord/Slack
Find community servers related to this model or its practitioners.

### Forums
Find domain-specific forums where this model is discussed (e.g., PurseForum for luxury, Indie Hackers for PLG, Watchuseek for watches, etc.)

### Specialist Platforms
Identify any platforms specific to this model (e.g., StockX for drops, G2/Capterra for SaaS, Product Hunt for PLG, etc.)

### Ask the user:
- "Which channels have you already explored?"
- "Are there specific communities or accounts you know about?"
- "Any keywords or hashtags I should search?"

## Extraction Framework

### Fixed Dimensions (always extract)

**1. Community Dynamics**
- How do people talk about this model? Is there in-group identity?
- How do brands interact with communities between model events?
- What creates loyalty vs. one-time participation?

**2. Engagement Patterns**
- What content around this model gets the most engagement?
- What's the engagement arc (before, during, after model events)?
- How do comments/shares differ from non-model content?
- What makes people share/repost?

**3. Transferability Insights**
- What tactics from this channel/category could work for the user's category?
- What doesn't transfer and why?
- What would need adaptation vs. direct application?

### Model-Specific Dimensions (determine at runtime)

Based on the research context, identify 2-4 additional extraction dimensions specifically relevant to this GTM model. These should capture the model's unique dynamics.

**Examples to guide dimension selection:**

| GTM Model | Example Model-Specific Dimensions |
|-----------|----------------------------------|
| Drops/scarcity | Hype mechanics, scarcity sentiment, secondary market signals |
| Subscriptions | Retention/churn sentiment, pricing sensitivity, switching triggers |
| Community-led | Organic advocacy signals, contribution patterns, governance sentiment |
| Product-led growth | Onboarding friction, viral loops, free-to-paid conversion signals |
| Marketplace | Trust/safety sentiment, supply-demand balance, platform lock-in perception |
| Freemium | Feature-gating sentiment, upgrade triggers, "good enough" perception |

Name the dimensions clearly and apply them consistently across all channels.

**For each model-specific dimension, extract:**
- What patterns do we see?
- Who does it well? Poorly?
- What generates positive vs. negative sentiment?
- Direct quotes and examples

## Analysis Process

### 1. Channel Mapping
Identify which channels are most relevant and active for this model + category.

### 2. Per-Channel Extraction
Apply fixed dimensions + model-specific dimensions to each channel.

### 3. Pattern Recognition
- What themes appear across channels and categories?
- What's specific to the model broadly vs. the user's category?
- What's signal vs noise?
- Where do model culture and category culture overlap naturally?

## Output Format

Create `projects/<project>/reports/social-channel-analysis.md`:

```
# Social Channel Analysis: [GTM Model] in [Category]

## Executive Summary
[2-3 paragraph summary of key findings across both layers]

## Research Context
- **GTM Model:** [from context]
- **Category:** [from context]
- **Brand:** [if applicable]

## Channels Analyzed

### Channel Overview
| Channel | Communities/Sources | Layer | Activity Level | Key Value |
|---------|---------------------|-------|----------------|-----------|
| [channel] | [sources] | Model broad / Category specific / Both | High/Med/Low | [what we learned] |

## Layer 1: [GTM Model] — How It Works in Practice

### Model Mechanics
#### [Model-Specific Dimension 1: named at runtime]
- **How it works:** [description]
- **Who does it well:** [brands/examples]
- **Engagement impact:** [what happens]
- **Examples:**
  - "[description or quote]" - [source]

#### [Model-Specific Dimension 2: named at runtime]
[Repeat structure]

### Community Dynamics
#### [Dynamic 1]
- **What we see:** [description]
- **Evidence:** [quotes, examples]
- **Implication for [category]:** [transferability]

### [Model-Specific Dimension 3: if applicable]
- **Positive signals:** [evidence]
- **Negative signals:** [evidence]
- **Net effect on brand perception:** [analysis]

### [Model-Specific Dimension 4: if applicable]
- **Patterns observed:** [what we see]
- **What they signal:** [interpretation]

## Layer 2: [Category] — Current State of [GTM Model]

### How [Category] Brands Use [Core Mechanic] Today
- [What's already happening in the space]

### Adjacent Category Examples
- **[Adjacent 1]:** [how they use this model]
- **[Adjacent 2]:** [how they use this model]
- **Implications for [category]:** [what transfers]

### Gaps in [Category]
- [What no brand in this category is doing yet]
- [Opportunities identified]

## Voice of the Consumer

### What Drives Participation
1. [Factor] - [evidence]
2. [Factor] - [evidence]

### What Causes Backlash
1. [Factor] - [evidence]
2. [Factor] - [evidence]

### Segment Differences
#### [Segment 1: determined from context]
- Motivations:
- Channels:
- What they value:

#### [Segment 2]
[Repeat]

## Influencer & Creator Landscape

| Name/Channel | Platform | Following | Focus | Relevant? |
|--------------|----------|-----------|-------|-----------|
| [name] | [platform] | [size] | [what they cover] | [how they relate] |

## Transferability Notes

*Community-lens view of what transfers. For the detailed operator-by-operator transferability matrix, see `projects/<project>/reports/competitive-analysis.md`.*

- [Tactic community says works] — [evidence]
- [Tactic community says doesn't work] — [evidence]
- [Tactic with mixed sentiment] — [nuance]

## Opportunities for [Brand/Category]

### Opportunity 1: [Name]
- **Insight:** [what we learned]
- **Evidence:** [quotes, patterns]
- **How it could apply:** [specific application]

## Notable Quotes Repository

### On [Model Core Mechanic]
> "[quote]" - [source]

### On Community & Identity
> "[quote]" - [source]

### On [Category]-Specific Applications
> "[quote]" - [source]

## Research Gaps
- [ ] [Gap 1]
- [ ] [Gap 2]

## Recommended Next Steps
1. [Follow-up research]
2. [Communities to monitor]
3. [Creators to track]

---
*Analyzed by /research-social on [date]*
*GTM Model: [model] | Category: [category]*
*Channels: [list of channels reviewed]*
```

## Guidelines

- Use direct quotes whenever possible — the community's exact words are more powerful than summaries
- Note the source/channel for each insight
- Distinguish between model enthusiasts vs. casual observers — weight accordingly
- Watch for recency — tactics evolve fast, note when evidence is dated
- Be aware of platform bias — different platforms attract different demographics
- Look for consensus vs. outlier opinions — note when sample sizes are small
- Separate what people say they want from what they actually engage with
- Flag when insights are from adjacent categories vs. the user's specific category
- Name model-specific extraction dimensions clearly so the output is self-documenting
