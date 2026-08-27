# Agent Architecture and Runtime

## Scope and organizing claim

An agent is not just a prompted model. The architecture assigns responsibility
among a generative model, action interface, state/context manager, execution
runtime, tools, planner, validator, and policy monitor. The best literature in
this cluster makes one of those boundaries an experimental variable.

## Mechanism map

### Action representation

- [Toolformer](../literature/papers/toolformer.md) learns call placement,
  arguments, and result incorporation from loss-filtered self-labels.
- [CodeAct](../literature/papers/codeact.md) uses stateful executable Python as
  one compositional action language.
- [SWE-agent](../literature/papers/swe-agent.md) takes the opposite route: a
  small LM-specific command set, bounded observations, and guardrails.

This yields a useful design triangle: **learned selection vs. expressive action
language vs. constrained interface**. No point dominates on capability,
inspectability, cost, and confinement simultaneously.

### Runtime and programming model

- DSPy separates declarative LM modules from metric-driven compilation. Its
  contribution is a programming model, not an agent loop per se.
- OpenHands standardizes a sandbox/runtime and reusable agent skills across
  tasks. It is a valuable artifact, but its paper isolates mechanisms less
  cleanly than SWE-agent.
- ReAct remains the common observation–thought–action vocabulary, but is now a
  short prerequisite rather than the deepest reading.

### Planning and verification

- LATS embeds model proposals and value estimates in tree search.
- [LLM-Modulo planning](../literature/papers/llm-modulo-planning.md) argues that
  models should propose while external model-based components check and plan.
- [CodePlan](../literature/papers/codeplan.md) is the strongest software-specific
  instance: dependencies and change-impact analysis grow an edit-obligation DAG.

### Memory and state

- MemGPT makes context tiers, interrupts, and model-directed movement explicit,
  but remains a preprint with largely untyped memory.
- LEGO-Prover is the stronger systems lesson: only verifier-accepted lemmas enter
  a reusable skill store. “Memory” quality depends on entry invariants, not just
  retrieval.

## Reading decisions

**Strong:** CodeAct, SWE-agent, Toolformer, LLM-Modulo. CodePlan and LEGO-Prover
are cross-listed in their more specific weeks.

**Other candidates:** ReAct, DSPy, LATS, MemGPT, OpenHands.

**Weaker alternatives:** broad framework papers whose main contribution is a
role prompt or product integration. These are not rejected as software, but they
do not isolate a reusable architectural mechanism.

## Current assessment

- Literature maturity: **high for action interfaces and tool loops; medium for
  explicit state and memory; low for standardized tool protocols**.
- Technical depth: high when interfaces, compilers, or validators are the object
  of study; medium for generic planning prompts.
- Course suitability: very high as the opening week because its responsibility
  boundaries recur everywhere else.

## Gaps and next searches

- Peer-reviewed comparisons of tool protocol semantics, versioning, capability
  discovery, and schema evolution—not protocol announcements.
- Durable state models with provenance, invalidation, transactions, and recovery.
- Matched experiments separating a better base model from a better harness.
- Citation-chain follow-up from SWE-agent's ACI ablations and from verified
  memory systems, especially negative interface results.
