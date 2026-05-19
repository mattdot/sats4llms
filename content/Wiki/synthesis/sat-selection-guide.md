---
type: synthesis
tags: [wiki/synthesis]
date_updated: 2026-05-19
query: "Given a problem type or bias risk, which SAT should I apply?"
sources_used: ["[[sources/tradecraft-primer-2009|CIA Tradecraft Primer (2009)]]", "[[sources/roberts-llm-sats-ftw-2025|Roberts: LLM SATs FTW (2025)]]"]
confidence: high
---

# SAT Selection Guide

**Query:** Given a problem type, bias risk, or point in the analytic process — which SAT(s) should I apply?

*Use this page to select the right technique. For how techniques work together in sequence, see [[synthesis/sat-pipeline|SAT Pipeline]]. For the full cross-reference, see [[synthesis/bias-sat-matrix|Bias x SAT Matrix]].*

---

## Select by: Where Are You in the Process?

| Stage | Problem | Reach For |
|-------|---------|-----------|
| **Before you start** | Need to scope what questions to ask | [[concepts/starbursting\|Starbursting]] |
| **Before you start** | Need to generate candidate explanations | [[concepts/brainstorming\|Brainstorming]] |
| **During analysis** | Have a preferred explanation and want to test it rigorously | [[concepts/analysis-of-competing-hypotheses\|ACH]] |
| **During analysis** | Need to surface hidden assumptions in the current line | [[concepts/key-assumptions-check\|Key Assumptions Check]] |
| **During analysis** | Need to evaluate source reliability | [[concepts/quality-of-information-check\|Quality of Information Check]] |
| **During analysis** | Need an adversary's perspective | [[concepts/red-team-analysis\|Red Team Analysis]] |
| **During analysis** | Need to monitor for changing conditions | [[concepts/indicators-or-signposts-of-change\|Indicators or Signposts of Change]] |
| **Challenging a conclusion** | A consensus has formed; want to stress-test it | [[concepts/devils-advocacy\|Devil's Advocacy]] |
| **Challenging a conclusion** | Need truly independent views (not just devil's advocate) | [[concepts/team-a-team-b\|Team A/Team B]] |
| **Planning / forecasting** | Need to think about uncertain futures | [[concepts/alternative-futures-analysis\|Alternative Futures Analysis]] |
| **Planning / forecasting** | Need to consider low-probability but high-impact events | [[concepts/high-impact-low-probability-analysis\|High-Impact/Low-Probability Analysis]] |
| **Post-analysis** | Need to stress-test a finished product | [[concepts/what-if-analysis\|What If? Analysis]], [[concepts/key-assumptions-check\|Key Assumptions Check]] |

---

## Select by: Which Bias Are You Worried About?

| Primary Bias Risk | Best Single SAT | Supporting SATs |
|------------------|-----------------|----------------|
| [[concepts/confirmation-bias\|Confirmation Bias]] | [[concepts/analysis-of-competing-hypotheses\|ACH]] | [[concepts/devils-advocacy\|Devil's Advocacy]], [[concepts/key-assumptions-check\|Key Assumptions Check]] |
| [[concepts/sycophancy\|Sycophancy]] (LLM) | [[concepts/devils-advocacy\|Devil's Advocacy]] | [[concepts/team-a-team-b\|Team A/Team B]], [[concepts/analysis-of-competing-hypotheses\|ACH]] |
| [[concepts/hallucination\|Hallucination]] (LLM) | [[concepts/quality-of-information-check\|Quality of Information Check]] | [[concepts/key-assumptions-check\|Key Assumptions Check]], [[concepts/devils-advocacy\|Devil's Advocacy]] |
| [[concepts/anchoring-bias\|Anchoring Bias]] | [[concepts/key-assumptions-check\|Key Assumptions Check]] | Generate-before-evaluate separation, [[concepts/starbursting\|Starbursting]] |
| [[concepts/groupthink\|Groupthink]] | [[concepts/team-a-team-b\|Team A/Team B]] | [[concepts/devils-advocacy\|Devil's Advocacy]], independent parallel analysis |
| [[concepts/overconfidence-bias\|Overconfidence Bias]] | [[concepts/what-if-analysis\|What If? Analysis]] | [[concepts/key-assumptions-check\|Key Assumptions Check]], [[concepts/high-impact-low-probability-analysis\|HILP]] |
| [[concepts/mirror-imaging\|Mirror Imaging]] | [[concepts/red-team-analysis\|Red Team Analysis]] | [[concepts/outside-in-thinking\|Outside-In Thinking]] |
| [[concepts/status-quo-bias\|Status Quo Bias]] | [[concepts/alternative-futures-analysis\|Alternative Futures Analysis]] | [[concepts/what-if-analysis\|What If? Analysis]], [[concepts/devils-advocacy\|Devil's Advocacy]] |
| [[concepts/availability-heuristic\|Availability Heuristic]] | [[concepts/brainstorming\|Brainstorming]] | [[concepts/alternative-futures-analysis\|Alternative Futures Analysis]], [[concepts/analysis-of-competing-hypotheses\|ACH]] |
| [[concepts/motivated-reasoning\|Motivated Reasoning]] | [[concepts/analysis-of-competing-hypotheses\|ACH]] | [[concepts/key-assumptions-check\|Key Assumptions Check]], [[concepts/devils-advocacy\|Devil's Advocacy]] |
| [[concepts/framing-effect\|Framing Effect]] | [[concepts/outside-in-thinking\|Outside-In Thinking]] | [[concepts/starbursting\|Starbursting]], [[concepts/red-team-analysis\|Red Team Analysis]] |
| [[concepts/hindsight-bias\|Hindsight Bias]] | [[concepts/indicators-or-signposts-of-change\|Indicators or Signposts of Change]] | [[concepts/what-if-analysis\|What If? Analysis]] |

---

## Select by: Problem Type

### Attribution / "Who did this?"
Primary risk: [[concepts/confirmation-bias|Confirmation Bias]], [[concepts/mirror-imaging|Mirror Imaging]], [[concepts/anchoring-bias|Anchoring Bias]]

**Recommended sequence:**
1. [[concepts/brainstorming|Brainstorming]] — generate all possible actors
2. [[concepts/analysis-of-competing-hypotheses|ACH]] — evaluate evidence against all actors simultaneously
3. [[concepts/red-team-analysis|Red Team Analysis]] — would the attributed actor actually behave this way?

---

### Forecasting / "What will happen?"
Primary risk: [[concepts/status-quo-bias|Status Quo Bias]], [[concepts/overconfidence-bias|Overconfidence Bias]], [[concepts/availability-heuristic|Availability Heuristic]]

**Recommended sequence:**
1. [[concepts/alternative-futures-analysis|Alternative Futures Analysis]] — develop multiple scenarios from key uncertainties
2. [[concepts/high-impact-low-probability-analysis|High-Impact/Low-Probability Analysis]] — explicitly address the tail
3. [[concepts/indicators-or-signposts-of-change|Indicators or Signposts of Change]] — define observable signals for each scenario

---

### Reviewing a finished product / "Is this analysis sound?"
Primary risk: [[concepts/confirmation-bias|Confirmation Bias]], [[concepts/anchoring-bias|Anchoring Bias]], [[concepts/hallucination|Hallucination]] (LLM)

**Recommended sequence:**
1. [[concepts/key-assumptions-check|Key Assumptions Check]] — surface all load-bearing assumptions
2. [[concepts/devils-advocacy|Devil's Advocacy]] — build the best case against the conclusion
3. [[concepts/quality-of-information-check|Quality of Information Check]] — audit sources and evidence quality

---

### Planning / "What could go wrong?"
Primary risk: [[concepts/overconfidence-bias|Overconfidence Bias]], [[concepts/status-quo-bias|Status Quo Bias]], [[concepts/motivated-reasoning|Motivated Reasoning]]

**Recommended sequence:**
1. [[concepts/what-if-analysis|What If? Analysis]] — assume it has already failed; work backwards
2. [[concepts/high-impact-low-probability-analysis|High-Impact/Low-Probability Analysis]] — enumerate the tail risks
3. [[concepts/key-assumptions-check|Key Assumptions Check]] — identify which assumptions, if wrong, cause the plan to fail

---

### Adversarial / "What will an opponent do?"
Primary risk: [[concepts/mirror-imaging|Mirror Imaging]], [[concepts/framing-effect|Framing Effect]], [[concepts/overconfidence-bias|Overconfidence Bias]]

**Recommended sequence:**
1. [[concepts/outside-in-thinking|Outside-In Thinking]] — force analysis from the adversary's external constraints
2. [[concepts/red-team-analysis|Red Team Analysis]] — adopt adversary persona and evaluate the plan from their perspective
3. [[concepts/what-if-analysis|What If? Analysis]] — assume the adversary succeeded; reconstruct how

---

### Multi-agent deliberation / "How do we prevent echo chambers?"
Primary risk: [[concepts/groupthink|Groupthink]], [[concepts/sycophancy|Sycophancy]], [[concepts/confirmation-bias|Confirmation Bias]]

**Recommended pattern:**
- Run agents independently before any agent sees others' outputs ([[concepts/team-a-team-b|Team A/Team B]] pattern)
- Assign one agent an explicit adversarial critique role ([[concepts/devils-advocacy|Devil's Advocacy]] pattern)
- Use different system prompts or models to prevent synchronization
- See [[synthesis/sat-pipeline|SAT Pipeline]] for the full multi-agent architecture

---

## Minimum Viable Intervention

When you can only apply *one* SAT and bias risk is general, these deliver the broadest coverage:

| Priority | SAT | Biases covered | LLM implementation complexity |
|----------|-----|---------------|-------------------------------|
| 1st | [[concepts/key-assumptions-check\|Key Assumptions Check]] | Anchoring, Confirmation, Overconfidence, Motivated Reasoning, Status Quo | Single prompt; zero-shot |
| 2nd | [[concepts/devils-advocacy\|Devil's Advocacy]] | Confirmation, Groupthink, Motivated Reasoning, Sycophancy | Single adversarial prompt; or two-agent |
| 3rd | [[concepts/analysis-of-competing-hypotheses\|ACH]] | Confirmation, Anchoring, Availability, Motivated Reasoning, Groupthink | Multi-step sequential (see [[sources/roberts-llm-sats-ftw-2025\|Roberts: LLM SATs FTW (2025)]]) |

---

## See Also

[[synthesis/sat-pipeline|SAT Pipeline]] | [[synthesis/bias-sat-matrix|Bias x SAT Matrix]] | [[synthesis/sats-for-llm-agents|SATs for LLM Agents]]
