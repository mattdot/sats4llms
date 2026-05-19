---
type: synthesis
tags: [wiki/synthesis]
date_updated: 2026-05-19
query: "How can Structured Analytic Techniques be adapted to control cognitive biases in LLM-based agentic systems?"
sources_used: ["[[Wiki/sources/tradecraft-primer-2009|CIA Tradecraft Primer (2009)]]", "[[Wiki/sources/riley-sats-cybersecurity-2024|Riley: SATs in Cybersecurity (2024)]]", "[[Wiki/sources/roberts-llm-sats-ftw-2025|Roberts: LLM SATs FTW (2025)]]"]
confidence: medium
---

# SATs for LLM Agentic Systems

**Query:** How can [[Wiki/concepts/structured-analytic-techniques|Structured Analytic Techniques]] be adapted to control [[Wiki/concepts/cognitive-bias|cognitive biases]] in LLM-based agentic systems?

*Synthesis page — interpretation and extrapolation. Factual claims about LLM behavior are drawn from the field of LLM alignment and evaluation research; SAT descriptions are drawn from [[Wiki/sources/tradecraft-primer-2009|CIA Tradecraft Primer (2009)]].*

---

## The Core Analogy

The problem SATs were designed to solve in human intelligence analysis is structurally identical to a core problem in LLM agentic systems:

| Human Intelligence Analysis | LLM Agentic Systems |
|-----------------------------|---------------------|
| Analyst has cognitive biases from training and experience | Model has systematic biases from pretraining and RLHF |
| Mind-sets filter incoming information | Context priming shapes token generation |
| Groupthink in teams produces consensus errors | Multi-agent systems with identical base models produce echo chambers |
| Experts are *more* susceptible to overconfidence | Larger models are often *more* confidently wrong in domain-specific errors |
| Motivated reasoning toward preferred conclusions | Sycophancy — reasoning toward user-preferred answers |
| Mirror imaging projects analyst values onto adversaries | Persona capture — agent projects its value system onto modeled actors |

**The key insight**: SATs are *structural* interventions in the reasoning process. Because LLM agents are software systems, these structural interventions can be implemented as **architectural patterns** and **prompt engineering protocols** — not just advisory guidelines.

---

## LLM Bias Taxonomy

The following LLM failure modes map to the classical bias library:

| LLM Failure Mode | Analogous Human Bias | Description |
|-----------------|---------------------|-------------|
| Sycophancy | [[Wiki/concepts/confirmation-bias\|Confirmation Bias]] + [[Wiki/concepts/groupthink\|Groupthink]] | Model agrees with user framing even against evidence; rewards from RLHF aligned to approval — see [[Wiki/concepts/sycophancy\|Sycophancy]] |
| Hallucination with confidence | [[Wiki/concepts/overconfidence-bias\|Overconfidence Bias]] | States false facts in confident register; no calibrated uncertainty — see [[Wiki/concepts/hallucination\|Hallucination]] |
| Prompt anchoring | [[Wiki/concepts/anchoring-bias\|Anchoring Bias]] | Initial prompt framing propagates through all downstream reasoning |
| Context recency weighting | [[Wiki/concepts/availability-heuristic\|Availability Heuristic]] | Tokens near end of context window exert disproportionate influence |
| Training corpus frequency bias | [[Wiki/concepts/availability-heuristic\|Availability Heuristic]] | Common training patterns feel more probable and available |
| Premature closure | [[Wiki/concepts/anchoring-bias\|Anchoring Bias]] + [[Wiki/concepts/status-quo-bias\|Status Quo Bias]] | Settles on first plausible interpretation; subsequent reasoning confirms rather than re-evaluates |
| Persona capture / role lock | [[Wiki/concepts/mirror-imaging\|Mirror Imaging]] | Agent deeply adopts assigned persona; sanitizes adversary reasoning through its own value system |
| Self-consistency pressure | [[Wiki/concepts/status-quo-bias\|Status Quo Bias]] | Prior output becomes "status quo"; subsequent turns motivated to maintain consistency |
| Chain-of-thought confirmation | [[Wiki/concepts/motivated-reasoning\|Motivated Reasoning]] | Intermediate reasoning steps progressively commit to initial interpretation |
| Multi-agent echo chambers | [[Wiki/concepts/groupthink\|Groupthink]] | Multiple instances of same base model converge on identical errors; no genuine independent review |
| Instruction framing capture | [[Wiki/concepts/framing-effect\|Framing Effect]] | Task framing shifts output significantly independent of underlying content |

---

## SAT Adaptations for LLM Agents

### 1. ACH as Multi-Step Sequential Prompting
**Original:** Build matrix of hypotheses × evidence; focus on disconfirmation.

**LLM Adaptation (confirmed implementation from [[Wiki/sources/roberts-llm-sats-ftw-2025|Roberts: LLM SATs FTW (2025)]]):**

ACH **requires multiple sequential LLM calls** — a single prompt fails because it causes the model to anchor on the first hypothesis generated before evaluating evidence. Roberts' working implementation:

```
Call 1: "Generate [N] distinct, competing hypotheses that could explain [X].
         Do not evaluate them yet. Return as a JSON list."

Call 2 (per hypothesis): "Given hypothesis: [HYPOTHESIS]
         List evidence that would CONFIRM this hypothesis.
         List evidence that would DISCONFIRM this hypothesis.
         Rate each evidence item: C (consistent), I (inconsistent), N (neutral)."

Call 3 (per hypothesis): "Score this hypothesis given its evidence.
         Use scale -5 (strongly disconfirmed) to +5 (strongly confirmed).
         Return: {hypothesis, score, rationale}"

Post-processing: Sum scores. Export CSV. Human reviews, adds evidence, adjusts, decides.
```

**⚠ Anti-pattern:** Generating hypotheses and evaluating them in a single prompt causes prompt anchoring — the first hypothesis generated dominates evaluation. This defeats the disconfirmation structure of ACH.

**Biases countered:** [[Wiki/concepts/confirmation-bias|Confirmation Bias]], [[Wiki/concepts/anchoring-bias|Anchoring Bias]], [[Wiki/concepts/availability-heuristic|Availability Heuristic]], sycophancy, [[Wiki/concepts/motivated-reasoning|Motivated Reasoning]]

**Architecture:** Streamlit + GPT-4 + LangChain + Pydantic | Live: https://sat-ach.streamlit.app/

---

### 2. Devil's Advocacy as Adversarial Self-Review
**Original:** Assign an analyst to build the best case against the current consensus.

**LLM Adaptation (single-agent):**
```
"You just produced the following analysis: [ANALYSIS].
Now argue the strongest possible case AGAINST this analysis. 
Build the best counter-argument you can. Do not hedge or 
equivocate — make the opposition case as strong as possible."
```

**LLM Adaptation (multi-agent):**
- Agent A produces analysis
- Agent B (different temperature/system prompt) is given *only* the conclusion and tasked with maximum adversarial critique
- Agent A reviews Agent B's critique and updates if warranted

**Biases countered:** [[Wiki/concepts/confirmation-bias|Confirmation Bias]], [[Wiki/concepts/groupthink|Groupthink]], [[Wiki/concepts/motivated-reasoning|Motivated Reasoning]], sycophancy

**Implementation note:** Single-agent devil's advocacy works but is weaker than multi-agent because the same model's self-consistency pressure reduces genuine adversariality. Different models or significantly different system prompts produce stronger adversarial challenge.

---

### 3. Key Assumptions Check as Premise Audit
**Original:** List all assumptions the analytic line depends on; challenge each.

**LLM Adaptation:**
```
"Before giving your final answer on [TASK]:
1. List every assumption your reasoning depends on being true.
2. For each assumption, rate your confidence (high/medium/low) and explain why.
3. For each assumption: what would make it false? What would you expect 
   to observe if it were false?
4. Which assumptions, if wrong, would most change your answer?"
```

**Biases countered:** [[Wiki/concepts/anchoring-bias|Anchoring Bias]], [[Wiki/concepts/overconfidence-bias|Overconfidence Bias]], [[Wiki/concepts/motivated-reasoning|Motivated Reasoning]], [[Wiki/concepts/status-quo-bias|Status Quo Bias]]

**Implementation note:** This is one of the highest-leverage single prompts for improving LLM reasoning quality. It consistently surfaces unstated premises that confirm-bias would have hidden.

**⚠ KAC on long documents (from [[Wiki/sources/roberts-llm-sats-ftw-2025|Roberts: LLM SATs FTW (2025)]]):** Applying KAC to a full intelligence product (PDF) requires chunking due to token limits. This causes **cross-chunk context loss** — the model identifies assumptions within each chunk but misses assumptions that are only visible by cross-referencing evidence across the full document. Mitigation options: summarize the full document first, use a sliding window with overlap, or run a final consolidation pass that looks for cross-chunk inconsistencies.

---

### 4. Red Team as Adversarial Persona
**Original:** Analysts adopt adversary's perspective to evaluate their capabilities and likely actions.

**LLM Adaptation:**
```
System prompt: "You are [ADVERSARY/ACTOR]. Reason from their constraints, 
goals, risk tolerance, and world-view. Do NOT sanitize their reasoning 
through your own values. Pursue their objectives with full strategic logic."
```

**Multi-agent pattern:**
- Primary agent: produces an action plan
- Red team agent: adopts the adversary persona and evaluates what the adversary would do in response
- Primary agent: revises plan accounting for red team findings

**Biases countered:** [[Wiki/concepts/mirror-imaging|Mirror Imaging]], [[Wiki/concepts/framing-effect|Framing Effect]]

**Implementation note:** LLMs have strong tendency toward "sanitized" adversarial reasoning — they model adversaries as having reasonable goals and operating within implicit ethical constraints. This must be explicitly overridden in the system prompt.

---

### 5. What If? as Pre-Mortem
**Original:** Assume an unexpected event has occurred; explain how it could have happened.

**LLM Adaptation:**
```
"Assume that [CURRENT PLAN / ANALYSIS / DECISION] has FAILED catastrophically.
It's 6 months from now and things went badly wrong.
Working backwards: what went wrong? What did we miss? 
What assumptions proved false? What indicators were ignored?"
```

**Biases countered:** [[Wiki/concepts/overconfidence-bias|Overconfidence Bias]], [[Wiki/concepts/status-quo-bias|Status Quo Bias]], [[Wiki/concepts/hindsight-bias|Hindsight Bias]]

**Implementation note:** Pre-mortem prompting reliably reduces LLM overconfidence and surfaces failure modes. The temporal framing ("it's 6 months from now") helps displace the current state as the default reference.

---

### 6. Alternative Futures as Scenario Generation
**Original:** Systematically vary key drivers to generate multiple plausible future scenarios.

**LLM Adaptation:**
```
"Identify the 2-3 most uncertain and most impactful variables in [SITUATION].
For each combination of high/low values for these variables, 
describe a distinct plausible future. Give each scenario a name.
Do NOT indicate which you think is most likely until all scenarios are developed."
```

**Biases countered:** [[Wiki/concepts/status-quo-bias|Status Quo Bias]], [[Wiki/concepts/availability-heuristic|Availability Heuristic]], [[Wiki/concepts/overconfidence-bias|Overconfidence Bias]]

---

### 7. Quality of Information Check as Source Audit
**Original:** Evaluate completeness and soundness of information sources.

**LLM Adaptation:**
```
"Before answering [QUESTION]:
1. What sources or data types would you need to answer this confidently?
2. Which of those do you actually have access to in this conversation?
3. What important information is MISSING from what you've been given?
4. Where might your training data be incomplete, outdated, or biased 
   on this specific topic?"
```

**Biases countered:** [[Wiki/concepts/overconfidence-bias|Overconfidence Bias]], [[Wiki/concepts/availability-heuristic|Availability Heuristic]], [[Wiki/concepts/confirmation-bias|Confirmation Bias]]

---

### 8. Starbursting as Pre-Analysis Scope Mapping
**Original:** Generate questions (not answers) about a topic organized by 5W framework before analysis begins.

**LLM Adaptation (simplest of all SAT adaptations — zero-shot):**
```
"Before I begin analyzing [TOPIC], generate a comprehensive list of questions
that need to be answered. Organize them by:
- Who: actors, stakeholders, affected parties
- What: nature, scope, systems, impact
- When: timing, detection, resolution
- Where: origin, location, geographic scope  
- Why: motivation, cause, enabling factors

Do NOT answer any of these questions yet. Just generate the question space."
```

**Use case:** Pre-analysis scoping. Forces the analyst and agent to define what the analysis should cover before committing to any hypothesis.

**Biases countered:** [[Wiki/concepts/availability-heuristic|Availability Heuristic]], [[Wiki/concepts/anchoring-bias|Anchoring Bias]], [[Wiki/concepts/framing-effect|Framing Effect]], [[Wiki/concepts/confirmation-bias|Confirmation Bias]]

**Architecture:** Zero-shot single query (per [[Wiki/sources/roberts-llm-sats-ftw-2025|Roberts: LLM SATs FTW (2025)]]); output can be visualized as Mermaid mind map. Live: https://sat-starburst.streamlit.app/

---

## Architectural Patterns

### Independent Parallel Analysis
Run multiple agent calls on the same task with different system prompts (or different models) before any agent sees the others' outputs. Aggregate or debate results. Directly counters [[Wiki/concepts/groupthink|Groupthink]] in multi-agent systems.

### Separation of Generation and Evaluation
Never ask an LLM to generate options and select among them in the same prompt. Generate first (all options, no evaluation), evaluate second (all options against criteria). Counters [[Wiki/concepts/anchoring-bias|Anchoring Bias]] and [[Wiki/concepts/availability-heuristic|Availability Heuristic]].

### Explicit Uncertainty Tracking
Require agents to output a structured confidence assessment with every substantive claim:
```json
{
  "claim": "...",
  "confidence": "high|medium|low",
  "key_assumptions": ["...", "..."],
  "what_would_change_this": "..."
}
```
Counters [[Wiki/concepts/overconfidence-bias|Overconfidence Bias]].

### Adversarial Review Gate
Before any agent output is acted upon, route it through an adversarial review agent with an explicit Devil's Advocacy system prompt. The primary agent must acknowledge the critique. Counters [[Wiki/concepts/confirmation-bias|Confirmation Bias]], [[Wiki/concepts/motivated-reasoning|Motivated Reasoning]].

### Context Anchoring Reset
For long-running agent sessions, periodically re-ground the agent with a "Key Assumptions Check" prompt to surface drifted premises. Counters [[Wiki/concepts/anchoring-bias|Anchoring Bias]] and [[Wiki/concepts/status-quo-bias|Status Quo Bias]] accumulating across turns.

---

## Empirical Evidence (from [[Wiki/sources/roberts-llm-sats-ftw-2025|Roberts: LLM SATs FTW (2025)]])

[[Wiki/entities/scott-roberts|Scott Roberts]] is the first source in this wiki to provide **empirical results** from actually running LLM-SAT tools on real problems. Key findings:

| Finding | SAT | Status |
|---------|-----|--------|
| ACH requires multi-step sequential calls, not a single prompt | ACH | ✅ Confirmed implementation pattern |
| Starbursting works as zero-shot single query | Starbursting | ✅ Confirmed; simplest to implement |
| KAC on long documents causes cross-chunk context loss | KAC | ⚠️ Known failure mode; chunking required but imperfect |
| LLMs "help, but rarely replace" analysts | All | Confirmed; human review step is essential |
| CSV export + human review is the correct human-machine team model | ACH, KAC | Confirmed working pattern |
| GPT-4 is not required; any capable model works | All | Architecture is model-agnostic |

**Roberts' framing:**  
> *"An AI system doesn't have to be better than a human, just better than the best available human."*

This directly addresses open question #1 below: there is now at least one practitioner's empirical evidence that the patterns work in practice, though formal bias-reduction measurement is still lacking.

---

## Open Questions

1. ~~What is the empirical evidence for SAT-inspired prompting patterns actually reducing LLM bias?~~ Roberts (2025) provides practitioner empirical evidence that the tools work in practice. Formal academic measurement of bias reduction magnitude remains an open research question.
2. How do these patterns interact with chain-of-thought prompting? Does CoT amplify or reduce the biases targeted by SATs?
3. At what scale (agent count, context length, task complexity) do these patterns become computationally prohibitive?
4. Can the bias taxonomy from intelligence analysis be validated against LLM failure mode taxonomies from alignment research (sycophancy, specification gaming, reward hacking)?
5. **New (from Roberts):** How can cross-chunk context loss in KAC be fully mitigated? Map-reduce, sliding windows, and pre-summarization are candidates — untested comparatively.

---

## See Also

[[Wiki/concepts/structured-analytic-techniques|Structured Analytic Techniques]] | [[Wiki/concepts/cognitive-bias|Cognitive Bias]] | [[Wiki/concepts/system-1-system-2|System 1 / System 2]] | [[Wiki/synthesis/bias-sat-matrix|Bias x SAT Matrix]] | [[Wiki/synthesis/sat-selection-guide|SAT Selection Guide]] | [[Wiki/synthesis/sat-pipeline|SAT Pipeline]]
