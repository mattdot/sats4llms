---
type: entity
tags: [wiki/entity]
date_updated: 2026-05-20
entity_type: person
source_count: 1
---

# suprathermal

GitHub user (https://github.com/suprathermal) and author of the [[sources/suprathermal-ach-grounding-2024|ACH-Grounding]] open-source project — a working Python implementation of [[concepts/analysis-of-competing-hypotheses|ACH]] as an LLM grounding mechanism.

## Contributions

- **ACH-Grounding** (https://github.com/suprathermal/ACH-Grounding) — a hybrid LLM + classical-algorithm implementation that uses LLMs only to fill matrix cells (per-evidence × per-hypothesis judgments) while delegating combinatorial synthesis to deterministic code.

## Why It Matters Here

This author independently arrived at the same architectural conclusion as [[entities/scott-roberts|Scott Roberts]]: **multi-step ACH with externalized synthesis is the working pattern; single-prompt ACH is unreliable.** Two independent implementations converging on the same design is empirical evidence for the principle.

## Sources

- [[sources/suprathermal-ach-grounding-2024|ACH-Grounding (GitHub)]]
