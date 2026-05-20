---
type: source-summary
tags: [wiki/source]
date_updated: 2026-05-20
source_file: "https://github.com/suprathermal/ACH-Grounding"
source_date: 2024-01-01
author: "suprathermal (GitHub)"
topics: [ACH, RAG, grounding, hallucination-mitigation, hybrid-symbolic-LLM, implementation]
---

# ACH-Grounding (suprathermal, GitHub)

> *"LLMs hallucinate. Various strategies exist to cope with that. This project implements one of them."*

A working open-source Python implementation of [[concepts/analysis-of-competing-hypotheses|Analysis of Competing Hypotheses (ACH)]] used as a **grounding mechanism** for LLM output. Repo: https://github.com/suprathermal/ACH-Grounding

---

## Core Claim

LLM statements should be organized as a **matrix of evidence × hypotheses**, with each cell scored for the *degree* and *direction* of support. The LLM only fills the matrix cells; the synthesis (ranking hypotheses, computing confidence) is performed by **classical, deterministic code**.

This separation is the central design pattern: LLMs do focused per-cell judgments where they are strong; combinatorial reasoning over the full matrix is delegated to algorithms where they are reliable.

---

## Why This Architecture

[[entities/suprathermal|suprathermal]] cites two papers asserting that LLM hallucinations on combinatorially complex problems are **provably inevitable** and cannot be arbitrarily reduced:

- arXiv:2401.11817 — Hallucination is inevitable (Xu et al.)
- arXiv:2508.01781 — Follow-up on practical bounds

Therefore, for any required degree of analytic assurance, the combinatorial step **must** be moved out of the LLM. The ACH matrix is a structural fit because each cell is a local, low-context judgment.

---

## Claimed Benefits

1. **Stability against rogue/wrong observations** — outliers don't dominate
2. **Stability against [[concepts/confirmation-bias|confirmation bias]]** — every evidence is checked against every hypothesis, so no single hypothesis becomes the anchor for evidence interpretation
3. **Forced exhaustive cross-referencing** — "interrogating all situational knowledge out of the LLM"
4. **External grounding** — pre-existing verified hypotheses or evidence can be injected via `ExtraH` / `ExtraE` config

---

## Process

1. Take pre-existing hypotheses and evidence from the user (or have the LLM generate them)
2. Estimate API cost; ask for approval if > $1
3. (Optional) Generate additional hypotheses about the question/event
4. Collect supporting and contradicting evidence
5. **Cross-validate each hypothesis against each evidence** to build a support matrix
6. **Statistical analysis** of the resulting matrix → likelihood scores per hypothesis
7. Output: per-hypothesis likelihood scores printed to screen and saved as CSV in time-stamped folder

Internal RAG: the system feeds previously generated hypotheses and evidence back as context to subsequent calls, enabling iterative coherent build-up. The author calls this "the most rudimentary form of RAG."

---

## Cost Model

The algorithm consumes **O((|Evidence| + |Hypotheses|)²)** tokens. The author is explicit that this is unsuitable for massive datasets — it is a "few hypotheses, few precious pieces of evidence, everything highly uncertain" tool.

This matches the human ACH use case: ACH is intended for hard, ambiguous, high-stakes questions, not for mass-data triage.

---

## Hybrid-Workflow Support

Designed to accept input from:

- **Humans** — analysts provide hypotheses and evidence via config files
- **LLMs** — system autonomously generates hypotheses and evidence
- **Hybrid** — analyst provides verified seeds; LLM extends; matrix evaluation runs over the union

The `ExtraH` and `ExtraE` parameters are the explicit hook for grounding: known-true facts and expert-asserted hypotheses are injected as constraints the LLM cannot override.

---

## Self-Stated Scope

**This is:** a working personal/small-team tool, an implementation of basic ACH, a practical demo of LLM grounding the author believes is novel.

**This is not:** an enterprise-grade tool, a solution for massive data, a clean prompting example, a production-ready RAG framework.

---

## Significance

This is a **concrete, working artifact** for [[synthesis/hypotheses/h1-ach-confirmation-bias|H1 (ACH reduces confirmation bias in LLM evidence evaluation)]]. Independent of [[sources/roberts-llm-sats-ftw-2025|Roberts (2025)]], it confirms the same architectural conclusion through a different design:

| Roberts | suprathermal |
|---|---|
| Multi-step sequential LLM calls (hypotheses → evidence → per-cell scoring) | Multi-step sequential LLM calls (hypotheses → evidence → per-cell scoring) |
| Single-prompt ACH is an anti-pattern | Single-prompt ACH is implicitly rejected (cell-by-cell scoring) |
| LLM does scoring; analyst totals | LLM fills matrix; **classical algorithms** total |
| Streamlit + GPT-4 + LangChain + Pydantic | Python, configurable, CSV output |

Both designs converge on the same principle: **LLMs do local judgments; structure is enforced outside the LLM.** This convergence is empirical evidence for the design pattern.

---

## Connections

- [[concepts/analysis-of-competing-hypotheses|ACH]] — direct implementation
- [[concepts/confirmation-bias|Confirmation Bias]] — the bias the matrix structurally counters
- [[concepts/hallucination|Hallucination]] — the failure mode this design mitigates
- [[synthesis/hypotheses/h1-ach-confirmation-bias|H1]] — corroborating implementation
- [[sources/roberts-llm-sats-ftw-2025|Roberts (2025)]] — independent convergent implementation
- [[sources/huang-hallucination-survey-2023|Huang et al. (2023)]] — RAG as hallucination mitigation taxonomy

---

## Cited External Work

- [Wikipedia: Analysis of competing hypotheses](https://en.wikipedia.org/wiki/Analysis_of_competing_hypotheses)
- [arXiv:2401.11817](https://arxiv.org/abs/2401.11817) — Hallucination inevitability
- [arXiv:2508.01781](https://arxiv.org/pdf/2508.01781) — Follow-up bounds
