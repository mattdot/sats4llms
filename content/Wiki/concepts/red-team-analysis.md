---
type: concept
tags: [wiki/concept, wiki/sat]
date_updated: 2026-05-19
confidence: high
source_count: 2
sat_category: imaginative
---

# Red Team Analysis

A [[concepts/structured-analytic-techniques|SAT]] in which analysts adopt the perspective of an adversary or other actor to evaluate courses of action, capabilities, and intent from that actor's point of view.

---

## Purpose

Generate insights about adversary behavior that a conventional analysis — conducted from the analyst's own perspective — would miss. Forces consideration of the adversary's logic, constraints, and objectives rather than projecting one's own rationality.

---

## Relationship to Attribution Bias

Red Team Analysis directly counters the *attribution bias* in [[concepts/cognitive-bias|cognitive biases]]: the tendency to attribute others' behavior to fixed nature while attributing one's own behavior to situational factors. By explicitly adopting the adversary's frame, analysts must reason from that actor's situation.

---

## Applied in Cybersecurity

**Threat Intelligence Analysts** ([[sources/riley-sats-cybersecurity-2024|Riley: SATs in Cybersecurity (2024)]])  
Models adversary TTPs (Tactics, Techniques, and Procedures) to understand and predict attacker strategies.

**Forensic Investigators**  
Evaluates how attackers might attempt to mislead forensic investigations (anti-forensics, false flag operations).

**SOC Analysts**  
Simulates potential attacker scenarios, preparing SOC analysts for adversaries' likely actions.

**Vulnerability Analysts**  
Explores how discovered vulnerabilities might be exploited under different adversarial models (script kiddies vs. advanced persistent threats).

---

## Biases Primarily Controlled

| Bias | How this technique counters it |
|------|-------------------------------|
| [[concepts/mirror-imaging\|Mirror Imaging]] | The primary technique for this bias — forces analysts to inhabit the adversary's logic rather than projecting their own |
| [[concepts/framing-effect\|Framing Effect]] | Replacing the analyst's natural frame with the adversary's frame; outcome depends on which frame is applied |
| [[concepts/availability-heuristic\|Availability Heuristic]] | Adversary capabilities and motivations that are unfamiliar to the analyst are made cognitively available through structured role adoption |

---

## Note

The term "red team" is also used in cybersecurity to describe an offensive security team that conducts authorized penetration testing. This is a related but distinct usage — a live red team engagement vs. an analytic red-teaming exercise. Context determines which meaning applies.

---

## Sources

- [[sources/tradecraft-primer-2009|CIA Tradecraft Primer (2009)]] (p. 31)
- [[sources/riley-sats-cybersecurity-2024|Riley: SATs in Cybersecurity (2024)]]
