# Agents for Systems, Science, and Hardware

## Scope and selection test

Domain impact alone does not make a core architecture paper. A central candidate
should expose a reusable closed-loop mechanism—hypothesis or plan, consequential
action, observation, validation, and recovery—not merely attach tools to ReAct.

## Mechanism map

### Scientific laboratory loops

Coscientist combines planning, web/document search, code execution, and
laboratory APIs and demonstrates real reaction execution/optimization. ChemCrow
packages 18 expert chemistry tools and includes robotic synthesis. Both prove
that physical action changes the safety and evaluation stakes; neither cleanly
isolates a new general runtime mechanism.

### Experimental software systems

MLAgentBench makes ML experimentation executable across 13 tasks and exposes
recency, hallucination, and long-horizon planning failures. It is a useful
benchmark, not the preferred architecture reading.

OS-Copilot proposes planner/configurator/actor components and accumulated skills,
but its workshop/preprint evidence and broad claims are too weak for a primary
slot.

### Hardware and EDA

ChatEDA drives an RTL-to-GDSII tool flow from natural language and is the closest
hardware candidate. [ChipNeMo](../literature/papers/chipnemo.md) contributes
domain adaptation and retrieval, not an agent loop, and is explicitly rejected
as an “agent” primary reading.

## Reading decisions

**No strong primary candidate yet.** This is a substantive result, not an empty
slot to fill.

**Other candidates:** Coscientist (preferred physical-loop case), ChemCrow,
MLAgentBench, ChatEDA.

**Rejected as primary:** OS-Copilot due publication/evidence and mechanism
isolation; ChipNeMo because its contribution is domain-adapted language models.

## Current assessment

- Literature maturity: **application-rich but mechanism-thin; hardware is low**.
- Technical depth: high within chemistry/EDA domains, medium for reusable agent
  abstractions.
- Course suitability: medium as a comparative case or student-led session, not
  currently justified as a required standalone week.

## Gaps and next searches

- Transactional, auditable laboratory actions and safe interruption/recovery.
- Reproducible comparisons against non-agent automated experimentation.
- Hardware loops that use formal equivalence, simulation, timing, power, and
  physical-design feedback as explicit validators.
- Network/OS agents with real fault containment and benchmarkable side effects.
- Citation chaining from Coscientist and ChatEDA toward follow-up systems papers,
  while rejecting work whose only novelty is a domain prompt/tool list.
