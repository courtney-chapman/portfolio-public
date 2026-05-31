# LTDD Reasoning Workflow

Governed operational reasoning workflow for LTDD determination, evidence validation, escalation guidance, and audit-defensible documentation support.

Back to portfolio index: [README.md](../../README.md)

## Overview

This demo shows how AI can help someone reason through an audit-sensitive property loss scenario without jumping to unsupported conclusions.

The goal is not to generate a document quickly. The goal is to separate facts from assumptions, identify missing evidence, preserve uncertainty, and know when to escalate.

The workflow separates:
- verified facts
- interview statements
- unsupported assumptions
- required evidence
- escalation conditions

## Public Demo Page

Public portfolio context for this demo is published at [courtneypetersonchapman.notion.site](https://courtneypetersonchapman.notion.site/).

## What It Demonstrates

- triages incidents without assuming final disposition
- separates facts from interview statements and unsupported conclusions
- preserves uncertainty when documentation is incomplete
- surfaces escalation conditions before a draft is finalized
- supports audit-defensible reasoning under ambiguous operational conditions

## Operational Reasoning Flow

```text
Operational signal
↓
Safety and containment assessment
↓
Fact vs. statement separation
↓
Evidence validation
↓
Risk and escalation review
↓
LTDD determination
↓
Draft generation
↓
Validation and hardening
```

## Repository Contents

| File or Folder | Description |
| --- | --- |
| `reasoning-design/instructions.md` | instruction layers defining generation, validation, escalation, and evidence-handling behavior |
| `reasoning-design/knowledgefile.md` | encoded evidence rules, drafting standards, and rejection-pattern guidance |
| `prompts/output-examples/` | staged walkthrough outputs covering triage, interviews, evidence review, escalation, drafting, and validation |
| `workflow/ltdd_workflow.svg` | workflow visual for presentation and walkthrough use |

## Source Documents

The GPT was built entirely from publicly available sources. No proprietary materials were used.

| Source | URL |
| --- | --- |
| FAR 52.245-1 - Government Property | [acquisition.gov/far/52.245-1](https://www.acquisition.gov/far/52.245-1) |
| DFARS 252.245-7005 - Management and Reporting of Government Property | [acquisition.gov/dfars/252.245-7005-management-and-reporting-government-property](https://www.acquisition.gov/dfars/252.245-7005-management-and-reporting-government-property) |
| PGI 245.1 - Government Property Procedures | [acquisition.gov/dfarspgi/pgi-245.1](https://www.acquisition.gov/dfarspgi/pgi-245.1) |
| PIEE GFP Module - Property Loss Training | [dodprocurementtoolbox.com](https://www.dodprocurementtoolbox.com) |
| DFARS Case 2020-D029 - Clause Consolidation Overview | [acquisition.gov/dfars/252.245-7005-management-and-reporting-government-property](https://www.acquisition.gov/dfars/252.245-7005-management-and-reporting-government-property) |

## Development Methodology

### Step 1 - Extract Requirements from Regulations

Starting with FAR 52.245-1, DFARS 252.245-7005, and PGI guidance, the first step was identifying:

- what an LTDD package is legally required to contain
- required wording for key statements such as financial liability, willful misconduct, and relief request
- what DCMA reviews during adjudication
- how property loss cases are submitted through PIEE

These requirements became the structural backbone of the knowledge file.

### Step 2 - Encode Rules into a Knowledge File

The knowledge file is not a copy of the regulations. It is a distillation that translates regulatory requirements into:

- a required LTDD structure with 15 sections
- evidence-versus-assumption rules for what can be stated as fact and what must remain unverified
- safe and unsafe wording examples
- common rejection triggers
- root cause and corrective action standards
- required statement language
- a validation checklist

The goal was to encode the judgment a knowledgeable reviewer would apply, not just the text of the rules.

### Step 3 - Build the Instruction Set

The instruction set defines how the GPT behaves, not what it knows.

Key design decisions included:

- Two-mode architecture:
  Generation mode is used when the user provides facts and asks for a draft.
  Validation mode is used when the user provides a draft and asks for review against requirements.
- Audit-defensive posture:
  The GPT is instructed to never fabricate facts, infer dates, invent documentation, or turn unverified statements into facts, mirroring the standard a DCMA reviewer would apply.
- Required output structure:
  The instruction set enforces the 15-section LTDD format and required wording for key statements drawn from FAR 52.245-1(f)(1)(vii)(B).

### Step 4 - Test and Iterate

Testing focused on two primary failure modes:

- unsupported claims, such as stating disposal, destruction, or cannibalization as fact without documentation
- vague outputs, such as generic root causes, insufficient corrective actions, or missing required statements

### Step 5 - Refine Using Rejection Archetypes

Synthetic DCMA rejection examples were used to simulate the feedback loop a real submission would generate. Each rejection archetype exposed a gap in the instruction set or knowledge file, which was then addressed.

## Iteration Log

| Iteration | Evidence | Update Made |
| --- | --- | --- |
| `v1` | Initial build from FAR, DFARS, and PGI | Base instruction set and knowledge file created |
| `v2` | Testing revealed the GPT stated disposal as fact without documentation | Added evidence-versus-assumption rules to the knowledge file and explicit prohibitions to the instructions |
| `v3` | Testing revealed vague root causes and corrective actions | Added stronger root cause and corrective action standards with strong and weak examples |
| `v4` | Procedural rejection archetype | Added PIEE submission requirements and documentation checklist |
| `v5` | Substantive rejection archetype | Added storage, access, and Government property marking requirements to the investigation checklist and tightened validation fail criteria |

## Demonstrated Capabilities

- evidence-constrained reasoning
- escalation-aware workflow behavior
- audit-defensible drafting
- uncertainty preservation
- root-cause validation
- corrective-action alignment
- operational hardening and validation review

## Example Workflow

The included demo scenario walks through:

1. initial LTDD triage
2. interview support
3. evidence validation
4. risk and escalation review
5. controlled draft generation
6. validation and hardening

Example outputs are included in `prompts/output-examples/`:

- `initial-triage-walkthrough.md`
- `interview-support-question-set.md`
- `evidence-validation-review.md`
- `risk-and-escalation-review.md`
- `ltdd-draft-generation-example.md`
- `validation-and-hardening-review.md`

## Key Design Decisions

### Why two modes?

Most domain GPTs are single-purpose. Separating generation from validation allows the same knowledge base to support two distinct workflows without conflating them.

### Why a knowledge file instead of embedding everything in the instructions?

The instruction set defines behavior. The knowledge file defines domain rules. Keeping them separate makes each easier to maintain and update independently as requirements or rejection patterns evolve.

### Why encode rejection triggers explicitly?

DCMA rejection reasons are consistent and predictable. Encoding them as explicit fail criteria allows the GPT to catch likely rejection issues before submission, which is a core part of the tool's value.

### Why Bayesian framing?

Each test or rejection is treated as evidence that updates the model. The instruction set and knowledge file are not static; they are posteriors that improve with each iteration. This makes the development process more reproducible and explainable.

## Limitations

- This GPT is a drafting and validation aid, not a legal determination.
- It cannot verify facts provided by the user.
- Output quality depends on the completeness and accuracy of inputs.
- It does not substitute for review by a qualified Property Administrator or legal counsel.

## Public-Safety Note

This repository is intended to demonstrate operational reasoning architecture and governance-aware workflow design. Public examples have been sanitized and simplified for demonstration purposes.
