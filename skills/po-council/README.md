# PO Council

A reusable, model-agnostic decision skill for Product Owners and AI-assisted product workflows.

**Author:** Andreas Stolz

## What it does

PO Council adds a structured decision layer before delivery work begins. It is intended for product ideas, architecture choices, build-vs-buy decisions, tooling choices, scope changes, prioritization conflicts, and other non-trivial decisions.

The workflow is simple:

1. Frame the decision neutrally.
2. Pass it through a complexity gate.
3. Run independent product perspectives before they can anchor on each other.
4. Challenge the initial analyses.
5. Synthesize one PO recommendation while preserving meaningful dissent.
6. Convert the result into an actionable experiment, issue, ADR, defer/reject record, or escalation.

## Why

Single-agent answers can become overconfident, anchored, or too implementation-focused. PO Council deliberately separates perspectives such as customer value, first principles, red-team risk, delivery feasibility, and prioritization before producing a final recommendation.

It is designed to answer not only **“Can we build this?”** but **“Should we build this, what do we need to learn first, and what is the smallest sensible next step?”**

## Modes

- **QUICK** — lightweight challenge for medium-impact decisions.
- **STANDARD** — default five-perspective council with peer challenge and synthesis.
- **DEEP** — for strategic, expensive, difficult-to-reverse, or high-risk decisions.

## Output

A completed Council produces:

- Verdict: `ACCEPT`, `EXPERIMENT`, `DEFER`, `REJECT`, or `ESCALATE`
- recommendation and rationale
- strongest counterargument
- assumptions and risks
- preserved dissent
- evidence gaps
- confidence
- smallest validation/MVP
- success and acceptance criteria
- one concrete next action

## Use

The full reusable specification is in [`SKILL.md`](./SKILL.md).

Typical prompts:

```text
Run PO Council on this idea.
Council this decision.
Pressure-test this as a Product Owner.
Run a STANDARD Council and turn the result into acceptance criteria.
```

The skill is intentionally project-neutral. Private project context should stay in the consuming project's private layer rather than being copied into this public artifact.
