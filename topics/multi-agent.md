# Multi-Agent Systems

## Scope and threshold

Multiple model calls are not automatically a multi-agent mechanism. A paper
belongs at the center only if it studies decomposition, topology, aggregation,
shared state, incentives, fault containment, or another property that changes
because actors are distinct.

## Mechanism map

### Debate and aggregation

Du et al. is the canonical multi-agent debate baseline: independent answers are
exchanged and revised before aggregation. Its gains are not sufficient evidence
for interaction, because *Large Language Models Cannot Self-Correct Reasoning
Yet* finds matched-budget debate can collapse to self-consistency effects.

### Communication topology

- Sparse-debate work establishes connectivity as a cost/performance variable.
- [Information Propagation Effects](../literature/papers/information-propagation-topologies.md)
  introduces a counterfactual influence metric, separates useful insight from
  error diffusion, and learns moderately sparse task-specific graphs.

The emerging principle is **selective communication**: fully connected graphs
maximize both access and contamination.

### Fault containment and review

[Multi-Agent Resilience](../literature/papers/multi-agent-resilience.md) injects
faults into different structures. Hierarchy, Challenger, and Inspector mechanisms
make recovery measurable. An Inspector remains an untrusted model component,
however; it is not equivalent to an external verifier or reference monitor.

### Role workflows

[MetaGPT](../literature/papers/metagpt.md) and
[ChatDev](../literature/papers/chatdev.md) encode software-company roles and
SOP/chat chains. They are useful historical artifacts but do not give a matched
single-agent workflow control or a causal account of coordination.

## Reading decisions

**Strong:** Information Propagation Effects; Multi-Agent Resilience.

**Other candidates:** sparse communication topology; Du et al. as a compact
baseline. G-Designer is a follow-up if the seminar wants automated graph design,
but it is redundant with the more explanatory propagation paper.

**Rejected as primary:** MetaGPT and ChatDev. The specific reason is not “they
use prompts”; it is failure to isolate why distinct agents are necessary.

## Current assessment

- Literature maturity: **medium and improving**. Topology/fault work is now
  technically credible; role-based software teams are overrepresented.
- Technical depth: high in causal graph/fault-injection work, medium in debate,
  low-to-medium in persona workflows.
- Course suitability: high if framed around communication and correlated
  failure, low if framed as a catalog of frameworks.

## Gaps and next searches

- Correlated faults from shared base models and shared retrieval stores.
- Consistency semantics for blackboards/shared memory and concurrent actions.
- Equal-compute single-agent, ensemble, and interactive multi-agent controls.
- Adversarial or Byzantine actors with real tool authority, not only bad text.
- Citation chain from ICML 2025 resilience and EMNLP 2025 propagation into
  distributed-systems venues and 2026 proceedings.
