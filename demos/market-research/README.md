# Market Research Workflow

Back to portfolio index: [README.md](../../README.md)

## Overview

Data-source orchestration workflow for federal market research, price benchmarking, vendor discovery, and compliance-aware sourcing support.

This demo shows how AI can help structure federal market research without fabricating vendor data, overclaiming compliance status, or replacing compliant judgment.

The goal is not to produce a quick supplier list. The goal is to organize public market data into a usable research package that supports price reasonableness, sourcing strategy, and acquisition decision support.

## Public Demo Page

Public portfolio context for this demo is published at [courtneypetersonchapman.notion.site](https://courtneypetersonchapman.notion.site/).

## What It Demonstrates

- transforms incomplete intake into a structured acquisition requirement
- maps output needs to public data sources and authoritative systems
- surfaces vendor, pricing, and compliance information as decision-support inputs
- identifies gaps and forces manual verification where public data is incomplete

## Repository Contents

| Path | Description |
|---|---|
| `reasoning-design/instructions.md` | GPT instruction set and workflow behavior |
| `prompts/input-examples/` | example requests for requirement clarification, strategy design, and acquisition-planning support |
| `prompts/output-examples/` | illustrative requirement assessments, research strategies, and research summaries |
| `workflow/market_research.svg` | workflow visual for presentation and walkthrough use |

## Source Documents

This GPT was built entirely from publicly available sources.

| Source | URL |
|---|---|
| FAR Part 10 — Market Research | https://www.acquisition.gov/far/part-10 |
| FAR Part 12 — Commercial Items | https://www.acquisition.gov/far/part-12 |
| FAR Part 13 — Simplified Acquisition | https://www.acquisition.gov/far/part-13 |
| FAR Part 15 — Contracting by Negotiation | https://www.acquisition.gov/far/part-15 |
| DFARS Part 225 — BAA / TAA | https://www.acquisition.gov/dfars/part-225-foreign-acquisition |
| SAM.gov | https://sam.gov |
| GSA Advantage | https://www.gsaadvantage.gov |
| FPDS.gov | https://www.fpds.gov |
| USASpending.gov | https://www.usaspending.gov |
| CPARS | https://www.cpars.gov |

## Development Methodology

### Step 1 — Identify the Regulatory Requirement

FAR Part 10 requires agencies to conduct market research before acquiring supplies or services. The research must be appropriate to the circumstances and support a determination that the price is fair and reasonable.

The GPT was designed to automate the labor-intensive parts of this process — finding vendors, benchmarking pricing, identifying socioeconomic status, and surfacing compliance considerations — while preserving the Contracting Officer's judgment on final determinations.

### Step 2 — Map the Data Sources

Each output element in the GPT maps to a specific public data source:

| Output Element | Source |
|---|---|
| Vendor registration and socioeconomic status | SAM.gov |
| GSA schedule availability and pricing | GSA Advantage |
| Historical federal procurement awards | FPDS.gov / USASpending.gov |
| Past performance ratings | CPARS |
| BAA / TAA compliance flags | DFARS Part 225 |
| NAICS code suggestion | FAR Part 12 / FPDS classifications |

### Step 3 — Design the Output Architecture

The GPT uses a two-table architecture:

- Primary table — item description, pricing, compliance notes, delivery options. Delivered by default.
- Vendor table — vendor identifiers, business size, socioeconomic category, federal experience, past performance. Delivered on request only.

This separation keeps the default output focused and actionable, while allowing users who need deeper vendor analysis to request it without cluttering the primary result.

### Step 4 — Define Scope and Guardrails

Key design decisions:

- Covers all procurement values, not just SAT. Above SAT purchases trigger a note that FAR Part 15 documentation requirements may apply.
- BAA/TAA compliance is flagged conditionally — only when product type, country of origin, or contract type warrants it. Flagging every item by default adds noise without value.
- When data sources return no results, the GPT instructs the user to verify manually and provides the direct URL. It does not estimate or fabricate vendor data.
- NAICS code suggestions and socioeconomic set-aside applicability are surfaced as information only. Final determinations remain with the Contracting Officer.

## Key Design Decisions

**Why two tables?**
Market research has two distinct audiences — the buyer who needs to know what something costs and where to get it, and the acquisition team that needs vendor qualification data. Separating them keeps the default output clean and lets users pull deeper detail only when needed.

**Why conditional BAA/TAA flagging?**
Flagging compliance on every item creates alert fatigue and slows the output. BAA and TAA are relevant for specific product types and contract requirements. The GPT applies judgment about when to flag rather than defaulting to always-on.

**Why ask the user to verify manually when data is missing?**
Federal procurement decisions cannot rest on fabricated or estimated vendor data. When SAM.gov, FPDS, or CPARS returns nothing, the GPT surfaces that gap and directs the user to the source rather than filling it with inference.

## Limitations

- This GPT is a research aid, not a procurement determination.
- Pricing data reflects publicly available information at the time of search and may not reflect current market conditions.
- Vendor registration status, past performance, and socioeconomic designations must be verified in the authoritative systems before award.
- BAA/TAA determinations require Contracting Officer review.
- This GPT does not substitute for legal or policy review.
 
## Public-Safety Note

Illustrative output examples in this folder use fictional vendor data created solely for demonstration of the workflow. Direct contact details are intentionally omitted so the examples stay portfolio-safe and do not imply current sourcing data.

## Why It Matters

Federal market research means fragmented public systems, inconsistent pricing visibility, and incomplete vendor data. This workflow structures public-source research into a repeatable process without fabricating or over-interpreting unavailable data.
