---
type: concept
tags: [wiki/concept, wiki/llm-bias]
date_updated: 2026-05-19
confidence: high
source_count: 0
domain: llm-alignment
---

# Hallucination

The tendency of an LLM to **generate confident, fluent, plausible-sounding statements that are factually incorrect, unsupported, or fabricated** — without any internal signal that the output is unreliable. The model does not know it doesn't know.

Hallucination is the LLM analog of [[concepts/overconfidence-bias|Overconfidence Bias]], but with a structural difference: human overconfidence involves *underestimating uncertainty*; LLM hallucination involves *having no uncertainty signal at all* for many outputs.

---

## Mechanism

LLMs are trained to predict the next token given a context. The training objective has no direct mechanism for:

1. Distinguishing "I learned this from reliable sources" from "this token sequence looks plausible"
2. Refusing to generate when evidence is thin
3. Calibrating confidence to evidence quality

Result: the model generates *fluent* text regardless of reliability. Fluency and factual accuracy are decoupled. The model's "confidence" is expressed through register (hedging words, assertive tone) — but this register is also learned from patterns, not from actual epistemic state.

**Types of hallucination:**

| Type | Description | Example |
|------|-------------|---------|
| **Factual fabrication** | States false facts as true | Fake citations, wrong dates, invented statistics |
| **Confabulation** | Fills gaps in knowledge with plausible-sounding content | "As Heuer wrote in his 1995 paper..." (paper doesn't exist) |
| **Over-generalization** | Applies a pattern to cases where it doesn't hold | Correct principle applied to wrong domain |
| **Source hallucination** | Invents or misattributes sources | Cites a real author but wrong paper, or invents a paper entirely |
| **Reasoning hallucination** | Produces correct-seeming intermediate reasoning steps that lead to wrong conclusions | Math errors with confident presentation |

---

## Why It Matters for Agentic Systems

In a single-turn chat, a hallucinated fact can be caught by a skeptical user. In agentic systems, hallucination is more dangerous:

- **Tool-use agents**: a hallucinated API endpoint, SQL table, or file path causes a cascade of downstream errors
- **Multi-agent pipelines**: Agent B receives Agent A's hallucinated output as grounded fact; it builds on it; the hallucination propagates and compounds
- **Long-horizon tasks**: early hallucinations shape later steps; by the time the error manifests, the causal chain is long and the fix is costly
- **Self-consistency amplification**: if an agent generates a false claim and then checks it by re-generating, the same false pattern may re-emerge (the model is consistent with itself, not with truth)

---

## Relationship to Human Biases

| Hallucination Pattern | Human Analogue | Difference |
|----------------------|----------------|-----------|
| High confidence on weak evidence | [[concepts/overconfidence-bias\|Overconfidence Bias]] | Human overconfidence: underestimates uncertainty. LLM: no uncertainty signal. |
| Fabricates supporting sources | [[concepts/confirmation-bias\|Confirmation Bias]] | Human: selectively attends to confirming sources. LLM: invents them. |
| Plausible-sounding gap-filling | [[concepts/availability-heuristic\|Availability Heuristic]] | Human: uses available patterns. LLM: uses fluency patterns from training. |
| Consistent-with-prior outputs | [[concepts/anchoring-bias\|Anchoring Bias]] | Human: adjusts from anchor. LLM: maintains self-consistency. |

---

## SAT Countermeasures

| Technique | How It Counters Hallucination |
|-----------|------------------------------|
| [[concepts/quality-of-information-check\|Quality of Information Check]] | Forces explicit source audit — agent must identify *what* it actually has access to vs. what it's inferring |
| [[concepts/key-assumptions-check\|Key Assumptions Check]] | Requires distinguishing "known fact" from "assumed" from "inferred" — surfaces the epistemic gaps hallucination fills |
| [[concepts/devils-advocacy\|Devil's Advocacy]] | Adversarial review agent looks specifically for unsupported claims, missing citations, fabricated specifics |
| [[concepts/indicators-or-signposts-of-change\|Indicators or Signposts of Change]] | Forces explicit statement of what *evidence* would be needed to support each claim — hallucinated claims typically can't specify real evidence |

---

## Prompt Patterns

**Pattern 1 — Epistemic labeling:**
```
"For each factual claim in your response, label it as one of:
  [KNOWN] — you have high confidence from training data
  [INFERRED] — logical deduction from known facts
  [UNCERTAIN] — you are not confident; this may be wrong
  [UNKNOWN] — you do not have this information

Do not generate [UNKNOWN] claims. Flag [UNCERTAIN] claims explicitly."
```

**Pattern 2 — Source grounding:**
```
"Only make factual claims that you can ground in the documents provided
in this context. If a claim is not supported by the provided context,
say so explicitly rather than drawing on training data."
```

**Pattern 3 — Absence acknowledgment:**
```
"Before answering, list: what information would you need to answer
this question reliably? Which of that do you actually have?
What are you filling in from pattern rather than evidence?"
```

---

## Distinction: Hallucination vs. Sycophancy

Both are LLM-native failure modes, but the trigger differs:

| | [[concepts/sycophancy\|Sycophancy]] | Hallucination |
|-|------------|---------------|
| **Trigger** | Social/approval signal (user preference) | Fluency signal (plausible completion) |
| **Target** | Agreement with user's views | Filling gaps with fluent content |
| **Primary SAT counter** | Devil's Advocacy, Team A/Team B | Quality of Information Check, KAC |
| **Mitigation** | Adversarial prompting, role assignment | Source grounding, epistemic labeling |

In practice they interact: a hallucinated claim that the user implicitly wants to be true will be sycophantically reinforced rather than corrected.

---

## See Also

[[concepts/overconfidence-bias|Overconfidence Bias]] | [[concepts/sycophancy|Sycophancy]] | [[concepts/quality-of-information-check|Quality of Information Check]] | [[concepts/key-assumptions-check|Key Assumptions Check]] | [[synthesis/sats-for-llm-agents|SATs for LLM Agents]]
