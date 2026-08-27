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
- [Murakkab](../literature/papers/murakkab.md) makes a workflow a declarative
  program whose model, hardware, and execution configuration are jointly
  optimized and adapted under SLOs. It supplies the missing systems-runtime
  design point.
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
  but remains a preprint with largely untyped memory and is no longer the best
  primary evidence.
- [Agentic Memory](../literature/papers/agentic-memory.md) exposes long- and
  short-term memory operations as actions and learns store/retrieve/update/
  summarize/discard policies with reinforcement learning.
- [Memory Management Impacts](../literature/papers/memory-management-impact.md)
  supplies the needed negative control: similar retrieved experience can be
  imitated even when erroneous or misaligned, and deletion helps only with a
  trustworthy quality signal.
- LEGO-Prover is the stronger systems lesson: only verifier-accepted lemmas enter
  a reusable skill store. “Memory” quality depends on entry invariants, not just
  retrieval.

## Reading decisions

**Strong:** CodeAct, SWE-agent, Toolformer, LLM-Modulo, Murakkab, and the two ACL
2026 memory papers. CodePlan and LEGO-Prover are cross-listed in their more
specific weeks.

**Other candidates:** ReAct, DSPy, LATS, MemGPT, OpenHands.

**Weaker alternatives:** broad framework papers whose main contribution is a
role prompt or product integration. These are not rejected as software, but they
do not isolate a reusable architectural mechanism.

## Current assessment

- Literature maturity: **high for action interfaces, tool loops, workflow
  optimization, and memory policy; low for standardized tool protocols and
  transactional state**.
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

## Due diligence audit — 2026-08-27

### Previously believed

Interfaces, tool use, and external planning were mature, but memory/context
management had interesting designs without enough peer-reviewed mechanism and
failure evidence for an independent seminar discussion.

### New papers checked

- Fully inspected AgeMem and the ACL 2026 experience-following study. Also
  screened Memory-R1, HiAgent, RMM, THEANINE, Hindsight, ARTEM, and CA3Mem.
- Inspected OSDI 2026 agent-system papers and found Murakkab; checked adjacent
  serving/training papers but excluded them when they optimized model inference
  rather than the agent workflow abstraction.
- Rechecked MemGPT's citation/publication chain; it remains an arXiv preprint.

### Important additions

- [Agentic Memory](../literature/papers/agentic-memory.md): learned unified LTM/
  STM actions; **high technical depth**, suitable as a constructive primary.
- [Memory Management Impacts](../literature/papers/memory-management-impact.md):
  controlled addition/deletion and error propagation; **high technical depth**,
  suitable as the adversarial/negative primary.
- [Murakkab](../literature/papers/murakkab.md): declarative orchestration plus
  cross-layer optimization; **very high technical depth**, suitable for a
  systems-runtime discussion.

### Stronger replacements

AgeMem replaces MemGPT as the preferred constructive memory primary; MemGPT is
retained as architectural history. Murakkab does not replace SWE-agent or
CodeAct because it studies deployment/runtime optimization rather than the
agent-computer action interface.

### Judgment

**WEAKENED overall: memory OVERTURNED; harness, tools, and planning UPHELD.**

### Why

Memory now has two complementary, formally published readings—one designs a
learned state policy and one isolates persistent-state failure—plus verified
memory in LEGO-Prover. That is enough for a focused classroom session, although
transactions, provenance, and cross-session security remain open. No stronger
peer-reviewed alternative found in this audit for the current interface and
planning primaries.
