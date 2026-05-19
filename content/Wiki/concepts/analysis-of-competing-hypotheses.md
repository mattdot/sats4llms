---
type: concept
tags: [wiki/concept, wiki/sat]
date_updated: 2026-05-19
confidence: high
source_count: 2
sat_category: diagnostic
---

# Analysis of Competing Hypotheses (ACH)

A [[concepts/structured-analytic-techniques|SAT]] that identifies all alternative explanations (hypotheses) and evaluates evidence to *disconfirm* rather than confirm them. The most rigorous diagnostic technique.

---

## Purpose

Overcome three common analytic mistakes:
1. Undue influence of a first impression based on incomplete data or existing analytic line
2. Failure to generate a full set of alternative hypotheses at project outset
3. Relying on evidence that *supports* the preferred hypothesis but is also consistent with other explanations

---

## When to Use

- When there is a large amount of data to absorb and evaluate
- Most effective with a small team (members challenge each other's evidence evaluation)
- Controversial issues requiring a clear audit trail
- When considering the possibility of denial and deception
- Initial matrix can be built in a day or less; data reassembly may require more time

---

## Method (8 Steps)

1. **Brainstorm** all possible hypotheses with analysts of different perspectives
2. **List** all significant evidence and arguments relevant to all hypotheses
3. **Build a matrix** — hypotheses across the top, evidence down the side; rate each: **C** (consistent), **I** (inconsistent), **N** (not applicable/neutral)
4. **Refine** — reconsider hypotheses; add new ones; re-examine information
5. **Focus on disproving** — tally inconsistency scores; weakest explanations eliminated first
6. **Sensitivity analysis** — if a few critical pieces of evidence proved wrong or deceptive, how would that change results?
7. **Ask what's missing** — what evidence *would* be expected if a given hypothesis were true? Is denial/deception possible?
8. **Report all conclusions** — including weaker hypotheses that should still be monitored

**Diagnostic value of evidence:** Evidence consistent with *only one* hypothesis is most valuable. Evidence consistent with all hypotheses has low diagnostic value.

---

## Example: Tokyo Sarin Attack (March 1995)

Four hypotheses: kooky cult (H1), terrorist group (H2), political movement (H3), criminal group (H4)

| Evidence | Weight | H1: Cult | H2: Terror | H3: Political | H4: Criminal |
|---------|--------|---------|-----------|-------------|------------|
| Attacks on journalists | MEDIUM | I | N | I | I |
| Religious affiliation | MEDIUM | C | I | I | I |
| Established party | MEDIUM | N | N | C | I |
| Blind leader Matsumoto | MEDIUM | C | C | C | C |
| **Inconsistency Score** | | -1.0 | -1.0 | -2.0 | -3.0 |

Result: criminal group hypothesis most strongly disconfirmed; terrorist group hypothesis most consistent.

---

## Biases Primarily Controlled

| Bias | How this technique counters it |
|------|-------------------------------|
| [[concepts/confirmation-bias\|Confirmation Bias]] | Disconfirmation focus is the structural core — you must disprove hypotheses, you cannot simply confirm a preferred one |
| [[concepts/anchoring-bias\|Anchoring Bias]] | Building all hypotheses simultaneously before evaluating evidence prevents any single hypothesis from becoming an anchor |
| [[concepts/availability-heuristic\|Availability Heuristic]] | Requires listing *all* hypotheses, including ones that don't readily come to mind; the matrix forces equal treatment |
| [[concepts/motivated-reasoning\|Motivated Reasoning]] | The matrix structure makes it structurally difficult to reach a preferred conclusion through selective evidence weighting |
| [[concepts/groupthink\|Groupthink]] | Most effective with a small team; team members challenge each other's evidence ratings across all hypotheses |

---

## Applied in Cybersecurity

- **Threat Intelligence**: ensures all potential threat actors, motivations, and capabilities are rigorously evaluated ([[sources/riley-sats-cybersecurity-2024|Riley: SATs in Cybersecurity (2024)]])
- **Forensic Investigators**: considers all explanations for evidence, avoiding [[concepts/confirmation-bias|Confirmation bias]]
- **Risk Analysts**: evaluates likelihood of diverse threat scenarios

---

## LLM Implementation (per [[sources/roberts-llm-sats-ftw-2025|Roberts: LLM SATs FTW (2025)]])

[[entities/scott-roberts|Scott Roberts]] found that ACH **requires multi-step sequential LLM queries** — a single zero-shot prompt fails ACH because the task is fundamentally evaluative and depends on hypotheses being generated before evidence can be evaluated. Roberts' working implementation:

1. **Query 1:** LLM generates competing hypotheses for the analytic question
2. **Query 2–N:** For each hypothesis, a separate query generates evidence for and against
3. **Query 2–N+M:** For each hypothesis-evidence pair, a separate query scores it on -5 to +5 scale
4. **Post-processing:** Scores totalled per hypothesis; results exported as CSV
5. **Human step:** Analyst reviews CSV, adds missing evidence, adjusts scores, makes final call

> *"ACH is a complex SAT that takes teams hours or even days to complete... many teams of analysts struggle with it."* — Roberts

**Architecture:** Streamlit + GPT-4 + LangChain + Pydantic (structured output)  
Live app: https://sat-ach.streamlit.app/ | Code: https://github.com/sroberts/talk-llm-sats-ftw-code/blob/main/experiment-2-ach.py

**⚠ Warning:** Any single-prompt ACH implementation is a known failure mode — hypothesis generation primes the model before evidence evaluation, defeating the disconfirmation structure.

---

## Sources

- [[sources/tradecraft-primer-2009|CIA Tradecraft Primer (2009)]] (pp. 14–16)
- [[sources/riley-sats-cybersecurity-2024|Riley: SATs in Cybersecurity (2024)]]
- [[sources/roberts-llm-sats-ftw-2025|Roberts: LLM SATs FTW (2025)]]
