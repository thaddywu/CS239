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
- [G-Designer](../literature/papers/g-designer.md) learns a task-adaptive graph
  with a variational graph autoencoder, optimizing performance, communication
  cost, and a measured adversarial condition.

The emerging principle is **selective communication**: fully connected graphs
maximize both access and contamination.

### Fault containment and review

[Multi-Agent Resilience](../literature/papers/multi-agent-resilience.md) injects
faults into different structures. Hierarchy, Challenger, and Inspector mechanisms
make recovery measurable. An Inspector remains an untrusted model component,
however; it is not equivalent to an external verifier or reference monitor.

[SAGA](../literature/papers/saga.md) adds a different coordination layer:
provider-mediated identity and cryptographic authorization tokens for inter-agent
communication. It governs who may talk, not whether communicated content is true.

### Role workflows

[MetaGPT](../literature/papers/metagpt.md) and
[ChatDev](../literature/papers/chatdev.md) encode software-company roles and
SOP/chat chains. They are useful historical artifacts but do not give a matched
single-agent workflow control or a causal account of coordination.

## Reading decisions

**Strong:** Information Propagation Effects; Multi-Agent Resilience.

**Other candidates:** sparse communication topology; Du et al. as a compact
baseline; G-Designer for automated graph design; SAGA for authorization and
delegation protocols.

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

## Due diligence audit — 2026-08-27

### Previously believed

Topology and injected-fault studies supported a good seminar, while role-playing
frameworks dominated volume and distributed-systems-grade consistency,
authorization, and Byzantine protocols remained sparse.

### New papers checked

- Fully inspected G-Designer (ICML 2025) and SAGA (NDSS 2026).
- Checked CONSENSAGENT, recent ACL multi-agent strategy papers, and the NeurIPS
  position *Large Language Models Miss the Multi-agent Mark*; these did not add
  a stronger coordination mechanism.
- Followed topology/fault citations and searched consensus, task allocation,
  shared state, communication cost, and Byzantine terms across AI, systems, and
  security venues.

### Important additions

- [G-Designer](../literature/papers/g-designer.md): learned task-adaptive sparse
  graphs; **high technical depth**, useful as an optimizer-versus-explanation
  contrast.
- [SAGA](../literature/papers/saga.md): cryptographic inter-agent authorization;
  **very high technical depth**, useful for protocol and trust-boundary debate.

### Stronger replacements

Neither addition replaces the primary pair. Information Propagation better
explains causal diffusion; Multi-Agent Resilience better isolates fault
containment. No stronger peer-reviewed alternative found in this audit for
those two classroom roles.

### Judgment

**UPHELD.**

### Why

The audit adds learned topology and authorization, so the design space is less
persona-centric. It still finds no mature shared-state consistency or Byzantine
tool-execution protocol, and the existing explanatory/fault-injection pair
remains the strongest basis for one discussion-rich week.
