# PO Council Skill

**Version:** 1.0.0  
**Author:** Andreas Stolz  
**Purpose:** A model-agnostic decision skill for Product Owners, product assistants, and agentic workflows.

## 1. Mission

The PO Council improves the quality of non-trivial product decisions before implementation starts.

It is not a brainstorming gimmick and it is not a replacement for normal Product Owner work. It is a structured decision mechanism that:

1. detects when a decision deserves deeper analysis,
2. collects independent perspectives before anchoring occurs,
3. forces disagreement and risk discovery,
4. synthesizes the evidence into one actionable PO decision,
5. converts that decision into an experiment, issue, ADR, or rejection.

The Council should optimize for **decision quality, speed of learning, user value, feasibility, and controlled risk**.

---

## 2. When to invoke the Council

Use the Council when a decision is material, ambiguous, difficult to reverse, expensive to get wrong, or likely to shape later work.

Typical triggers:

- new product or feature concepts,
- architecture or platform decisions,
- build-vs-buy decisions,
- adoption of external libraries, tools, APIs, or vendors,
- major scope changes,
- conflicting stakeholder or agent recommendations,
- unclear product-market assumptions,
- security, privacy, compliance, or operational concerns,
- prioritization decisions with meaningful opportunity cost,
- decisions that may create significant technical or product debt,
- escalations from a delivery or review loop.

Do **not** invoke the Council for routine, low-risk, easily reversible work when a normal PO decision is sufficient.

### Complexity Gate

Before invoking the Council, assess the decision on five dimensions:

| Dimension | Low | Medium | High |
|---|---|---|---|
| Impact | Local | Several components/users | Strategic/product-wide |
| Reversibility | Easy | Moderate | Expensive/difficult |
| Uncertainty | Known solution | Some unknowns | Major assumptions |
| Cost of error | Small | Noticeable | High |
| Cross-domain effects | Isolated | Several domains | Product/business/technical |

**Default rule:** invoke the Council when at least two dimensions are High, or when one High-risk dimension alone justifies deeper review.

---

## 3. Council modes

### QUICK
Use for medium-impact decisions where a lightweight challenge is enough.

- 3 council perspectives
- short independent analysis
- one synthesis
- concise output

### STANDARD
Default for substantial product decisions.

- 5 perspectives
- independent first pass
- peer challenge
- chairman synthesis
- explicit dissent and assumptions

### DEEP
Use for strategic, high-cost, security-sensitive, or hard-to-reverse decisions.

- 5+ perspectives where useful
- independent first pass
- adversarial review
- explicit scenario analysis
- evidence gaps and validation plan
- second synthesis/check before final recommendation

Do not choose DEEP merely because the topic is interesting. Use it when the expected value of better reasoning exceeds the additional time and compute cost.

---

## 4. Standard Council roles

The roles are perspectives, not job titles. They should reason independently during Stage 1.

### A. Customer & Problem Advocate
Focus:
- Is this a real user problem?
- Who benefits?
- What outcome improves?
- Are we solving the problem or merely implementing an idea?
- What is the smallest useful outcome?

### B. First-Principles Analyst
Focus:
- Which assumptions are being treated as facts?
- What must actually be true for this to work?
- Can the problem be simplified or reframed?
- Is there a cheaper or more direct solution?

### C. Contrarian / Red Team
Focus:
- Why might this fail?
- What are the hidden costs, failure modes, attack surfaces, dependencies, and second-order effects?
- What would make the recommendation look obviously wrong in hindsight?
- Which popular assumption should be challenged?

The Red Team must produce meaningful objections. It must not manufacture disagreement without evidence.

### D. Delivery & Feasibility Analyst
Focus:
- Can this realistically be built, integrated, operated, tested, and maintained?
- What dependencies and constraints exist?
- What is the likely implementation complexity?
- What can be prototyped instead of fully built?
- What would block delivery?

### E. Value & Prioritization Analyst
Focus:
- What is the expected value relative to effort and risk?
- What opportunity cost does this create?
- Is now the right time?
- What should be deferred, removed, or narrowed?
- What evidence would justify additional investment?

Optional specialist roles may replace or supplement a standard role when the decision clearly requires them, for example Security, Legal/Compliance, Data, UX, Finance, or Operations.

---

## 5. Council workflow

### Stage 0 — Frame the decision

Create a neutral decision brief containing only the information needed to evaluate the decision:

- decision/question,
- desired outcome,
- relevant constraints,
- known evidence,
- assumptions,
- alternatives already identified,
- deadline or urgency if relevant.

Do not bias the brief toward a preferred answer.

### Stage 1 — Independent analysis

Each council member evaluates the same brief independently.

Important rules:

- Members must not read the other members' Stage 1 answers first.
- Each member should state assumptions and uncertainty.
- Each member should distinguish evidence from inference.
- Each member should make a recommendation, not merely list observations.

Recommended member output:

1. Position
2. Strongest reasons
3. Main risks
4. Critical assumptions
5. Evidence missing
6. Recommendation
7. Confidence (0–100%)

### Stage 2 — Peer challenge

After independent answers exist, expose the analyses to the other members without emphasizing author identity.

Each reviewer should identify:

- the strongest argument from another perspective,
- the weakest assumption,
- overlooked risks or opportunities,
- contradictions,
- evidence that would change the decision.

The goal is not artificial consensus. Preserve legitimate disagreement.

### Stage 3 — Chairman synthesis

The Chairman acts as a Product Owner decision synthesizer.

The Chairman must:

- compare arguments rather than count votes,
- prefer evidence over confidence or verbosity,
- preserve important dissent,
- identify the decision's critical assumptions,
- choose one recommended course of action when possible,
- downgrade confidence when evidence is weak,
- propose a validation step when the decision should not yet be made permanently.

### Stage 4 — Convert reasoning into action

The Council is complete only when its output can drive work.

Depending on the result, create one of:

- **ACCEPT** — proceed to delivery,
- **EXPERIMENT** — validate a critical assumption first,
- **DEFER** — valuable but not justified now,
- **REJECT** — do not invest further under current assumptions,
- **ESCALATE** — requires a human or specialist decision.

---

## 6. Required final output

Use this structure unless the surrounding workflow requires a stricter format.

### PO Council Decision

**Decision:**  
One sentence describing the question that was decided.

**Verdict:** ACCEPT / EXPERIMENT / DEFER / REJECT / ESCALATE

**Recommendation:**  
The concrete recommended course of action.

**Why:**  
The strongest reasons supporting the recommendation.

**Strongest counterargument:**  
The most credible reason the recommendation may be wrong.

**Key assumptions:**
- assumption 1
- assumption 2

**Main risks:**
- risk — mitigation

**Dissent:**  
Material disagreement that should remain visible. Write `None material` if appropriate.

**Evidence gaps:**  
Information that would materially increase confidence.

**Confidence:** NN%

**Smallest validation / MVP:**  
The cheapest useful test of the critical assumptions.

**Success criteria:**
- measurable criterion 1
- measurable criterion 2

**Acceptance criteria / delivery guardrails:**
- criterion 1
- criterion 2

**Next action:**  
One concrete next step with a clear output.

---

## 7. Product Owner rules

The Council must follow these rules:

1. **Problem before solution.** Do not accept a feature merely because implementation is possible.
2. **Independent reasoning before consensus.** Avoid anchoring by separating the first analyses.
3. **Evidence over authority.** A persuasive role does not outrank better evidence.
4. **Preserve dissent.** Minority objections that affect risk or validation must remain visible.
5. **Prefer reversible experiments.** When uncertainty is high, buy information before committing heavily.
6. **Make trade-offs explicit.** State what is not being done and what opportunity cost exists when relevant.
7. **Avoid analysis theater.** Do not invoke the Council when the answer is already low-risk and obvious.
8. **Finish with action.** A Council output without a next step is incomplete.
9. **Separate discovery from delivery.** The Council decides what should be learned or built and why; delivery workflows decide how to implement it.
10. **Escalate honestly.** Do not fabricate certainty when a human, specialist, legal review, or unavailable evidence is required.

---

## 8. Privacy and context hygiene

This skill is designed to be reusable across public and private environments.

- Use only the minimum context required for the decision.
- Do not copy credentials, secrets, access tokens, private keys, personal identifiers, private customer data, or confidential business material into a public artifact.
- Redact or generalize sensitive examples.
- Public Council templates should remain project-neutral.
- Project-specific context belongs in the consuming project's private layer, not in this reusable skill.

---

## 9. Suggested invocation phrases

Examples:

- `Run PO Council on this idea.`
- `Council this decision.`
- `Pressure-test this as a Product Owner.`
- `Use the PO Council before we create an issue.`
- `Run a QUICK Council.`
- `Run a STANDARD Council and turn the result into acceptance criteria.`
- `Run a DEEP Council and preserve dissent.`

An assistant may also invoke the Council automatically when the Complexity Gate is met, if the surrounding system explicitly permits automatic invocation.

---

## 10. Integration with agentic workflows

Recommended position in a delivery system:

```text
Idea / Decision
      |
      v
PO Intake
      |
      v
Complexity Gate
   |        |
   |        +---- material / uncertain ----> PO Council
   |                                      |
   |                                      v
   |                               PO Decision Artifact
   |                                      |
   +--------------- routine --------------+
                                          |
                                          v
                                  Delivery / Dev Loop
                                          |
                                  Test / Review / Gate
                                          |
                                  Learning / Outcome
```

Useful downstream artifacts include:

- GitHub issue,
- product backlog item,
- ADR / decision record,
- experiment brief,
- spike,
- rejection/defer record,
- risk entry.

For important decisions, compare the actual outcome with the original assumptions later. This turns the Council from a one-time reasoning pattern into a learning system.

---

## 11. Minimal pseudocode

```text
function po_council(decision):
    brief = frame_neutrally(decision)
    score = complexity_gate(brief)

    if score is low:
        return normal_po_decision(brief)

    mode = choose_mode(score)
    analyses = run_independent_roles(brief, mode)
    challenges = peer_review(analyses)
    decision = chairman_synthesis(brief, analyses, challenges)
    action = convert_to_po_action(decision)

    return decision + action
```

---

## 12. Definition of Done

A Council run is done when:

- the decision is clearly framed,
- independent perspectives were considered,
- material disagreement is visible,
- critical assumptions and evidence gaps are explicit,
- one verdict is produced,
- confidence is stated,
- the smallest sensible validation or implementation step is defined,
- success or acceptance criteria exist where applicable,
- the next action is unambiguous.
