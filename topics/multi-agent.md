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

**Other candidates/background:** sparse communication topology; Du et al. as a
compact baseline; G-Designer for automated graph design; SAGA for authenticated
inter-agent contact rather than general delegation.

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

## Final-selection v3 update — 2026-08-27

Only [Multi-Agent Resilience](../literature/papers/multi-agent-resilience.md)
remains in the final primary set. Information Propagation Effects stays a strong
candidate, but its causal-topology lesson is partially preserved by the retained
fault/topology comparisons, while correctness required the slot. The targeted
preferred-group search found sparse-debate, learned-topology, and security
alternatives but no equally direct combination of controlled fault injection,
architecture comparison, and remediation. [SAGA](../literature/papers/saga.md)
is promoted in the correctness unit for the separate problem of identity,
authorization, and delegation across agents.

## Reading-list v4 update — 2026-08-27

The dedicated block now uses three primary mechanisms:

- [Information Propagation Effects](../literature/papers/information-propagation-topologies.md)
  for causal intervention on error and insight diffusion;
- [CARD](../literature/papers/card.md) for condition-aware topology generation
  and runtime adaptation;
- [Multi-Agent Resilience](../literature/papers/multi-agent-resilience.md) for
  controlled faulty nodes and challenge/inspection containment.

[State Delta Encoding](../literature/papers/state-delta-trajectory.md) is a real
communication protocol but remains background because it assumes white-box
hidden-state transfer and does not address concurrent shared state. The audit
still found no mature peer-reviewed protocol for consistency, synchronization,
races, or transactional shared memory among tool-using agents.

## Reading-list v5 update — 2026-08-27

The primary pair is now [Information Propagation Effects](../literature/papers/information-propagation-topologies.md)
and [LLM-as-Scheduler](../literature/papers/llm-as-scheduler.md): causal influence
over a graph versus dynamic allocation of workflow stages. CARD becomes a
candidate because it overlaps topology; Multi-Agent Resilience remains a strong
fault-injection alternative because its Inspector and Challenger do not create
an independent consistency or recovery protocol.

[AMA](../literature/papers/ama-adaptive-memory.md) was rejected as the missing
shared-state paper: update/deletion roles and model-judged consistency do not
define versions, conflicts, isolation, or concurrency. [H-MAS](../literature/papers/h-mas.md)
was rejected as a controller-role serving system; Agentix is the direct
agent-program runtime. Shared-state consistency remains an explicit gap.

## Final adversarial review — 2026-08-28

Only [Information Propagation Effects](../literature/papers/information-propagation-topologies.md)
remains a primary. Its forced-answer intervention and TCTE metric are limited
but technically meaningful, and EIB-Learner turns the error/insight tradeoff into
a graph-selection mechanism. LAS is cut because routing stages in a fixed
workflow does not add multi-agent coordination semantics.

[SAGA](../literature/papers/saga.md) moves to authenticated-contact background:
its tokens and provider registry are real security mechanisms, but they do not
encode attenuated task delegation. CARD and Multi-Agent Resilience remain
alternatives, not replacements; neither supplies the missing shared-state,
consistency, or independent fault-recovery semantics. One primary is an honest
reflection of the current literature's maturity.

## Supplied-list correctness audit — 2026-08-28

[TraceFix](../literature/papers/tracefix.md) is the first inspected published
paper to materially change the shared-state/coordination gap. It synthesizes an
explicit topology and PlusCal protocol, repairs TLC counterexamples, and derives
a runtime coordination interface. The contribution is distinct from Information
Propagation: one analyzes causal diffusion over communication graphs; the other
checks interleavings, mutual exclusion, channel cleanup, and deadlock.

TraceFix is selected as the second primary in this area. Its bounded checks omit
task semantics and liveness, and the current runtime monitor enforces topology
membership rather than the verified state-machine step order. Those limits make
it a particularly useful correctness reading rather than evidence that general
shared-state consistency is solved.

## Ingredient-level architecture audit — 2026-08-28

The current pair remains the strongest **mechanism** pair, but it is not a full
architecture tour. Information Propagation studies communication topology and
TraceFix studies protocol interleavings; neither explains role formation,
heterogeneous agent construction, or dynamic task allocation.

- [Evolving Orchestration](../literature/papers/evolving-orchestration.md) is the
  best recent high-level architecture companion inspected. Agents combine a
  model, reasoning pattern, and tool set; a learned central orchestrator selects
  them as state evolves, inducing chains, trees, graphs, and cycles.
- [MaAS](../literature/papers/maas.md) makes a multi-agent architecture a
  query-dependent DAG drawn from an operator supernet. It is stronger on
  architecture search and cost allocation, weaker on distinct-agent semantics.
- [GPTSwarm](../literature/papers/gptswarm.md) provides the cleanest recursive
  computational-graph abstraction, but is older and optimizes only prompts and
  communication edges.
- [Flow](../literature/papers/flow.md) exposes subtasks, dependencies, roles,
  parallelism, and repair in an AOV graph, but its small evaluation and
  model-owned checks do not clear the primary-reading bar.

[Large Language Models Miss the Multi-agent Mark](../literature/papers/llms-miss-multi-agent-mark.md)
is the right short framing: social agency, structured environments,
coordination/communication protocols, and emergent behavior. It also explains
why no inspected empirical LLM paper supplies every ingredient. Use Evolving
Orchestration to show organization, Information Propagation to explain
communication, and TraceFix to expose coordination correctness; do not pretend
that one paper is a complete multi-agent stack.

## Reading-list v6 resolution — 2026-08-28

The multi-agent unit is capped at one week. Evolving Orchestration, Information
Propagation, and TraceFix are selected as organization → communication effects →
coordination correctness. Agentless moves to repair-week background because it
is an autonomy control, not a distinct-agent architecture mechanism. This keeps
agent plus multi-agent material to two weeks total.

## Reading-list v7 placement — 2026-08-29

The scheduled multi-agent block is now exactly one week:

- [Evolving Orchestration](../literature/papers/evolving-orchestration.md) covers
  heterogeneous agent construction, dynamic selection, and induced topology.
- [Information Propagation](../literature/papers/information-propagation-topologies.md)
  covers causal insight/error diffusion and topology optimization.

[TraceFix](../literature/papers/tracefix.md) remains selected but moves to the
correctness/runtime-assurance block. Its TLA+/TLC counterexample-repair loop is
a coordination-correctness mechanism, not the missing ingredient-level
architecture explanation. This preserves organization, communication, and
checked coordination as three distinct lessons without consuming a third week.
