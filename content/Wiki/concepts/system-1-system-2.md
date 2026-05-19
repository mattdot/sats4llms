---
type: concept
tags: [wiki/concept, wiki/bias-theory]
date_updated: 2026-05-19
confidence: high
source_count: 1
domain: cognitive-psychology
---

# System 1 / System 2 (Dual-Process Theory)

The theoretical framework underlying the entire [[Wiki/concepts/cognitive-bias|Cognitive Bias]] research program. Proposed by [[Wiki/entities/daniel-kahneman|Daniel Kahneman]] (drawing on earlier work by [[Wiki/entities/amos-tversky|Amos Tversky]] and Stanovich & West), and synthesized in *Thinking, Fast and Slow* (2011).

**The core claim:** human cognition operates via two distinct systems with different speeds, capacities, and error profiles. [[Wiki/concepts/structured-analytic-techniques|Structured Analytic Techniques]] work because they impose System 2 structure onto processes that System 1 would otherwise handle — badly.

---

## The Two Systems

| Dimension | System 1 | System 2 |
|-----------|----------|----------|
| **Speed** | Fast, automatic | Slow, deliberate |
| **Effort** | Effortless | Effortful |
| **Capacity** | Unlimited parallel processing | Serial, limited capacity |
| **Consciousness** | Unconscious, implicit | Conscious, explicit |
| **Learning** | Pattern-matched from experience | Rule-following, logical |
| **Errors** | Systematic, predictable biases | Random errors; avoidable with care |
| **Examples** | Reading facial expressions, driving on familiar roads, 2+2 | Complex math, novel arguments, deliberate planning |

System 1 is not stupid — it is extraordinarily capable and correct in familiar domains. Its failures are **systematic** (not random), which is why they are predictable and why structural interventions work.

---

## Why Biases Arise

System 1 solves hard problems by substituting easier ones — **heuristics**. These usually work, but produce predictable failures:

| Heuristic | What System 1 Does | Resulting Bias |
|-----------|-------------------|---------------|
| Availability | Judges probability by ease of recall | [[Wiki/concepts/availability-heuristic|Availability Heuristic]] |
| Anchoring and adjustment | Takes first number as anchor; adjusts insufficiently | [[Wiki/concepts/anchoring-bias|Anchoring Bias]] |
| Representativeness | Judges by resemblance to prototype | Base rate neglect, conjunction fallacy |
| Affect | Uses emotional response as a proxy for probability | [[Wiki/concepts/framing-effect|Framing Effect]], [[Wiki/concepts/motivated-reasoning|Motivated Reasoning]] |
| Coherence / narrative | Constructs the most coherent story from available data | [[Wiki/concepts/confirmation-bias|Confirmation Bias]], [[Wiki/concepts/hindsight-bias|Hindsight Bias]] |

System 1 runs first, automatically. System 2 only engages when System 1 flags uncertainty — and System 1 rarely flags its own errors. **This is the fundamental problem SATs address.**

---

## Why SATs Work

SATs are **System 2 scaffolds** — structured processes that:

1. Force System 2 engagement on problems System 1 would auto-solve (incorrectly)
2. Make System 1's implicit outputs explicit so they can be examined
3. Create friction that prevents System 1 from settling on the first plausible interpretation
4. Distribute cognitive load across structure so System 2 capacity isn't exhausted

| SAT Mechanism | System 1/2 Translation |
|---------------|----------------------|
| Writing down all assumptions | Makes System 1's background model explicit and examinable by System 2 |
| Generating all hypotheses before evaluating | Prevents System 1's coherence-seeking from locking onto the first plausible story |
| Assigned devil's advocate role | Forces System 2 to construct counter-narrative that System 1 would suppress |
| Evidence matrix | Replaces System 1's narrative "feel" with System 2's systematic accounting |
| Pre-mortem | Hijacks System 1's fluency ("imagine it already happened") to surface failures |

---

## The LLM Parallel

LLMs do not have System 1 and System 2 in the cognitive science sense — but they exhibit **functionally analogous patterns**:

| Human System 1/2 | LLM Functional Analog |
|-----------------|----------------------|
| System 1: fast, pattern-matched, confident | Autoregressive completion on high-probability token sequences |
| System 2: slow, deliberate, effortful | Chain-of-thought prompting; multi-step reasoning |
| System 1 errors: systematic, predictable | LLM biases: sycophancy, anchoring, hallucination — systematic, not random |
| SATs impose System 2 structure | SAT-structured prompts impose deliberate, multi-step reasoning structure |
| System 2 requires explicit instruction to engage | LLMs require explicit prompting to reason rather than pattern-complete |

**The key insight for LLM agents:** just as System 2 doesn't engage automatically — it must be *invoked* — LLMs don't reason carefully by default. They must be *prompted* to do so through structural interventions. SATs are exactly that kind of structural intervention.

---

## Calibrated Uncertainty vs. Overconfidence

A core System 1 failure is **overconfidence**: the system produces confident outputs regardless of actual reliability. System 2 can modulate confidence but only when engaged. This maps directly to LLM hallucination: high-confidence output on low-reliability token predictions.

SATs that force explicit confidence rating ([[Wiki/concepts/key-assumptions-check|Key Assumptions Check]], [[Wiki/concepts/quality-of-information-check|Quality of Information Check]]) are directly targeting this System 1 → System 2 gap.

---

## Key Reference

**Kahneman, D.** (2011). *Thinking, Fast and Slow*. Farrar, Straus and Giroux.  
Original dual-process framework developed with [[Wiki/entities/amos-tversky|Amos Tversky]] in the 1970s–1990s (Prospect Theory, heuristics and biases program).

---

## See Also

[[Wiki/concepts/cognitive-bias|Cognitive Bias]] | [[Wiki/concepts/mind-set|Mind-Set]] | [[Wiki/entities/daniel-kahneman|Daniel Kahneman]] | [[Wiki/concepts/structured-analytic-techniques|Structured Analytic Techniques]]
