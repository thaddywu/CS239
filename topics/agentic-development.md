# Agent-Based Software Development

## Scope

This is the integration topic: issue interpretation, repository navigation,
editing, execution, testing, and review. Its intellectual value comes from
comparing control and evidence, not from tracking a fast-moving leaderboard.

## Mechanism map

### Interactive generalists

[SWE-agent](../literature/papers/swe-agent.md) attributes gains to an
agent-computer interface and supports that claim with component ablations.
OpenHands generalizes the runtime, sandbox, browser, and skills across tasks; it
is a significant reusable artifact but a less focused causal reading.

### Software-specific guidance

[AutoCodeRover](../literature/papers/autocoderover.md) uses program structure and
fault localization. RepairAgent constrains a repair-specific loop with an FSM.
[CodePlan](../literature/papers/codeplan.md) propagates edits through dependency
and change-impact relations. These systems make software-engineering knowledge
part of control rather than only prompt context.

### Deterministic control condition

[Agentless](../literature/papers/agentless.md) fixes localization, sampling, and
validation into a staged pipeline. It demonstrates that autonomy must be compared
against a carefully engineered workflow under matched models, budgets, and
evidence.

[Murakkab](../literature/papers/murakkab.md) adds a deployment-side control: even
when workflow logic is fixed, a runtime can optimize model/hardware bindings and
adapt execution under SLOs. It should not be credited as better coding reasoning.

### Multi-agent process metaphors

[MetaGPT](../literature/papers/metagpt.md) and
[ChatDev](../literature/papers/chatdev.md) encode software-company roles. They are
rejected as primary readings because multi-agent necessity is not isolated and
greenfield toy generation weakly represents maintenance.

## Reading decisions

**Strong:** SWE-agent, AutoCodeRover, Agentless, CodePlan. These already live in
architecture, repair, and repository weeks; a separate “coding agents” week
would duplicate them.

**Other candidates:** RepairAgent, OpenHands, SWE-bench as evaluation context.
Murakkab is a strong systems cross-listing rather than another coding agent.

**Rejected as primary:** MetaGPT, ChatDev, and leaderboard reports without
mechanism ablations, cost, reproducibility, or patch-quality audits.

## Current assessment

- Literature maturity: **high but benchmark-concentrated**.
- Technical depth: high in interface, analysis, and planning papers; variable in
  end-to-end framework papers.
- Course suitability: very high as a thread running through the course, not as a
  disconnected framework survey.

## Gaps and next searches

- Human review interfaces and whether traces support calibrated oversight.
- Ambiguous requirements, escalation, and conflict between issue text/tests/docs.
- Long-lived branches: dependency updates, merge conflicts, CI, deployment, and
  rollback—not one isolated patch.
- Cross-language, non-Python, and non-GitHub evaluation.
- Reproducible matched comparisons that hold model, token budget, retrieved
  context, and test access constant.

## Due diligence audit — 2026-08-27

### Previously believed

Software-development agents were mature but SWE-bench concentrated; the best
course story was an interface/analysis/planning/pipeline spectrum rather than a
tour of coding-agent products or multi-agent roles.

### New papers checked

- Checked IGSIL (ASE 2025), Amur (ASE 2025), CausalRepair (ISSTA 2026), AROP
  (ICSE 2026), and current ICSE/FSE/ASE repair and localization sessions.
- Fully inspected Murakkab for the boundary between agent workflow logic and
  deployment optimization.
- Rechecked the author/citation chains around Agentless, AutoCodeRover,
  RepairAgent, SWE-agent, and CodePlan for a matched agent-versus-structured-
  pipeline result that would reverse their current roles.

### Important additions

Murakkab is the only important cross-listing: **very high technical depth**, but
its contribution is workflow serving and resource/SLO optimization rather than
repository reasoning or repair quality.

### Stronger replacements

No stronger peer-reviewed alternative found in this audit for SWE-agent's ACI
evidence, AutoCodeRover's SE-guided loop, Agentless's deterministic control, or
CodePlan's dependency-driven planning.

### Judgment

**UPHELD.**

### Why

New repair/localization systems add variants but do not overturn the control
spectrum or isolate autonomy more cleanly. The topic remains highly suitable as
a cross-course thread; allocating a separate “coding agents” survey week would
still duplicate stronger mechanism-specific sessions.
