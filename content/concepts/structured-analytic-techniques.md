---
type: concept
tags: [wiki/concept]
date_updated: 2026-05-19
confidence: high
source_count: 3
---

# Structured Analytic Techniques (SATs)

A family of systematic methods designed to improve analysis by making reasoning processes explicit, challenging assumptions, stimulating creativity, and managing uncertainty. Core tool of modern intelligence analysis and increasingly applied in cybersecurity.

---

## Definition

From [[sources/tradecraft-primer-2009|CIA Tradecraft Primer (2009)]]: techniques that help analysts "challenge judgments, identify mental mindsets, stimulate creativity, and manage uncertainty."

From [[sources/riley-sats-cybersecurity-2024|Riley: SATs in Cybersecurity (2024)]]: "systematic methods designed to improve analysis by reducing cognitive biases, challenging assumptions, and promoting clarity and creativity in reasoning."

---

## The Problem SATs Solve

The three perennial problems in intelligence analysis ([[sources/tradecraft-primer-2009|CIA Tradecraft Primer (2009)]]):
1. **Complexity** of international developments
2. **Incomplete and ambiguous information**
3. **Inherent limitations of the human mind** ← SATs directly address this

The human limitations problem: analysts process information through [[concepts/mind-set|mental models]] that filter incoming information in ways that can lead to systematic [[concepts/cognitive-bias|cognitive biases]].

---

## The 12 CIA-Defined Techniques (3 Categories)

*From the [[sources/tradecraft-primer-2009|CIA Tradecraft Primer (2009)]]. Note: the full Heuer/Pherson book ([[entities/heuer-pherson-book|Heuer & Pherson (book)]]) includes additional techniques — see below.*

### Diagnostic Techniques
*(Make analytic arguments, assumptions, or intelligence gaps transparent)*
- [[concepts/key-assumptions-check|Key assumptions check]]
- [[concepts/quality-of-information-check|Quality of information check]]
- [[concepts/indicators-or-signposts-of-change|Indicators or signposts of change]]
- [[concepts/analysis-of-competing-hypotheses|Analysis of competing hypotheses (ach)]]

### Contrarian Techniques
*(Explicitly challenge current thinking)*
- [[concepts/devils-advocacy|Devil's advocacy]]
- [[concepts/team-a-team-b|Team a/team b]]
- [[concepts/high-impact-low-probability-analysis|High Impact low Probability analysis]]
- [[concepts/what-if-analysis|What if? analysis]]

### Imaginative Thinking Techniques
*(Develop new insights, perspectives, and alternative outcomes)*
- [[concepts/brainstorming|Brainstorming]]
- [[concepts/outside-in-thinking|Outside In thinking]]
- [[concepts/red-team-analysis|Red team analysis]]
- [[concepts/alternative-futures-analysis|Alternative futures analysis]]

---

## Additional Techniques (Heuer/Pherson Book)

The full *Structured Analytic Techniques for Intelligence Analysis* ([[entities/heuer-pherson-book|Heuer & Pherson (book)]]) covers a broader taxonomy than the CIA Primer's 12:

- [[concepts/starbursting|Starbursting]] — Idea Generation; 5W question-scoping pre-analysis technique; confirmed in LLM implementation by [[sources/roberts-llm-sats-ftw-2025|Roberts: LLM SATs FTW (2025)]]

*Book not yet directly ingested — known through [[sources/roberts-llm-sats-ftw-2025|Roberts: LLM SATs FTW (2025)]]. See entity page for status.*

---

## Application in Cybersecurity (per [[sources/riley-sats-cybersecurity-2024|Riley: SATs in Cybersecurity (2024)]])

SATs are **role-agnostic** within cybersecurity — applicable across all roles because the underlying challenges (complexity, ambiguity, uncertainty) are universal. Key roles where SATs are applied:
- Threat Intelligence Analysts (ACH, Indicators, Red Team)
- Incident Responders (Key Assumptions Check, What If?, Brainstorming)
- Risk Analysts (Alternative Futures, High-Impact/Low-Probability)
- Forensic Investigators (ACH, Devil's Advocacy)
- SOC Analysts (Brainstorming, Red Team, Key Assumptions Check)

---

## Sources

- [[sources/tradecraft-primer-2009|CIA Tradecraft Primer (2009)]] — definitive government reference (CIA, 2009)
- [[sources/riley-sats-cybersecurity-2024|Riley: SATs in Cybersecurity (2024)]] — cybersecurity application overview
- [[sources/roberts-llm-sats-ftw-2025|Roberts: LLM SATs FTW (2025)]] — LLM implementation (Starbursting + ACH + KAC); introduces Heuer/Pherson book reference
