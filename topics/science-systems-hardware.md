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

[Murakkab](../literature/papers/murakkab.md) is the first core systems paper in
this map: its declarative workflow representation enables profile-guided and
adaptive model/hardware orchestration under SLOs. It studies serving agentic
workflows, not a scientific or OS-controlling agent.

OS-Copilot proposes planner/configurator/actor components and accumulated skills,
but its workshop/preprint evidence and broad claims are too weak for a primary
slot.

### Hardware and EDA

ChatEDA drives an RTL-to-GDSII tool flow from natural language and is the closest
hardware candidate. [ChipNeMo](../literature/papers/chipnemo.md) contributes
domain adaptation and retrieval, not an agent loop, and is explicitly rejected
as an “agent” primary reading.

## Reading decisions

**Strong systems cross-listing:** Murakkab. **No strong science/hardware primary
that isolates a general mechanism yet.** This remains a substantive result, not
an empty slot to fill.

**Other candidates:** Coscientist (preferred physical-loop case), ChemCrow,
MLAgentBench, ChatEDA.

**Rejected as primary:** OS-Copilot due publication/evidence and mechanism
isolation; ChipNeMo because its contribution is domain-adapted language models.

## Current assessment

- Literature maturity: **high for agent-workflow serving, application-rich but
  mechanism-thin for science, and low for hardware agents**.
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

## Due diligence audit — 2026-08-27

### Previously believed

Systems/science/hardware was application-rich but lacked an isolated reusable
mechanism strong enough for a required week; hardware was the thinnest subarea.

### New papers checked

- Fully inspected Murakkab (OSDI 2026) and surveyed the OSDI/SOSP/NSDI/EuroSys/
  ASPLOS/ATC agent-related sessions around orchestration, serving, and recovery.
- Checked the Nature Communications 2025 AFM-agent evaluation, whose negative
  findings expose domain knowledge and prompting failures but contribute an
  evaluation case rather than a general runtime mechanism.
- Checked SAMPLE and follow-ups around autonomous laboratories plus current EDA
  work; excluded non-agent active learning and tool-chain applications that do
  not isolate an agent mechanism.

### Important additions

[Murakkab](../literature/papers/murakkab.md): declarative workflow/runtime and
cross-layer SLO optimization; **very high technical depth**, strong enough for a
systems lecture or cross-listing with architecture.

### Stronger replacements

Murakkab replaces the claim that the systems side has no strong primary, but it
does not replace Coscientist/ChatEDA as domain cases. No stronger peer-reviewed
alternative found in this audit for a mechanism-isolating science or hardware
agent primary.

### Judgment

**WEAKENED.**

### Why

One excellent OSDI runtime paper overturns the “mechanism-thin systems” part of
the combined judgment. Science and hardware still supply cases rather than a
diverse technical cluster, so the combined category does not merit replacing a
core week; Murakkab should instead appear in architecture/runtime.
