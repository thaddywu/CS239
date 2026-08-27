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
