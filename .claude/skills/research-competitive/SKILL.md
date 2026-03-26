---
name: research-competitive
description: Map the competitive landscape of go-to-market model operators. Analyzes operators across categories and within the user's specific category, mapping their mechanics and identifying transferable tactics. Adapts framework dimensions at runtime based on research context.
allowed-tools: Read, Write, WebFetch, WebSearch, AskUserQuestion
---

# Competitive Landscape Analysis

You are helping map the competitive landscape of a go-to-market model to identify transferable mechanics and positioning opportunities for the user's category.

## Context Check

First, check for:
1. `.claude/research-context.md` — Research context (required)
2. `reports/social-channel-analysis.md` — Social analysis (optional, enriches profiles with community perception)

If research-context.md doesn't exist, ask the user to run `/research-init` first, or gather minimal context directly.

## Your Task

Create a comprehensive competitive analysis that maps:
- **Tier 1:** Best operators of this GTM model across all categories — their mechanics, execution, what makes them work
- **Tier 2:** Operators in the user's category (or adjacent) — what's already happening in the target space

Then identify which mechanics transfer to the user's category and where the white space is.

## Operator Identification

### Tier 1 — Best operators across categories

Start from reference companies in the research context. Expand via web research to find the most notable operators of this GTM model. Cover multiple categories to show how the model works in different contexts.

### Tier 2 — Operators in user's category

- Brands in the user's category already using this model
- Adjacent categories that have adopted it
- How established players experiment with it vs. how insurgents use it natively

### Ask the user:
- "Are there specific companies you want me to focus on?"
- "Any brands in your category you've noticed using this model?"
- "Other categories worth looking at for inspiration?"

## Mechanics Framework

Based on the research context, identify the right analysis dimensions for the GTM model being studied.

### Structural Dimensions (always include)

| Dimension | What to Map |
|-----------|-------------|
| **Core Mechanic** | How the model's fundamental mechanism is implemented |
| **Cadence/Rhythm** | How often and with what timing |
| **Audience/Community** | How they build and engage their audience |
| **Channel Mix** | Where the model is executed (own platform, social, retail, etc.) |
| **Price Architecture** | How pricing relates to the model (entry points, premium, core line) |

### Model-Specific Dimensions (determine at runtime)

Add dimensions specific to this GTM model. Examples to guide selection:

| GTM Model | Additional Dimensions |
|-----------|----------------------|
| Drops/scarcity | Scarcity model, hype engine, secondary market |
| Subscriptions | Retention mechanics, tier structure, churn prevention |
| Community-led | Contribution incentives, governance model, network effects |
| Product-led growth | Onboarding flow, viral mechanics, conversion triggers |
| Marketplace | Supply acquisition, trust mechanisms, take rate |
| Freemium | Feature gating, upgrade triggers, usage limits |

Name the dimensions clearly and apply them consistently across all operators.

## Analysis Process

### 1. Operator Research
For each operator, gather information on all framework dimensions using web research.

### 2. Mechanics Profiling
Apply the full framework (structural + model-specific dimensions) to each operator.

### 3. Transferability Assessment
For each operator's tactics: could this work in the user's category? What's the barrier?

### 4. Gap Analysis
Where are the untapped mechanics, the missing applications, the positioning white space?

## Output Format

Create `reports/competitive-analysis.md`:

```
# Competitive Analysis: [GTM Model] Operators & [Category]

## Executive Summary
[2-3 paragraph summary of competitive landscape and key transferable insights]

## Research Context
- **GTM Model:** [from context]
- **Category:** [from context]
- **Brand:** [if applicable]

## Market Overview

### The [GTM Model] Ecosystem
- **Scale:** [how big this model is — revenue, adoption, growth]
- **Key dynamics:** [what makes this model work]
- **Evolution:** [how it has evolved over time]

### [GTM Model] in [Category] — Current State
- **Adoption level:** [how much the category uses this model]
- **Who's doing it:** [brands identified]
- **Opportunity:** [gap between model maturity and category adoption]

## Tier 1: [GTM Model] Operators — Full Profiles

### [Operator 1]

| Attribute | Details |
|-----------|---------|
| **Founded** | [year] |
| **Category** | [what they do] |
| **Scale** | [size/reach indicators] |
| **Audience** | [who they serve] |

**Model Mechanics Profile:**

| Dimension | How They Do It |
|-----------|---------------|
| **Core Mechanic** | [implementation] |
| **Cadence** | [timing/frequency] |
| **Audience/Community** | [engagement model] |
| **Channel Mix** | [where it happens] |
| **Price Architecture** | [pricing approach] |
| **[Model-Specific 1]** | [details] |
| **[Model-Specific 2]** | [details] |
| **[Model-Specific 3]** | [details] |

**What makes them effective:**
- [Key strength 1]
- [Key strength 2]

**What's transferable to [category]:**
- [Tactic that could apply]
- [Why it transfers or doesn't]

---

### [Operator 2]
[Repeat structure]

---

## Tier 2: [Category] Operators

### [Brand 1]
| Attribute | Details |
|-----------|---------|
| **Category** | [specific category] |
| **How they use [model]** | [description] |
| **Target customer** | [who] |
| **Price range** | [range] |

**Tactics:**
- [What they do]
- [How it works]
- [Results/engagement]

---

### Adjacent Category Reference Points

#### [Adjacent Category 1]
- **Model:** [how they implement it]
- **What worked:** [lessons]
- **What didn't:** [lessons]

#### [Adjacent Category 2]
[Repeat]

## Comparative Analysis

### Mechanics Comparison Matrix

| Operator | Core Mechanic | Cadence | Audience | Channels | Price | [Model-Specific dims] |
|----------|--------------|---------|----------|----------|-------|----------------------|
| [Op 1] | [impl] | [freq] | [model] | [mix] | [range] | [details] |

### What Separates Great [GTM Model] Operators from Good Ones
- [Pattern 1]
- [Pattern 2]
- [Pattern 3]

## Gap Analysis — Opportunities for [Category]

### Untapped Mechanics for [Category]
#### Opportunity 1: [Name]
- **What it is:** [description]
- **Who does it:** [in other categories]
- **Why no one does it in [category]:** [barrier or oversight]
- **How it could work:** [application]
- **Risk:** [what could go wrong]

### Transferability Matrix

| Tactic | [Cat 1] | [Cat 2] | [Cat 3] | [User's Category] Potential | Barrier |
|--------|---------|---------|---------|---------------------------|---------|
| [tactic] | [who] | [who] | [who] | [assessment] | [barrier] |

### Positioning White Space
- [Positioning no brand in the category owns]

## Strategic Implications for [Brand/Category]

### Most Promising Approaches
1. [Approach] — why it fits, how to adapt
2. [Approach] — why it fits, how to adapt

### Approaches to Avoid
- [Approach] — why it doesn't fit

### Key Differentiators Available
- [What could be owned]

## Data Sources
- [List sources used]

## Research Gaps
- [ ] [What we couldn't find]
- [ ] [What needs deeper investigation]

---
*Analyzed by /research-competitive on [date]*
*GTM Model: [model] | Category: [category]*
*Operators analyzed: [count]*
```

## Guidelines

- Be objective — don't dismiss operators because their category seems unrelated. The mechanics may transfer.
- Use public information only — websites, social accounts, press coverage, market data
- Note confidence level when estimating scale (volumes, premiums, audience size)
- Include links to operator websites and key accounts
- Distinguish between what operators claim (marketing) and what's observable (actual results, engagement, market data)
- Consider international operators if relevant — GTM models vary by region
- Validate claims with evidence — an operator isn't successful just because they say so
- When assessing transferability, be honest about barriers — different categories have different economics, constraints, and customer expectations
