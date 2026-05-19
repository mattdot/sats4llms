---
type: concept
tags: [wiki/concept, wiki/bias]
date_updated: 2026-05-19
confidence: high
source_count: 2
---

# Groupthink

A mode of thinking that occurs when the **desire for harmony and conformity in a group overrides realistic appraisal of alternatives**. The group prioritizes cohesion and consensus over critical analysis, often producing poor decisions that individual members might have rejected privately.

---

## Origin

First described by **Irving Janis** (1972) in *Victims of Groupthink*, which analyzed foreign policy disasters including the Bay of Pigs invasion, the Pearl Harbor intelligence failure, and the escalation of the Korean War. Janis coined the term by analogy with Orwell's "doublethink" — the collective counterpart of individual cognitive bias.

---

## Symptoms (Janis's Eight)

1. **Illusion of invulnerability** — excessive optimism; willingness to take extreme risks
2. **Collective rationalization** — members dismiss warnings that challenge shared assumptions
3. **Belief in inherent morality** — group ignores ethical or moral consequences of decisions
4. **Stereotyped views of out-groups** — adversaries seen as too weak, evil, or stupid to respond effectively
5. **Pressure on dissenters** — members who express doubts are pressured to conform
6. **Self-censorship** — members withhold dissenting views to avoid social friction
7. **Illusion of unanimity** — silence is interpreted as consent; dissenting views are invisible
8. **Self-appointed mind guards** — some members actively filter information that would disturb the consensus

---

## Intelligence Analysis Context

[[Wiki/sources/riley-sats-cybersecurity-2024|Riley: SATs in Cybersecurity (2024)]] identifies groupthink as one of the biases SATs counteract in cybersecurity analysis. In intelligence analysis, groupthink was a contributing factor in:
- The 2003 Iraq WMD assessment (analysts felt institutional pressure toward the dominant interpretation)
- The 1962 Bay of Pigs planning (Janis's original case study)

The [[Wiki/sources/tradecraft-primer-2009|CIA Tradecraft Primer (2009)]] addresses groupthink indirectly throughout — it's the primary social mechanism that makes [[Wiki/concepts/mind-set|mind-sets]] persistent even in team settings. The entire Contrarian Techniques category exists primarily to counteract it.

---

## LLM Agentic Systems Context

LLM agents exhibit groupthink-analogous behavior in multi-agent and multi-turn settings:
- **Sycophancy**: single agents trained with RLHF converge toward user-preferred answers even when incorrect — a one-agent "groupthink" against the training signal
- **Echo chamber dynamics in multi-agent systems**: when multiple LLM agents share the same base model, they tend to converge on similar outputs and reinforce each other's errors rather than providing genuine independent review
- **Context contamination**: early turns in a conversation bias all subsequent turns; the agent "conforms" to its own prior context
- **Consensus collapse**: in orchestrator/sub-agent architectures, sub-agents often defer to the orchestrator's framing rather than providing genuine independent analysis

Mitigation: architectural diversity (different models, different prompting), explicit adversarial roles, structured disagreement protocols. See [[Wiki/synthesis/sats-for-llm-agents|SATs for LLM Agents]].

---

## SATs That Control For This Bias

- **[[Wiki/concepts/devils-advocacy|Devil's Advocacy]]** — institutionalizes the role of the dissenter; gives explicit permission and expectation to challenge consensus
- **[[Wiki/concepts/team-a-team-b|Team A/Team B]]** — structurally separates two independent analysis teams, preventing social pressure from operating across them
- **[[Wiki/concepts/brainstorming|Brainstorming]]** — deferred-judgment rules temporarily suspend the social pressure toward consensus that groupthink exploits
- **[[Wiki/concepts/red-team-analysis|Red Team Analysis]]** — assigns an explicit adversarial role, legitimizing challenge to the group's view

---

## Key References

- Janis, I. L. (1972). *Victims of Groupthink*. Houghton Mifflin.
- Janis, I. L. (1982). *Groupthink: Psychological Studies of Policy Decisions and Fiascoes* (2nd ed.). Houghton Mifflin.
- Kahneman, D. (2011). *Thinking, Fast and Slow*. (Chapter 23: "The Outside View")
- [[Wiki/sources/riley-sats-cybersecurity-2024|Riley: SATs in Cybersecurity (2024)]] — names groupthink as a target bias for cybersecurity SAT application

---

## See Also

[[Wiki/concepts/cognitive-bias|Cognitive Bias]] | [[Wiki/concepts/confirmation-bias|Confirmation Bias]] | [[Wiki/concepts/motivated-reasoning|Motivated Reasoning]] | [[Wiki/concepts/mind-set|Mind-Set]]
