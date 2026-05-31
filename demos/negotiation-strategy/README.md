# SaaS Negotiation Strategy Workflow

Back to portfolio index: [README.md](../../README.md)

## Overview

Phase-gated negotiation preparation workflow for SaaS procurement, federal guardrail awareness, vendor questioning, strategy development, and optional role-play practice.

This demo shows how AI can help a federal buyer prepare for a SaaS negotiation before entering a vendor conversation.

The goal is not to negotiate for the buyer. The goal is to structure preparation: gather minimum facts, identify vendor questions, define negotiation levers, preserve federal procurement constraints, and establish walk-away conditions.

## Public Demo Page

Public portfolio context for this demo is published at [courtneypetersonchapman.notion.site](https://courtneypetersonchapman.notion.site/).

## What It Demonstrates

- uses a phase-gated workflow so strategy is built before role-play is offered
- preserves federal procurement guardrails during commercial-style negotiation prep
- turns vague buying intent into actionable vendor questions and strategy inputs
- supports pricing leverage analysis without replacing buyer judgment

## Repository Contents

| Path | Description |
|---|---|
| `reasoning-design/instructions.md` | GPT instruction set and phased workflow behavior |
| `prompts/input-examples/` | example requests for internal discovery, vendor discovery, and negotiation preparation |
| `prompts/output-examples/` | illustrative question sets, negotiation structure, and strategy outputs |
| `workflow/saas_negotiation.svg` | workflow visual for presentation and walkthrough use |

## Source Documents

This GPT was built entirely from publicly available sources.

| Source | URL |
|---|---|
| FAR Part 10 — Market Research | https://www.acquisition.gov/far/part-10 |
| FAR Part 12 — Commercial Items | https://www.acquisition.gov/far/part-12 |
| FAR Part 13 — Simplified Acquisition | https://www.acquisition.gov/far/part-13 |
| FAR 52.212-4 — Commercial Item Contract Terms | https://www.acquisition.gov/far/52.212-4 |
| GSA Advantage / FAR Part 8 | https://www.gsaadvantage.gov |

## Development Methodology

### Step 1 — Identify the Problem

Federal buyers purchasing SaaS often negotiate without a structured framework. Common failure modes include:

- Agreeing to auto-renewal clauses that conflict with government fiscal year appropriations
- Accepting vendor-standard terms that override FAR 52.212-4 commercial item protections
- Failing to use available levers — volume, term length, payment timing — to achieve fair and reasonable pricing
- Entering vendor conversations without a clear walk-away position

The GPT was designed to address these gaps by giving buyers a repeatable, structured preparation process before any vendor conversation occurs.

### Step 2 — Define the Scope

The GPT is intentionally scoped to SaaS only. SaaS procurement has a distinct set of negotiation considerations — licensing flexibility, true-up processes, data portability, uptime SLAs, and renewal pricing — that differ significantly from hardware or professional services. Keeping the scope narrow produces more specific and actionable output.

Purchases above the SAT are noted as potentially requiring additional FAR Part 15 documentation, but the coaching framework applies across procurement values.

### Step 3 — Design the Phase Architecture

The GPT follows a five-phase workflow:

Phase 1 — Requirements Gathering: establishes the facts before any strategy is developed.
Phase 2 — Vendor Engagement Questions: generates tailored questions for the buyer to ask the vendor, organized by pricing, licensing, billing, and exit terms.
Phase 3 — Negotiation Strategy: builds a structured strategy based on what was learned in Phases 1 and 2, including primary objectives, negotiation levers, federal-specific considerations, and walk-away conditions.
Phase 4 — Advanced Suggestions: surfaces additional cost-saving and value-maximizing ideas specific to the product and vendor.
Phase 5 — Role-Play Practice: optional, offered only after strategy is fully developed.

The phase gate between Phase 1 and Phase 2 is enforced — the GPT does not generate strategy without minimum facts. This prevents generic output that does not reflect the actual procurement context.

### Step 4 — Encode Federal-Specific Guardrails

General negotiation coaching tools do not account for federal procurement constraints. Key guardrails added:

- Price must be fair and reasonable under FAR 13.106-3. The GPT notes what market research supports this determination.
- Auto-renewal clauses conflict with government fiscal year appropriations and are flagged explicitly.
- Termination for convenience language must be preserved per FAR 52.212-4.
- Sole source situations require documented justification before negotiation begins.

### Step 5 — Make Role-Play Optional and Conditional

Role-play is only offered after the buyer has a fully developed strategy. Offering it earlier produces unfocused practice that does not reflect the actual negotiation context. Making it conditional ensures it adds value rather than substituting for preparation.

## Key Design Decisions

**Why SaaS only?**
SaaS has a unique and consistent set of negotiation variables that justify a dedicated GPT. Covering all procurement types would produce generic output. Narrow scope produces specific, actionable coaching.

**Why phase gates?**
Procurement professionals sometimes want to skip to strategy before gathering enough facts. The phase gate between requirements gathering and strategy development enforces the right sequence and prevents the GPT from generating advice that does not fit the actual situation.

**Why encode federal guardrails explicitly?**
Commercial negotiation coaching assumes commercial contracting norms. Federal procurement operates under FAR constraints that commercial tools ignore. Encoding these explicitly — auto-renewal conflicts, termination for convenience, price reasonableness documentation — makes the output directly usable in a federal context rather than requiring the buyer to mentally translate general advice.

**Why make role-play conditional?**
Role-play is most valuable when the buyer already knows their strategy and wants to stress-test it. Offering it too early encourages buyers to practice before they are prepared, which reinforces weak approaches rather than strong ones.

## Limitations

- This GPT coaches preparation and strategy. It does not conduct negotiations or make procurement determinations.
- FAR references are provided as guidance only. Final legal and policy interpretations require Contracting Officer or legal counsel review.
- Role-play responses simulate vendor behavior based on general SaaS sales patterns and may not reflect the specific vendor's actual approach.
- This GPT does not substitute for acquisition planning, market research, or formal price analysis.

## Public-Safety Note

Illustrative output examples in this folder use fictional vendor and pricing data created solely for demonstration of the workflow.

## Why It Matters

Most SaaS negotiation guidance assumes commercial contracting norms. Federal procurement adds constraints such as appropriations, fair and reasonable pricing, FAR commercial item protections, and acquisition documentation. This workflow structures preparation within those constraints while preserving buyer judgment.
