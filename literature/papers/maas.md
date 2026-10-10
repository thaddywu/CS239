# Multi-agent Architecture Search via Agentic Supernet

## Decision

**Candidate.** Primary source: [ICML 2025 proceedings](https://proceedings.mlr.press/v267/zhang25bi.html).

## Mechanism and evidence

MaAS represents a multi-agent system as a DAG of agentic operators and learns a
probabilistic multi-layer supernet. It samples a query-specific architecture,
trading answer utility against model, tool, and token cost; early exit and
textual-gradient evolution adapt the operator prompts and gates. Across six
math, coding, and tool-use benchmarks, the paper reports 6--45% of comparison
systems' inference cost and modest-to-large accuracy gains.

The abstraction makes topology, operator choice, and cost allocation explicit,
but most operators are reasoning patterns such as debate, refinement, and
self-consistency. The library is pre-specified, and the experiments do not model
shared memory, concurrent external effects, authority, or protocol correctness.
Ablations establish the search machinery, not which multi-agent ingredients are
independently necessary.

## Course role

Useful architecture-search comparison, especially against AgentSquare. It does
not replace Information Propagation or TraceFix because it optimizes a workflow
without explaining error diffusion or checking coordination semantics.

