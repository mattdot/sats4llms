---
type: concept
tags: [wiki/concept, wiki/sat]
date_updated: 2026-05-19
confidence: high
source_count: 1
sat_category: imaginative
---

# Starbursting

A [[Wiki/concepts/structured-analytic-techniques|SAT]] that generates questions about a topic, organized around the five W framework (Who, What, When, Where, Why), to scope a problem and identify what needs to be explored. A pre-analysis, idea-generation technique.

---

## Purpose

Define the scope of an analytic problem by systematically generating the questions that need to be answered — before attempting to answer any of them. Prevents premature closure by ensuring the question space is fully mapped before analysis begins.

---

## How It Differs From Brainstorming

[[Wiki/concepts/brainstorming|Brainstorming]] generates *answers* (hypotheses, explanations, options). Starbursting generates *questions*. Used earlier in the analytic process — before brainstorming or ACH — to define what the analysis should cover.

**Sequence:** Starbursting (scope questions) → [[Wiki/concepts/brainstorming|Brainstorming]] (generate hypotheses) → [[Wiki/concepts/analysis-of-competing-hypotheses|Analysis of Competing Hypotheses (ACH)]] (evaluate hypotheses)

---

## Method

Organize questions around the 5W framework:
- **Who** — actors, stakeholders, affected parties
- **What** — nature of the event, systems, impact
- **When** — timing, detection, resolution
- **Where** — origin, location, geographic scope
- **Why** — motivations, causes, enabling factors

*(Some versions add **How** for a 5W+1H framework.)*

---

## Biases Primarily Controlled

| Bias | How this technique counters it |
|------|-------------------------------|
| [[Wiki/concepts/availability-heuristic\|Availability Heuristic]] | Systematic 5W structure surfaces questions in less-salient categories (e.g., "Where?" when "Who?" dominates attention) |
| [[Wiki/concepts/anchoring-bias\|Anchoring Bias]] | Question generation precedes hypothesis formation; prevents early hypotheses from anchoring the scope |
| [[Wiki/concepts/framing-effect\|Framing Effect]] | Expanding to all five question categories breaks the framing of the initial problem statement |
| [[Wiki/concepts/confirmation-bias\|Confirmation Bias]] | Pre-analysis scoping ensures questions are generated before any hypothesis is formed to confirm |

---

## LLM Implementation (per [[Wiki/sources/roberts-llm-sats-ftw-2025|Roberts: LLM SATs FTW (2025)]])

**Approach:** Zero-shot single query — the simplest SAT to implement with an LLM.

Roberts' implementation (GPT-4 + Streamlit):
1. Analyst submits topic
2. LLM generates questions organized by 5W categories
3. Output visualized as a Mermaid mind map

**Example output (ransomware attack on a hospital):**
```
Who carried out the attack? | Who was affected? | Who responded?
What was the nature of the attack? | What systems were affected?
When did it occur? | When was it detected? | When resolved?
Where did it originate? | Where did it cause most damage?
Why was the hospital targeted? | Why was the attack successful?
```

**Assessment:** Fast, simple, good for problem scoping. Zero-shot works because the task is generative and bounded; no evaluation or scoring required.

Live app: https://sat-starburst.streamlit.app/  
Code: https://github.com/sroberts/talk-llm-sats-ftw-code/blob/main/experiment-1-starburst.py

---

## Note: Not in CIA Tradecraft Primer

Starbursting is from the broader [[Wiki/entities/heuer-pherson-book|Heuer & Pherson (book)]] (*Structured Analytic Techniques for Intelligence Analysis*, 3rd ed.) — not included in the [[Wiki/sources/tradecraft-primer-2009|CIA Tradecraft Primer (2009)]], which covers only 12 techniques. The full Heuer/Pherson taxonomy is larger.

---

## Sources

- [[Wiki/sources/roberts-llm-sats-ftw-2025|Roberts: LLM SATs FTW (2025)]]
