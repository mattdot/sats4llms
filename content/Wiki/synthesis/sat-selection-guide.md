---
type: synthesis
tags: [wiki/synthesis]
date_updated: 2026-05-19
query: "Given a problem type or bias risk, which SAT should I apply?"
sources_used: ["[[Wiki/sources/tradecraft-primer-2009|CIA Tradecraft Primer (2009)]]", "[[Wiki/sources/roberts-llm-sats-ftw-2025|Roberts: LLM SATs FTW (2025)]]"]
confidence: high
---

# SAT Selection Guide

**Query:** Given a problem type, bias risk, or point in the analytic process — which SAT(s) should I apply?

*Use this page to select the right technique. For how techniques work together in sequence, see [[Wiki/synthesis/sat-pipeline|SAT Pipeline]]. For the full cross-reference, see [[Wiki/synthesis/bias-sat-matrix|Bias x SAT Matrix]].*

---

## Select by: Where Are You in the Process?

| Stage | Problem | Reach For |
|-------|---------|-----------|
| **Before you start** | Need to scope what questions to ask | [[Wiki/concepts/starbursting\|Starbursting]] |
| **Before you start** | Need to generate candidate explanations | [[Wiki/concepts/brainstorming\|Brainstorming]] |
| **During analysis** | Have a preferred explanation and want to test it rigorously | [[Wiki/concepts/analysis-of-competing-hypotheses\|ACH]] |
| **During analysis** | Need to surface hidden assumptions in the current line | [[Wiki/concepts/key-assumptions-check\|Key Assumptions Check]] |
| **During analysis** | Need to evaluate source reliability | [[Wiki/concepts/quality-of-information-check\|Quality of Information Check]] |
| **During analysis** | Need an adversary's perspective | [[Wiki/concepts/red-team-analysis\|Red Team Analysis]] |
| **During analysis** | Need to monitor for changing conditions | [[Wiki/concepts/indicators-or-signposts-of-change\|Indicators or Signposts of Change]] |
| **Challenging a conclusion** | A consensus has formed; want to stress-test it | [[Wiki/concepts/devils-advocacy\|Devil's Advocacy]] |
| **Challenging a conclusion** | Need truly independent views (not just devil's advocate) | [[Wiki/concepts/team-a-team-b\|Team A/Team B]] |
| **Planning / forecasting** | Need to think about uncertain futures | [[Wiki/concepts/alternative-futures-analysis\|Alternative Futures Analysis]] |
| **Planning / forecasting** | Need to consider low-probability but high-impact events | [[Wiki/concepts/high-impact-low-probability-analysis\|High-Impact/Low-Probability Analysis]] |
| **Post-analysis** | Need to stress-test a finished product | [[Wiki/concepts/what-if-analysis\|What If? Analysis]], [[Wiki/concepts/key-assumptions-check\|Key Assumptions Check]] |

---

## Select by: Which Bias Are You Worried About?

| Primary Bias Risk | Best Single SAT | Supporting SATs |
|------------------|-----------------|----------------|
| [[Wiki/concepts/confirmation-bias\|Confirmation Bias]] | [[Wiki/concepts/analysis-of-competing-hypotheses\|ACH]] | [[Wiki/concepts/devils-advocacy\|Devil's Advocacy]], [[Wiki/concepts/key-assumptions-check\|Key Assumptions Check]] |
| [[Wiki/concepts/sycophancy\|Sycophancy]] (LLM) | [[Wiki/concepts/devils-advocacy\|Devil's Advocacy]] | [[Wiki/concepts/team-a-team-b\|Team A/Team B]], [[Wiki/concepts/analysis-of-competing-hypotheses\|ACH]] |
| [[Wiki/concepts/hallucination\|Hallucination]] (LLM) | [[Wiki/concepts/quality-of-information-check\|Quality of Information Check]] | [[Wiki/concepts/key-assumptions-check\|Key Assumptions Check]], [[Wiki/concepts/devils-advocacy\|Devil's Advocacy]] |
| [[Wiki/concepts/anchoring-bias\|Anchoring Bias]] | [[Wiki/concepts/key-assumptions-check\|Key Assumptions Check]] | Generate-before-evaluate separation, [[Wiki/concepts/starbursting\|Starbursting]] |
| [[Wiki/concepts/groupthink\|Groupthink]] | [[Wiki/concepts/team-a-team-b\|Team A/Team B]] | [[Wiki/concepts/devils-advocacy\|Devil's Advocacy]], independent parallel analysis |
| [[Wiki/concepts/overconfidence-bias\|Overconfidence Bias]] | [[Wiki/concepts/what-if-analysis\|What If? Analysis]] | [[Wiki/concepts/key-assumptions-check\|Key Assumptions Check]], [[Wiki/concepts/high-impact-low-probability-analysis\|HILP]] |
| [[Wiki/concepts/mirror-imaging\|Mirror Imaging]] | [[Wiki/concepts/red-team-analysis\|Red Team Analysis]] | [[Wiki/concepts/outside-in-thinking\|Outside-In Thinking]] |
| [[Wiki/concepts/status-quo-bias\|Status Quo Bias]] | [[Wiki/concepts/alternative-futures-analysis\|Alternative Futures Analysis]] | [[Wiki/concepts/what-if-analysis\|What If? Analysis]], [[Wiki/concepts/devils-advocacy\|Devil's Advocacy]] |
| [[Wiki/concepts/availability-heuristic\|Availability Heuristic]] | [[Wiki/concepts/brainstorming\|Brainstorming]] | [[Wiki/concepts/alternative-futures-analysis\|Alternative Futures Analysis]], [[Wiki/concepts/analysis-of-competing-hypotheses\|ACH]] |
| [[Wiki/concepts/motivated-reasoning\|Motivated Reasoning]] | [[Wiki/concepts/analysis-of-competing-hypotheses\|ACH]] | [[Wiki/concepts/key-assumptions-check\|Key Assumptions Check]], [[Wiki/concepts/devils-advocacy\|Devil's Advocacy]] |
| [[Wiki/concepts/framing-effect\|Framing Effect]] | [[Wiki/concepts/outside-in-thinking\|Outside-In Thinking]] | [[Wiki/concepts/starbursting\|Starbursting]], [[Wiki/concepts/red-team-analysis\|Red Team Analysis]] |
| [[Wiki/concepts/hindsight-bias\|Hindsight Bias]] | [[Wiki/concepts/indicators-or-signposts-of-change\|Indicators or Signposts of Change]] | [[Wiki/concepts/what-if-analysis\|What If? Analysis]] |

---

## Select by: Problem Type

### Attribution / "Who did this?"
Primary risk: [[Wiki/concepts/confirmation-bias|Confirmation Bias]], [[Wiki/concepts/mirror-imaging|Mirror Imaging]], [[Wiki/concepts/anchoring-bias|Anchoring Bias]]

**Recommended sequence:**
1. [[Wiki/concepts/brainstorming|Brainstorming]] — generate all possible actors
2. [[Wiki/concepts/analysis-of-competing-hypotheses|ACH]] — evaluate evidence against all actors simultaneously
3. [[Wiki/concepts/red-team-analysis|Red Team Analysis]] — would the attributed actor actually behave this way?

---

### Forecasting / "What will happen?"
Primary risk: [[Wiki/concepts/status-quo-bias|Status Quo Bias]], [[Wiki/concepts/overconfidence-bias|Overconfidence Bias]], [[Wiki/concepts/availability-heuristic|Availability Heuristic]]

**Recommended sequence:**
1. [[Wiki/concepts/alternative-futures-analysis|Alternative Futures Analysis]] — develop multiple scenarios from key uncertainties
2. [[Wiki/concepts/high-impact-low-probability-analysis|High-Impact/Low-Probability Analysis]] — explicitly address the tail
3. [[Wiki/concepts/indicators-or-signposts-of-change|Indicators or Signposts of Change]] — define observable signals for each scenario

---

### Reviewing a finished product / "Is this analysis sound?"
Primary risk: [[Wiki/concepts/confirmation-bias|Confirmation Bias]], [[Wiki/concepts/anchoring-bias|Anchoring Bias]], [[Wiki/concepts/hallucination|Hallucination]] (LLM)

**Recommended sequence:**
1. [[Wiki/concepts/key-assumptions-check|Key Assumptions Check]] — surface all load-bearing assumptions
2. [[Wiki/concepts/devils-advocacy|Devil's Advocacy]] — build the best case against the conclusion
3. [[Wiki/concepts/quality-of-information-check|Quality of Information Check]] — audit sources and evidence quality

---

### Planning / "What could go wrong?"
Primary risk: [[Wiki/concepts/overconfidence-bias|Overconfidence Bias]], [[Wiki/concepts/status-quo-bias|Status Quo Bias]], [[Wiki/concepts/motivated-reasoning|Motivated Reasoning]]

**Recommended sequence:**
1. [[Wiki/concepts/what-if-analysis|What If? Analysis]] — assume it has already failed; work backwards
2. [[Wiki/concepts/high-impact-low-probability-analysis|High-Impact/Low-Probability Analysis]] — enumerate the tail risks
3. [[Wiki/concepts/key-assumptions-check|Key Assumptions Check]] — identify which assumptions, if wrong, cause the plan to fail

---

### Adversarial / "What will an opponent do?"
Primary risk: [[Wiki/concepts/mirror-imaging|Mirror Imaging]], [[Wiki/concepts/framing-effect|Framing Effect]], [[Wiki/concepts/overconfidence-bias|Overconfidence Bias]]

**Recommended sequence:**
1. [[Wiki/concepts/outside-in-thinking|Outside-In Thinking]] — force analysis from the adversary's external constraints
2. [[Wiki/concepts/red-team-analysis|Red Team Analysis]] — adopt adversary persona and evaluate the plan from their perspective
3. [[Wiki/concepts/what-if-analysis|What If? Analysis]] — assume the adversary succeeded; reconstruct how

---

### Multi-agent deliberation / "How do we prevent echo chambers?"
Primary risk: [[Wiki/concepts/groupthink|Groupthink]], [[Wiki/concepts/sycophancy|Sycophancy]], [[Wiki/concepts/confirmation-bias|Confirmation Bias]]

**Recommended pattern:**
- Run agents independently before any agent sees others' outputs ([[Wiki/concepts/team-a-team-b|Team A/Team B]] pattern)
- Assign one agent an explicit adversarial critique role ([[Wiki/concepts/devils-advocacy|Devil's Advocacy]] pattern)
- Use different system prompts or models to prevent synchronization
- See [[Wiki/synthesis/sat-pipeline|SAT Pipeline]] for the full multi-agent architecture

---

## Minimum Viable Intervention

When you can only apply *one* SAT and bias risk is general, these deliver the broadest coverage:

| Priority | SAT | Biases covered | LLM implementation complexity |
|----------|-----|---------------|-------------------------------|
| 1st | [[Wiki/concepts/key-assumptions-check\|Key Assumptions Check]] | Anchoring, Confirmation, Overconfidence, Motivated Reasoning, Status Quo | Single prompt; zero-shot |
| 2nd | [[Wiki/concepts/devils-advocacy\|Devil's Advocacy]] | Confirmation, Groupthink, Motivated Reasoning, Sycophancy | Single adversarial prompt; or two-agent |
| 3rd | [[Wiki/concepts/analysis-of-competing-hypotheses\|ACH]] | Confirmation, Anchoring, Availability, Motivated Reasoning, Groupthink | Multi-step sequential (see [[Wiki/sources/roberts-llm-sats-ftw-2025\|Roberts: LLM SATs FTW (2025)]]) |

---

## See Also

[[Wiki/synthesis/sat-pipeline|SAT Pipeline]] | [[Wiki/synthesis/bias-sat-matrix|Bias x SAT Matrix]] | [[Wiki/synthesis/sats-for-llm-agents|SATs for LLM Agents]]
