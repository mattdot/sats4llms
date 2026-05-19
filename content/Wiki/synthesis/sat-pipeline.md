---
type: synthesis
tags: [wiki/synthesis]
date_updated: 2026-05-19
query: "How do SATs work together in sequence as a complete agentic workflow?"
sources_used: ["[[Wiki/sources/tradecraft-primer-2009|CIA Tradecraft Primer (2009)]]", "[[Wiki/sources/roberts-llm-sats-ftw-2025|Roberts: LLM SATs FTW (2025)]]"]
confidence: medium
---

# SAT Pipeline

**Query:** How do SATs compose into a complete analytic pipeline rather than isolated interventions?

*Individual technique pages describe each SAT in isolation. This page describes how they chain together into end-to-end workflows for LLM agentic systems.*

---

## The Core Insight

SATs were designed as a toolkit — any one technique reduces bias in a specific way, but full analytic rigor requires multiple techniques applied in sequence. The sequence matters: each technique produces output that is the input for the next.

For LLM agents, this means the "SAT pipeline" is a **multi-step orchestration pattern**, not a single prompt. [[Wiki/entities/scott-roberts|Scott Roberts]]' ACH implementation demonstrated this: ACH cannot be a single prompt — it requires sequential calls where hypothesis generation, evidence generation, and scoring are separate queries. The same principle extends to full pipelines.

---

## The Full Pipeline (Scoping → Analysis → Challenge → Forecast)

```
Phase 1: SCOPING
  Starbursting    → What questions do we need to answer?
       ↓
  Brainstorming   → What hypotheses / explanations exist?

Phase 2: ANALYSIS
  ACH             → Which hypotheses survive evidence disconfirmation?
       ↓
  Key Assumptions → What does the leading hypothesis depend on being true?
  Check
       ↓
  Quality of Info → Are our sources good enough to support this?
  Check

Phase 3: CHALLENGE
  Devil's Advocacy → What's the strongest case against the conclusion?
       ↓
  Red Team         → What would an adversary do with our conclusion?
  (if adversarial)

Phase 4: FORECAST / MONITOR
  Alternative      → What futures could emerge from this situation?
  Futures
       ↓
  Indicators /     → What signals will tell us which future is unfolding?
  Signposts
```

---

## Minimal Viable Pipeline (3-step)

For most agentic tasks, a full 8-step pipeline is overkill. The minimal high-value sequence:

```
1. Key Assumptions Check   → What assumptions is this reasoning built on?
2. Devil's Advocacy        → What's the strongest case against the conclusion?
3. Quality of Info Check   → Do our sources actually support this?
```

This 3-step sequence covers the broadest set of biases ([[Wiki/concepts/confirmation-bias|Confirmation Bias]], [[Wiki/concepts/anchoring-bias|Anchoring Bias]], [[Wiki/concepts/motivated-reasoning|Motivated Reasoning]], [[Wiki/concepts/overconfidence-bias|Overconfidence Bias]], [[Wiki/concepts/sycophancy|Sycophancy]], [[Wiki/concepts/hallucination|Hallucination]]) with minimal orchestration complexity.

---

## LLM Orchestration Architecture

### Pattern A: Sequential Single-Agent

One agent processes all stages sequentially. Each SAT stage is a separate call; the agent receives the prior stage's output as context.

```
Call 1 [Starbursting]: "What questions should we ask about [TOPIC]?"
  → output: question map

Call 2 [Brainstorming]: "Given these questions, what are the competing
  hypotheses? Generate all possibilities before evaluating any."
  → output: hypothesis list

Call 3–N [ACH per hypothesis]: "For hypothesis [H], what evidence
  confirms or disconfirms it? Rate each: C/I/N."
  → output: evidence matrix

Call N+1 [KAC]: "What assumptions does the top hypothesis depend on?
  Rate each assumption's confidence."
  → output: assumption list

Call N+2 [Devil's Advocacy]: "Build the strongest case AGAINST
  the top hypothesis."
  → output: adversarial critique

Call N+3 [Synthesis]: "Given all of the above, what is the most
  defensible conclusion? Where should a human reviewer focus?"
  → output: final judgment + review flags
```

**Pro:** Simple to implement; no multi-agent infrastructure needed.  
**Con:** Self-consistency pressure — the same model processes all stages; later stages are influenced by earlier outputs, which may introduce subtle anchoring.

---

### Pattern B: Parallel Independent Analysis + Adversarial Review

Multiple independent agents run on the same problem without seeing each other's outputs; an adversarial agent then critiques all results.

```
[Agent A: Analyst]    ─┐
[Agent B: Analyst]    ─┼─→ [Agent C: Devil's Advocate] → [Synthesis Agent]
[Agent C: Skeptic]    ─┘
```

Implementation:
1. Run Agent A (primary analysis, ACH)
2. Run Agent B (independent ACH — same task, same data, no shared context)
3. Run Adversarial Agent — receives A's and B's conclusions; tasked with maximum critique
4. Synthesis Agent — receives all three; produces final judgment with explicit disagreement flags

**Pro:** Counters [[Wiki/concepts/groupthink|Groupthink]] and self-consistency anchoring.  
**Con:** 3–4× compute cost; requires orchestration layer (LangChain, LangGraph, CrewAI, etc.).

**Key requirement:** Agents A and B must have **no shared context** for their analyses. If they see each other's outputs before generating, Pattern B degrades to Pattern A.

---

### Pattern C: Post-Hoc Audit (KAC + Devil's Advocacy on Finished Output)

For cases where you already have an output (e.g., a drafted report, a model recommendation) and want to apply SATs retrospectively:

```
Input: finished output

Call 1 [KAC]: "List every assumption in this analysis. Rate confidence
  of each. What would make each assumption false?"

Call 2 [Devil's Advocacy]: "Build the strongest case that this
  analysis is wrong or incomplete."

Call 3 [Quality Check]: "What sources support the claims in this
  analysis? What claims are unsupported? What's missing?"
```

This matches [[Wiki/entities/scott-roberts|Roberts]]' Key Assumptions Check implementation (applied to a finished Strider intelligence report). It's the lowest-friction pipeline entry point — requires no upfront process change, just retrospective review.

---

## Failure Modes of the Pipeline Itself

| Failure Mode | Cause | Mitigation |
|-------------|-------|-----------|
| **Analysis paralysis** | Too many SAT stages; the process becomes the product | Timebox each stage; use minimal viable pipeline |
| **Anchoring on Stage 1** | Early Starbursting/Brainstorming output shapes all downstream reasoning | Regenerate hypotheses independently before ACH; don't show Stage 1 output to ACH agent |
| **False confidence from process** | "We ran the SAT pipeline, therefore the conclusion is sound" | The pipeline reduces bias — it doesn't eliminate it; human review of the adversarial critique is non-negotiable |
| **Sycophantic devil's advocacy** | The adversarial agent produces mild critique rather than genuine challenge | Explicit system prompt: "Your critique should be as strong as possible. Do not hedge." Different model or temperature from primary agent |
| **Cross-chunk context loss** | Long documents chunked for KAC lose cross-document context | Summarize full document before chunking; run a final consolidation pass (see [[Wiki/sources/roberts-llm-sats-ftw-2025\|Roberts: LLM SATs FTW (2025)]]) |

---

## Mapping Pipelines to [[Wiki/concepts/system-1-system-2|System 1 / System 2]]

The pipeline is a System 2 scaffold:

- **System 1** (LLM default): single-prompt completion → fast, fluent, biased
- **System 2** (SAT pipeline): structured multi-step process → slower, more effortful, less biased

Just as humans default to System 1 unless explicitly required to engage System 2, LLMs default to single-step completion unless prompted into multi-step structured reasoning. The pipeline is the mechanism for that prompting.

---

## See Also

[[Wiki/synthesis/sat-selection-guide|SAT Selection Guide]] | [[Wiki/synthesis/sats-for-llm-agents|SATs for LLM Agents]] | [[Wiki/synthesis/bias-sat-matrix|Bias x SAT Matrix]]
