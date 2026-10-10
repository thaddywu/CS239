# Human Oversight and Control Transfer

## Scope and organizing claim

Human involvement is not a correctness oracle. A useful oversight design must
specify what the person sees, when control transfers, which actions are still
reversible, what delay and cognitive effort cost, and how the runtime binds an
approval to the action that eventually executes.

## Mechanism map

- [Plan-Then-Execute](../literature/papers/plan-then-execute.md) separates user
  involvement in planning from stepwise execution approval. Its 2×2 study shows
  that involvement can repair errors but does not reliably calibrate trust,
  increases cognitive load, and can damage a correct plan.
- [Towards Adjustable Autonomy](../literature/papers/towards-adjustable-autonomy.md)
  models transfer-of-control strategies as sequential decisions over response
  probability, wait cost, decision quality, and team miscoordination.
- [AgentSpec](../literature/papers/agentspec.md) enforces stateful action policy,
  while [SAGA](../literature/papers/saga.md) provides authenticated inter-agent
  contact as background. Neither establishes that the displayed request is
  comprehensible or that approval remains fresh until commit.
- [Temporary Authority, Permanent Effects](../literature/papers/temporary-authority-permanent-effects.md)
  makes approval freshness and binding explicit at commit time, but remains a
  preprint.

## Reading decision

**Primary:** Plan-Then-Execute, because it directly studies modern LLM-agent
planning/execution control and supplies a valuable negative result.

**Alternative:** Towards Adjustable Autonomy, when the goal is a formal policy
for choosing when and to whom control should transfer.

**Rejected pattern:** generic trust surveys or interfaces that add an approval
button without testing information quality, workload, action binding, or task
outcomes.

## Current assessment and gaps

- Literature maturity: **medium**; empirical studies are improving, but formal
  control-transfer ideas have not yet been fully rebuilt for LLM agents.
- Approval must be bound to a concrete action, world-state version, authority
  epoch, and expiry condition; narrative summaries are insufficient.
- Selective escalation needs risk/uncertainty signals that do not simply ask the
  same model to judge itself.
- Multi-human responsibility, interruptibility during long-running execution,
  and post-effect reconciliation remain undercovered.

## Reading-list v5 update — 2026-08-27

Plan-Then-Execute remains the primary on execution-time oversight.
[ARTEMIS](../literature/papers/artemis.md) adds a complementary, bounded form of
human involvement: users classify low-complexity distinguishing traces, and a
balanced algorithm minimizes the number of questions. Neither paper binds a
human judgment to the exact action and world-state version that later commits.
Adjustable Autonomy and Sagas are short instructor context; commit-time approval
freshness remains a modern research gap.

## Supplied-list update — 2026-08-28

[Semantic Commit](../literature/papers/semantic-commit.md) is selected as the
second primary for a different correctness boundary: persistent natural-
language intent changes over time. Its knowledge-graph retrieval and mixed-
initiative interface turn memory/rule updates into semantic impact analysis and
local human review. The small datasets and 12-person study remain important
limits, while Plan-Then-Execute continues to cover execution-time oversight.

## Reading-list v7 placement — 2026-08-29

[Semantic Commit](../literature/papers/semantic-commit.md) is now the sole
scheduled HCI/intent primary. Its knowledge-graph retrieval, impact analysis,
conflict detection, scoped resolution, and mixed-initiative review provide a
mechanism that can sustain an SE discussion about evolving specifications.

[Plan-Then-Execute](../literature/papers/plan-then-execute.md) moves to strong
supporting evidence. Its 2x2 study remains valuable negative evidence that
approval can add errors and workload without calibrating trust, but the study is
the contribution; the interface is not deep enough to consume one of 16
mechanism-first discussions.
