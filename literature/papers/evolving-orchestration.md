# Multi-Agent Collaboration via Evolving Orchestration

## Decision

**Selected for reading-list v6.** Primary source:
[NeurIPS 2025 proceedings](https://proceedings.neurips.cc/paper_files/paper/2025/hash/f1320d2e2842169c6fc89dcbd80e94d0-Abstract-Conference.html).

## Mechanism and evidence

The paper defines an agent as a tuple of model, reasoning pattern, and tool set.
A centralized reinforcement-learned orchestrator selects and sequences agents
from that heterogeneous pool as task state evolves, inducing query-specific
chains, trees, graphs, and cycles. Experiments and topology analyses support the
claim that compact cyclic organizations can outperform static collaboration at
lower cost.

This is the most direct recent paper inspected for roles, heterogeneity,
dynamic allocation, and emergent topology in one mechanism. It still treats
collaboration mainly as a sequence of reasoning calls: there is no durable
shared state, concurrent effect model, access-control relation, or independently
checked coordination protocol.

## Course role

Best current high-level architecture companion for the multi-agent unit, but
not a substitute for its mechanism papers. Information Propagation explains
what communication transmits; TraceFix checks whether a coordination protocol
can interleave safely. Evolving Orchestration explains who runs next and why.

In v6 it replaces Agentless in the multi-agent week. Agentless moves to the
repair unit as an instructor control rather than disappearing from the course.
