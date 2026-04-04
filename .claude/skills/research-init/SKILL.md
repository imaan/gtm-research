---
name: research-init
description: Initialize research context for go-to-market model exploration. Gathers GTM model, category, brand context, reference companies, and research priorities. Run this first before using other research-* skills.
allowed-tools: Read, Write, AskUserQuestion
---

# Initialize Research Context

Before running social analysis or competitive research, we need to understand your research context. This ensures analysis is appropriately scoped for the GTM model and category you're exploring.

## Your Task

Ask the user the following questions to build a context document. Ask them conversationally, grouping related questions together. Don't overwhelm — ask in 2-3 batches max.

## Questions to Gather

### GTM Model (ASK FIRST)

1. **What go-to-market model are you researching?**
   - Examples: drops/scarcity, subscriptions, community-led growth, product-led growth, marketplace, freemium, direct sales, referral/viral, licensing
   - If the user isn't sure, help them identify it from examples or companies they admire

2. **Which specific aspects or mechanics of this model interest you most?**
   - Examples by model:
     - Drops: scarcity, hype building, community, raffles, limited editions, collabs, cultural provocation, democratizing access
     - Subscriptions: retention mechanics, tiering, churn prevention, community perks, onboarding
     - Community-led: organic advocacy, contribution incentives, governance, network effects
     - PLG: self-serve onboarding, viral loops, freemium-to-paid conversion, usage-based pricing
     - Marketplace: supply acquisition, trust mechanisms, network effects, take rate

3. **Brief description of why this model interests you**

### Category/Industry

- What category or industry are you exploring this model for? (fashion, SaaS, food, fitness, luxury, etc.)
- Is this for a specific brand/company or general exploration?

### Brand Context (if applicable)

- Brand name and brief description
- What do they currently sell and how?
- Current positioning and price range
- What stage is the GTM model idea at?
  - Pure exploration / gathering inspiration
  - Specific concept in mind
  - Ready to design a strategy
  - Already running the model, looking to improve

### Reference Companies

- Which companies execute this GTM model well? (these become starting points for competitive research)
- Any companies you explicitly don't want to emulate? Why?

### Target Audience

- Who is the target customer for this GTM model?
- Same as the brand's current customer, or a new audience?
- What's the overlap between current customers and the model's typical audience?

### Research Priorities

- What do you most want to learn from this research?
- What assumptions are you most uncertain about?
- What would make you decide this model is a bad fit?

### Category Context

- How does this category currently handle the model's core mechanic? (e.g., does the industry already use scarcity? subscriptions? community?)
- Existing practices, seasonal patterns, norms

### Additional Context (Freeform)

After the structured questions, always ask:

> "Is there anything else I should know? Industry knowledge, personal experience with this GTM model, connections you have, research you've already done, or anything that might help me give better analysis."

## Output

## Project Selection

Resolve the active project before doing anything:

1. List directories under `projects/`
2. If the user passed a project name as an argument, use it
3. If only one project exists, use it
4. If multiple exist, ask the user which one (or offer to create a new one)
5. If none exist, ask for a project name and create `projects/<name>/input/`, `projects/<name>/reports/`, `projects/<name>/output/`

After gathering answers, create a context file at `projects/<project>/context.md` with this structure:

```
# Research Context: [GTM Model] for [Category/Brand]

## GTM Model
- **Model:** [which model — drops, subscriptions, community-led, etc.]
- **Description:** [brief description of the model and why it's interesting]
- **Core Mechanic:** [the fundamental mechanism — e.g., scarcity for drops, recurring revenue for subscriptions, organic advocacy for community-led]

## Category
- **Industry:** [category/industry]
- **Specific Brand:** [brand name, or "general exploration"]

## Brand (if applicable)
- **Name:** [brand]
- **Product:** [what they sell]
- **Current Model:** [how they sell today]
- **Price Range:** [range]
- **Positioning:** [who they are to customers]

## Exploration Stage
- **Stage:** [exploration/concept/strategy/optimization]
- **Interest Areas:** [which aspects of the model interest them]
- **Inspiration:** [what triggered the exploration]

## Reference Companies
- **Admire:** [list with brief notes on why]
- **Avoid:** [list with brief notes on why]

## Target Audience
- **Current Customer:** [who buys today]
- **Model Audience:** [who this GTM model would target]
- **Overlap:** [how these relate]

## Research Priorities
- **Key Questions:** [what to learn]
- **Uncertain Assumptions:** [what might be wrong]
- **Kill Criteria:** [what makes the model a bad fit]

## Category Context
- **Existing Practices:** [how the category currently handles this model's core mechanic]
- **Seasonal Patterns:** [relevant timing]
- **Category Norms:** [industry conventions around this mechanic]

## Additional Context
[Freeform]

## Research Implications
Based on this context:
- [Bullet points guiding research-social and research-competitive]
- [E.g., "Focus social analysis on [model] communities, not just [category] communities"]
- [E.g., "Competitive analysis should emphasize [category]-adjacent operators"]

---
*Generated by /research-init on [date]*
```

## Guidelines

- Be conversational, not interrogative
- If they don't know something, note it as "Unknown" or "TBD"
- Help users who aren't sure which GTM model they're looking at — provide examples
- The goal is a useful reference doc, not a perfect survey
- Infer what you can from prior conversation
- If they've already shared context, don't re-ask
- Stay focused on GTM model research — don't drift into product development, manufacturing, or other concerns
