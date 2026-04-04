---
name: research-full
description: Stage-aware go-to-validation research sprint. Detects company stage (idea → pre-revenue → MVP → PMF → scale), then runs analyses at appropriate depth — full when data supports it, hypothesis-mode when grounded in comps, skip-to-question when it would be fiction. Produces stage-appropriate outputs: synthesis, playground, action brief, and investment memo (MVP+).
allowed-tools: Read, Write, Edit, Bash, Glob, Grep, Agent, WebSearch, WebFetch, Skill
---

# Full Research Sprint

A 10-step research process that forces you to do the strategic thinking, automates the research, and produces actionable outputs. Stage-aware: detects what data you actually have (idea, pre-revenue, MVP, PMF, scale) and adjusts analysis depth accordingly. Won't produce unit economics from thin air at the idea stage, won't skip growth lever analysis when you have real data. Designed to minimize time-to-value — pull what we already know, make assumptions, ask you to confirm, not re-derive.

## Philosophy

- **Pull, don't ask.** Start from what we already know (claude-mem, existing docs, prior chats). Only ask what can't be inferred.
- **Force the thinking.** Surface uncertainties and make the user respond. This IS the strategic work.
- **Automate the busywork.** Web research, competitive analysis, data synthesis — agents do this in parallel.
- **Stage-appropriate outputs.** Every sprint produces a synthesis doc, interactive playground, and action brief. Investment memo added at MVP+. Analysis depth scales with available data — full, hypothesis (grounded in comps), or skip-to-question.
- **Maintain a task list.** Every step surfaces tasks. The task list is a first-class output.

## Project Selection

Resolve the active project before doing anything:

1. List directories under `projects/`
2. If the user passed a project name as an argument, use it
3. If only one project exists, use it
4. If multiple exist, ask the user which one (or offer to create a new one)
5. If none exist, create `projects/<name>/input/`, `projects/<name>/reports/`, `projects/<name>/output/` and proceed

All project paths below use `projects/<project>/` as the root.

## Before Starting

Check if the project already has research output:
- Look in `projects/<project>/output/` for existing research
- Search claude-mem for prior conversations about this project
- Check `projects/<project>/input/` for any source documents (transcripts, notes, briefs)

If prior research exists, acknowledge it and consolidate rather than starting from scratch.

## Step 1: Pull Prior Context

Search for everything we already know:

1. **Claude-mem:** Search for the project name, product name, any related terms
2. **Existing files:** Check `projects/<project>/input/`, `projects/<project>/output/`, `projects/<project>/reports/` for any prior work
3. **Git history:** Check if there's a separate repo for this project

Compile everything found into a base research document at `projects/<project>/input/base-research.md`. Structure it as:
- What the product/business is
- How it works
- Target market
- Pricing (if known)
- Competitive landscape (if known)
- Team and roles
- Current status
- What's missing

If significant prior context exists, draft the base doc from it. If not, this doc will be sparse and Step 2 fills it.

## Step 2: Gather Raw Input

Ask the user if they have any raw input to add:
- Transcripts of conversations
- Notes or voice memos
- Pitch decks or briefs
- Links to relevant docs

Accept whatever format they provide. Extract structured information and integrate into the base research doc. Don't make them pre-organize — that's your job.

If the user has nothing to add and Step 1 produced a solid base doc, skip to Step 3.

## Step 3: User Review + Corrections

Open the base research doc in Zed for review:
```bash
zed projects/<project>/input/base-research.md
```

Ask the user to read it and tell you what's wrong, missing, or needs updating. Include a checklist of things that might only be in their head (adapt based on what's already documented):
- Pricing details
- Target customer specifics
- Competitive awareness
- Team roles and constraints
- Timeline and urgency
- Validation status
- Kill criteria

Update the doc with their corrections. This is where most wrong assumptions get caught.

## Step 4: Stage Detection

By now Steps 1-3 have pulled prior context, gathered raw input, and gotten user corrections. Use that evidence to determine the company stage.

### Evidence Inventory

Scan everything gathered so far for these signals:

| Signal | How to detect |
|--------|--------------|
| Product exists | Codebase linked, landing page URL, demo, screenshots in input/ |
| Users exist | Mention of signups, waitlist, beta users, user count |
| Revenue exists | Pricing is actual (not planned), mentions of payments, MRR, transactions |
| Retention data | Repeat usage, churn rate, cohort data, "users come back" |
| Growth channels proven | CAC numbers, conversion rates from actual campaigns, referral data |
| Unit economics known | Real margins, real COGS, actual LTV (not modeled) |

### Stage Inference

| Stage | Evidence pattern |
|-------|-----------------|
| **Idea** | No product, no users, no revenue. A concept + maybe domain expertise. |
| **Pre-revenue** | Product exists (or being built), maybe a landing page or waitlist. Zero paying customers. |
| **MVP** | Live product with some users AND some revenue. Early signal, small numbers. |
| **PMF** | Retention data, repeat customers, organic growth signals, revenue trending up. |
| **Scale** | Proven unit economics, multiple working channels, expansion questions. |

Present the inferred stage: "Based on what I see, you're at **[stage]** — [one-sentence evidence summary]. Sound right?"

Wait for confirmation before proceeding. If the user disagrees, adjust.

### Analysis Depth by Stage

This matrix controls how deep each analysis module goes in Step 7. Three depths:

- **Full** — run the complete analysis as specified
- **Hypothesis** — run but frame as hypothetical, grounded in comp data. Only when comps make it genuinely useful. Label clearly: "Hypothesis: based on [comp], if [assumption], then [conclusion]."
- **Skip → Question** — don't produce analysis. Add to uncertainties (Step 5) and task list: "[Analysis] can't be modeled yet — you need to answer: [specific questions]."

| Analysis Module | Idea | Pre-revenue | MVP | PMF | Scale |
|----------------|------|-------------|-----|-----|-------|
| Competitive landscape | Full | Full | Full | Full | Full |
| Channel & community mapping | Full | Full | Full | Full | Full |
| Value chain mapping | Hypothesis | Full | Full | Full | Full |
| Unit economics / margin trees | Skip → Question | Hypothesis | Full | Full | Full |
| Growth lever analysis | Skip → Question | Skip → Question | Hypothesis | Full | Full |
| LTV scenarios | Skip → Question | Skip → Question | Hypothesis | Full | Full |
| Capacity scaling model | Skip → Question | Hypothesis | Full | Full | Full |
| Mix modeling | Skip → Question | Skip → Question | Skip → Question | Hypothesis | Full |

## Step 5: Surface Uncertainties

Based on everything gathered — including any "Skip → Question" items from the stage detection depth matrix — identify 3-5 key uncertainties. These are things that could make or break the business that haven't been validated yet. Present them to the user and ask them to respond to each.

**Important:** Any analysis module that was set to "Skip → Question" in Step 4 will have generated specific questions (e.g., "Unit economics can't be modeled yet — what will you charge? What does fulfillment cost?"). Include these alongside the strategic uncertainties. They're different in nature — data gaps vs. strategic unknowns — but both need answers.

Good uncertainties are specific and testable:
- ❌ "Will people buy this?" (too vague)
- ✅ "Will founders pay $3,000 before seeing which designers they'll meet?" (specific, testable)

The user's responses will generate concrete ideas and tasks. Add them to the task list.

## Step 6: Generate Research Context + Task List

Create two artifacts:

1. **Research context** at `projects/<project>/context.md` — structured context that downstream research reads. Use the template from `/research-init` but adapt to what we've gathered. Include:
   - **Detected stage** (from Step 4) and the evidence that supports it
   - **Analysis depth matrix** — which modules run at Full, Hypothesis, or Skip
   - GTM model and core mechanic
   - Category and brand
   - Target audience (phased if applicable)
   - Pricing
   - Research priorities and key questions
   - Uncertain assumptions
   - Kill criteria
   - Research implications (what to focus competitive + channel analysis on)

2. **Task list** at `projects/<project>/reports/task-list.md` — running list of things to do, organized by category. Every subsequent step should check: "does this change the task list?"

3. **Process log** at `projects/<project>/reports/process-log.md` — step-by-step record of what was done and what it surfaced. Updated at each step.

## Step 7: Combined Landscape + Business Analysis

Run competitive research, channel mapping, and business model analysis as ONE combined pass. These feed each other — competitors reveal channels, the value chain reveals where margin concentrates, growth levers reveal what to focus competitive analysis on.

**Launch three parallel agents:**

**Agent A — Competitive Discovery:**
- Find and analyze every relevant player (direct competitors + adjacent models)
- For each: what they do, pricing, supply/demand acquisition, trust mechanism, positioning, gaps
- How do similar services solve trust/conversion problems?
- Pricing landscape across all players
- Referral/creator program mechanics

**Agent B — Channel & Community Mapping:**
- Where does the target customer discuss this problem?
- Where does the supply side (if two-sided) congregate?
- Launch platforms and their fit
- Content/community channels that drive growth
- The buyer's journey at this price point
- Referral mechanics

**Agent C — Business Model Analysis:**

This is the financial and structural analysis. **Read the detected stage from `context.md` and apply the depth matrix from Step 4.** Each sub-analysis runs at Full, Hypothesis, or Skip → Question depending on stage.

**C1. Value Chain Mapping:**

*Full (pre-revenue+):*
- Map the full chain from buyer to supplier, with every intermediary
- For each intermediary: what they charge, what they capture, what margin they earn (percentage of total)
- Where does value concentrate? Who has durable power and why?
- What layer does this product enter at? How does its economics compare to every other layer?
- Identify information asymmetries, lock-in mechanisms, and trust signals that sustain current margins
- Present as a flow diagram (text-based) + comparison table with specific dollar amounts

*Hypothesis (idea):*
- Map the ecosystem's money flow using publicly available intermediary data
- Frame the product's entry point as hypothetical: "If [product] enters at the [layer] layer, its economics would compare to intermediaries as follows..."
- Grounded in real intermediary pricing, not the product's own numbers

**C2. Unit Economics & Margin Modeling:**

*Full (MVP+):*
- Build margin trees for current state AND 12-month target (revenue per unit → COGS breakdown → gross margin → net contribution)
- Model unit economics at each realistic price point (low / mid / high)
- Cash characteristics: payback period, cash cycle, working capital needs, cash breakeven
- Capacity constraints: what's the binding constraint? How does revenue scale as the constraint relaxes?
- Fixed vs. variable cost structure
- Benchmark against comparable businesses at similar stage (with sources)

*Hypothesis (pre-revenue):*
- Build margin trees using planned pricing and estimated costs, benchmarked against comps
- Label clearly: "Hypothesis: at $X price point, based on [comp]'s cost structure, margins would be approximately Y%"
- Cash characteristics can be modeled from the planned collection mechanism
- Capacity constraints modeled from known supply/delivery mechanism

*Skip → Question (idea):*
- Surface as uncertainties: "What will you charge? What does fulfillment cost per unit? What's your delivery mechanism? What are your fixed costs?"

**C3. Growth & Margin Lever Analysis:**

*Full (PMF+):*
- Identify the 3-5 variables that control the majority of business outcomes
- Growth equation: Growth = Volume × Price × Mix × New Products × Geography (adapt formula to the business)
- For each variable: current state, sensitivity analysis, what moves the needle
- Binding constraints: what limits growth today? What becomes the constraint as each bottleneck clears?
- LTV scenarios: model 3-4 scenarios from pessimistic to optimistic with specific assumptions
- Mix modeling: one-time vs. recurring, low-tier vs. high-tier — how does revenue composition change the business?
- Price sensitivity signals from comparable products at similar price points

*Hypothesis (MVP):*
- Identify likely binding constraints from early data
- Model sensitivity using comp benchmarks where own data is thin
- Label: "Early signal: based on N transactions, the binding constraint appears to be [X]. Sensitivity modeled from [comp]."
- LTV scenarios framed as projections with explicit assumptions, not conclusions

*Skip → Question (idea, pre-revenue):*
- Surface as uncertainties: "What are your binding constraints? What drives volume? What's your pricing power? What does the growth equation look like?"

**After all three return:** Synthesize into reports based on stage:

1. `projects/<project>/reports/landscape-research.md` — always produced. Competitive landscape + channel mapping from Agents A and B.

2. `projects/<project>/reports/business-analysis.md` — **produced at pre-revenue and above.** Contains whatever Agent C produced at the appropriate depth:
   - Executive summary (thesis in one paragraph)
   - Value chain map with margin comparison table (Full or Hypothesis, labeled accordingly)
   - Unit economics at each price point (if Full or Hypothesis)
   - Margin trees — current + target (if Full or Hypothesis)
   - Growth equation and binding constraints (if Full or Hypothesis)
   - LTV scenarios (if Full or Hypothesis)
   - Cash characteristics (if Full or Hypothesis)
   - Capacity scaling model (if Full or Hypothesis)
   - Sections that were Skip → Question don't appear here — they're in the task list

   At **idea stage**, skip this report entirely. Any hypothesis-mode value chain analysis goes directly into the synthesis document instead.

Update the task list with new items surfaced from all three agents, including all Skip → Question items from Agent C.

## Step 8: Validation / Action Plan

Based on all research, generate a concrete plan with:

1. **Proposed decisions** — recommend specific answers to open questions based on evidence. Ask the user to confirm or adjust each one.
2. **MVP definition** — what's the absolute minimum needed to test the core hypothesis?
3. **Channel sequencing** — what first, what second, what can wait
4. **Timeline** — 30-day sprint with weekly goals
5. **Kill/go criteria** — specific, measurable conditions
6. **"What NOT to do" guardrails** — based on the team's noted tendencies

Save to `projects/<project>/reports/validation-plan.md`.

## Step 9: Consolidate Prior Research (if applicable)

If the user has done research in other chats or tools:
1. Ask where it lives
2. Copy (not move) into `projects/<project>/output/` with subdirectories per source
3. Read via parallel agents to understand what each contributes uniquely
4. Note overlaps and unique additions

Skip this step if there's no prior research outside this session.

## Step 10: Final Outputs

Generate artifacts in parallel. **Which artifacts and how deep depends on the detected stage:**

| Artifact | Idea | Pre-revenue | MVP | PMF | Scale |
|----------|------|-------------|-----|-----|-------|
| Synthesis doc | Yes | Yes | Yes | Yes | Yes |
| Interactive playground | Yes (fewer tabs) | Yes | Yes | Yes | Yes |
| Action brief | Yes (mostly questions) | Yes | Yes | Yes (mostly actions) | Yes |
| Investment memo | No | No | Yes | Yes | Yes |

### A. Synthesis Document
`projects/<project>/output/synthesis.md`

One comprehensive narrative combining all research. Structured for NotebookLM video generation. **Length scales with stage:** ~1,500-2,500 words at idea stage (heavier on market/competitive), ~3,000-5,000 words at MVP+.

Sections (include only those that have content from the analysis):
- The problem and why it matters
- What the product is and how it works
- Market opportunity with specific data
- Value chain: how money flows and where the product enters *(skip at idea unless hypothesis was produced)*
- Competitive landscape
- Unit economics: margin trees, price sensitivity, cash characteristics *(MVP+ only; at pre-revenue, include hypothesis if produced)*
- Growth levers: the 3-5 variables that drive 80% of outcomes *(MVP+ only)*
- Channels and go-to-market
- Validation plan
- Risks and mitigations
- Key metrics to track
- Open tasks

Sections that ran at **Hypothesis** depth appear with a clear "Hypothesis" marker. Sections that were **skipped** don't appear — their questions are in the action brief instead.

Write it as a story, not a bullet list. Every claim has a number or source.

### B. Interactive Playground
`projects/<project>/output/playground.html`

Single-file HTML dashboard. **Tabs render only when they have data** — don't show empty tabs.

| Tab | Idea | Pre-revenue | MVP+ |
|-----|------|-------------|------|
| Overview | Yes | Yes | Yes |
| Market | Yes | Yes | Yes |
| Value Chain | No | Yes | Yes |
| Competitors | Yes | Yes | Yes |
| Economics | No | No | Yes |
| Channels | Yes | Yes | Yes |
| Validation/Strategy | Yes | Yes | Yes |
| Tasks | Yes | Yes | Yes |

Design: dark mode, card-based, data in JS objects for extensibility. Match the established design language (--bg: #0d0d0d, accent green #6ee7b7, monospace numbers).

### C. Action Brief / NotebookLM Prompt
`projects/<project>/output/notebooklm-prompt.md`

A document that serves dual purpose:
1. When fed to NotebookLM alongside the synthesis, it steers the video toward action
2. Standalone, it's the "what to do next" brief

Structure:
- Part 1: Most interesting findings (what the research revealed)
- Part 2: Questions to answer together (decisions that need founder judgment) — **at idea/pre-revenue, this section is the heaviest.** Include all Skip → Question items from the depth matrix alongside strategic questions.
- Part 3: 30-day action plan (specific, sequenced, with names and dates) — **at PMF/scale, this section is the heaviest.** More action items, fewer open questions.
- The bottom line (one paragraph — the single question that matters most right now)

Tone: direct, founder-to-founder, not consultant-to-client.

### D. Investment Memo *(MVP and above only)*
`projects/<project>/output/investment-memo.md`

**Skip at idea and pre-revenue** — not enough grounded data. The hypothetical pieces end up in the synthesis narrative and the action brief's open questions.

At MVP+: consolidated analytical document pulling together the business model analysis with competitive and market findings. This is the structured, numbers-heavy counterpart to the narrative synthesis — designed for decision-making, not storytelling.

Structure:
- Executive summary / thesis in one paragraph
- Business model and unit economics (margin trees at each price point, cash characteristics)
- Value chain position (where the product sits, how its economics compare to every intermediary)
- Competitive position and moat (from landscape research)
- Growth equation and binding constraints (the 3-5 variables that drive 80% of outcomes)
- LTV scenarios (pessimistic through optimistic, with assumptions)
- Capacity scaling model (how revenue grows as constraints relax)
- Risks and kill criteria
- Open tasks

Every number has a source or is explicitly marked as an estimate. Tables over prose where data supports it.

## Throughout the Process

- **Open files in Zed** when asking the user to review (`zed <path>`)
- **Update the task list** at every step — every finding surfaces potential tasks
- **Update the process log** at every step — captures what was done and what it surfaced
- **Parallelize where possible** — agents for web research, reading prior docs, building outputs
- **Don't re-ask what you can infer** — make assumptions from prior context, ask user to confirm
- **Check noted tendencies** — if the user/team has known patterns (over-engineering, perfectionism, scope creep), call them out in guardrails
