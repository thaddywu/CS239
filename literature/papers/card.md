# CARD: Towards Conditional Design of Multi-Agent Topological Structures

## Decision

**Selected for v4.** Primary source: [ICLR 2026 OpenReview](https://openreview.net/forum?id=JgvJdICc6P).

## Mechanism and evidence

CARD represents agents as a directed graph and uses separate profile and
environment-condition channels in a conditional variational graph generator.
Its objective trades task utility against condition-aware communication cost;
at runtime, changed model, tool, or source-quality signals produce new edges
without retraining. On HumanEval, MATH, and MMLU it outperforms fixed,
prompt-conditioned, and learned-static topology baselines on average. Ablations
show prompt-level condition injection can hurt while graph-level conditioning
produces non-negative gains across the reported model/task pairs.

The environmental changes are simulated, benchmark tasks have no durable
shared state, and the graph chooses who communicates without defining
consistency or concurrent-effect semantics. It belongs beside causal
propagation and fault-injection papers, not as a complete coordination stack.

## Reading-list v5 decision

**Candidate, no longer primary.** Conditional graph generation overlaps the
retained causal-topology paper and still does not specify task allocation,
shared-state consistency, or effect coordination. LAS supplies the more distinct
dynamic scheduler.
