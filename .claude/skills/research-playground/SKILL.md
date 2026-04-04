---
name: research-playground
description: Generate an interactive HTML playground to explore completed research findings. Reads social and competitive reports and creates a visual, filterable dashboard. Run after /research-social and /research-competitive.
allowed-tools: Read, Write, Glob, Bash
---

# Research Playground Generator

You are generating an interactive HTML playground that visualizes completed GTM research findings. This is an optional step — run it after `/research-social` and `/research-competitive` have produced their reports.

## Project Selection

Resolve the active project before doing anything:

1. List directories under `projects/`
2. If the user passed a project name as an argument, use it
3. If only one project exists, use it
4. If multiple exist, ask the user which one

## Context Check

Read these files:
1. `projects/<project>/context.md` — Research context (required)
2. `projects/<project>/reports/social-channel-analysis.md` — Social analysis (required)
3. `projects/<project>/reports/competitive-analysis.md` — Competitive analysis (required)

If either report is missing, tell the user to run the corresponding skill first.

## Your Task

Generate a single self-contained HTML file at `reports/playground.html` that lets users interactively explore their research findings. Then open it in the browser with `open reports/playground.html`.

## What to Extract from Reports

Read both reports thoroughly and extract:

**From research-context.md:**
- GTM model name and core mechanic
- Category/industry
- Brand name (if applicable)
- Reference companies

**From social-channel-analysis.md:**
- Channels analyzed (name, layer, activity level, key value)
- Hype/model mechanics (name, description, who does it well, engagement impact)
- Community dynamics (findings with evidence)
- Scarcity/model sentiment (positive, negative, net effect)
- Consumer segments (name, motivations, channels, what they value)
- Transferability notes (tactic, transfers?, notes)
- Opportunities (name, insight, evidence, application)
- Notable quotes (category, quote, source)
- Research gaps

**From competitive-analysis.md:**
- Tier 1 operators (name, model, mechanics, what works, what transfers)
- Tier 2 operators (name, approach, what's relevant)
- Transferability matrix (tactic, origin, feasibility, cost, time, priority)
- Gap analysis items (tactic, description)
- Anti-patterns / red flags (pattern, why dangerous)
- Strategic implications / recommended models

## HTML Playground Structure

Build a single-file HTML page with inline CSS and JS. No external dependencies.

### Layout

```
+------------------------------------------+
|  Header: [GTM Model] Research Explorer   |
|  [Brand] · [Category]                    |
+------------------------------------------+
|  Tab bar: Overview | Social | Competitive |
|           Opportunities | Quotes          |
+------------------------------------------+
|                                          |
|  Tab content area                        |
|  (changes per tab)                       |
|                                          |
+------------------------------------------+
```

### Tab: Overview
- Research context summary (model, category, brand, stage)
- Key stats: channels analyzed, operators profiled, opportunities identified, quotes collected
- Executive summaries from both reports (truncated with expand)

### Tab: Social
- Channel overview table (filterable by layer: broad / category-specific / both)
- Model mechanics cards (expandable — click to see details)
- Community dynamics findings
- Sentiment summary (positive vs negative with visual indicator)
- Consumer segments as cards with key attributes

### Tab: Competitive
- Tier 1 operators as expandable cards showing mechanics profile
- Tier 2 operators as a lighter list
- Mechanics comparison matrix as an interactive table (sortable columns)
- Filter by: all operators, tier 1 only, tier 2 only

### Tab: Opportunities
- Transferability matrix as interactive table
  - Sortable by priority (HIGH → MEDIUM → LATER → NO)
  - Filterable by cost ($0 vs requires spend)
  - Color-coded priority badges
- Gap analysis items as cards
- Anti-patterns / red flags section

### Tab: Quotes
- All quotes organized by category
- Click-to-copy individual quotes
- Filter by category

## Design Requirements

- **Dark theme.** Dark background (#0d1117), light text (#e6edf3), accent color derived from the GTM model (e.g., warm orange for drops, blue for subscriptions — pick something appropriate).
- **System font** for UI, monospace for data values.
- **Responsive.** Works on laptop screens (1200px+). Doesn't need mobile.
- **No external dependencies.** All CSS and JS inline.
- **Instant interactions.** Filters and sorts update immediately, no loading states.
- **Expandable cards.** Click to expand/collapse detail sections. Start collapsed for dense views.
- **Smooth animations.** Subtle transitions on expand/collapse and tab switches.

## State Management

```javascript
const data = {
  context: { /* extracted from research-context.md */ },
  social: {
    channels: [ /* extracted */ ],
    mechanics: [ /* extracted */ ],
    dynamics: [ /* extracted */ ],
    sentiment: { /* extracted */ },
    segments: [ /* extracted */ ],
    transferability: [ /* extracted */ ],
    opportunities: [ /* extracted */ ],
    quotes: [ /* extracted */ ],
    gaps: [ /* extracted */ ]
  },
  competitive: {
    tier1: [ /* extracted */ ],
    tier2: [ /* extracted */ ],
    matrix: [ /* extracted */ ],
    gaps: [ /* extracted */ ],
    antiPatterns: [ /* extracted */ ],
    recommendations: [ /* extracted */ ]
  }
};

const state = {
  activeTab: 'overview',
  socialLayerFilter: 'all',
  competitiveTierFilter: 'all',
  opportunitySort: 'priority',
  opportunityCostFilter: 'all',
  quoteCategory: 'all'
};
```

## After Generating

1. Write the HTML file to `projects/<project>/output/playground.html`
2. Open it: `open projects/<project>/output/playground.html`
3. Tell the user: "Playground generated at `projects/<project>/output/playground.html` and opened in your browser. You can also share this file — it's fully self-contained."

## Guidelines

- Extract REAL data from the reports — don't use placeholder content
- The playground should feel like a polished dashboard, not a prototype
- Prioritize scannability — users should get the key insights at a glance
- Keep the file under 2000 lines if possible — dense but not bloated
- Test that all interactive elements work (tabs, filters, sorts, expand/collapse, copy)
