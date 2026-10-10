# Plan-Then-Execute: An Empirical Study of User Trust and Team Performance When Using LLM Agents As A Daily Assistant

## Decision

**Strong alternate after the v7 audit.** Primary source: [CHI 2025
DOI](https://doi.org/10.1145/3706598.3713218).

## Mechanism and evidence

The interface separates editable stepwise planning from action-by-action
execution. During execution, users may approve, give feedback, or manually
specify an API action. A 2×2 study with 248 participants compares automatic
versus user-involved planning and execution over six simulated daily-assistant
tasks with different risk, complexity, and initial-plan quality.

Human involvement sometimes repairs a bad plan or action, but it does not
consistently improve performance or calibrated trust; editing can damage an
already-correct plan. Planning involvement increases mental/temporal demand and
frustration, while execution involvement increases effort. The simulated tools,
fixed one-step-to-one-action design, and six tasks limit transfer, but the
negative result is precisely why the paper is useful: approval is not a free or
reliable correctness oracle.

## Course role

This remains strong empirical HCI evidence, but the 2x2 user study is the main
contribution and the plan/approval interface is not a sufficiently deep new
agent mechanism for one of only 16 primary discussions. V7 gives the HCI-SE
slot to Semantic Commit's explicit impact-analysis and conflict-resolution
pipeline; use Plan-Then-Execute as supporting evidence in that discussion.
