# Agent Architecture and Runtime

## Scope and organizing claim

An agent is not just a prompted model. The architecture assigns responsibility
among a generative model, action interface, state/context manager, execution
runtime, tools, planner, validator, and policy monitor. The best literature in
this cluster makes one of those boundaries an experimental variable.

## Overview and survey layer

No survey should replace a mechanism-bearing primary, but a short framing
reading now fills the missing map above AgentSquare:

- [From Language Models to Agentic AI](../literature/papers/from-language-models-to-agentic-ai.md)
  is the closest current one-paper engineering overview. It separates
  perception, memory, reasoning/planning, tool interface, actuation, and
  feedback/oversight, then adds autonomy, tool-use, collaboration, and
  safety/governance axes. Its August 2026 publication and synthesis-level
  evidence make it instructor framing rather than a student-led primary.
- [Wang et al.'s autonomous-agent survey](../literature/papers/survey-llm-autonomous-agents.md)
  remains the cleanest established single-agent module vocabulary: profile,
  memory, planning, and action.
- [Guo et al.'s multi-agent survey](../literature/papers/llm-multiagents-survey.md)
  is the compact companion for environment interfaces, profiling,
  communication structure/content, and capability acquisition.
- [Xi et al.](../literature/papers/rise-potential-llm-agents-survey.md) is the
  encyclopedic brain-perception-action reference; [Khapre et al.](../literature/papers/agentic-ai-systems-survey.md)
  is the broad topology/cognition/trust reference. Neither is concise enough
  for a primary discussion.

The resulting teaching stack is **survey map -> AgentSquare's composable
ingredient/search abstraction -> SWE-agent's environment boundary**. Multi-agent
organization and communication remain technical follow-ons rather than a third
overview week.

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
- Recheck whether the August 2026 engineering survey gains field uptake or a
  stronger revised version before the syllabus freezes; its current value is
  vocabulary coverage, not validated architectural evidence.

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

## Final-selection v3 update — 2026-08-27

The final primary set keeps SWE-agent, CodeAct, and Murakkab as three distinct
layers: guarded ACI, executable action language, and workflow/runtime optimizer.
Memory remains technically mature, but neither ACL 2026 memory paper receives a
standalone day. AgeMem and the experience-following study move to tutorial and
cross-cutting state-correctness background because transaction, recovery,
authority, and oversight had larger uncovered gaps. Persistent state is now
revisited through CodePlan's explicit plan state, Beldi's logged transactional
state, AgentSpec's monitor state, and the final correctness scenario.

## Reading-list v4 update — 2026-08-27

The compact architecture week now assigns only SWE-agent and CodeAct. Murakkab
remains technically strong systems background, but resource/SLO optimization
across models and hardware does not answer the revised questions about the
agent-computer interface, control placement, shared state, or coordination.
Frameworks and protocols remain tutorial material unless their papers isolate a
comparable abstraction.

## Reading-list v5 update — 2026-08-27

[Agentix](../literature/papers/agentix.md) joins SWE-agent and CodeAct. It adds
the missing program-runtime layer: PLAS schedules by cumulative attained service
and ATLAS follows distributed critical paths. [LLM-as-Scheduler](../literature/papers/llm-as-scheduler.md)
is assigned in the coordination unit because it routes semantic workflow stages
rather than serving program calls. The current architecture sequence is thus
interface constraint → executable action language → whole-program runtime.

## Final adversarial review — 2026-08-28

The architecture sequence remains SWE-agent → CodeAct → Agentix. The first pair
still creates a real constrained-interface versus executable-action-language
tension; Agentix adds non-clairvoyant program and critical-path scheduling.

LAS is cut: its domain-trained gate and prompted JSON router do not model
resources, dependencies, concurrency, tools, or durable workflow state. The
Murakkab comparison does not displace Agentix: Murakkab is the broader
profile-guided model/hardware/SLO optimizer, while Agentix is the cleaner
runtime abstraction for arbitrary dynamic agent programs.

## Ingredient-level architecture audit — 2026-08-28

[AgentSquare](../literature/papers/agentsquare.md) materially changes the answer
to the narrower question “which paper teaches the ingredients of an agent?” It
standardizes planning, reasoning, tool use, and memory behind uniform interfaces
and searches their combinations. This is a more direct component map than the
current SWE-agent → CodeAct → Agentix sequence, which instead teaches interface
constraint, action representation, and runtime scheduling.

The result does not invalidate those three papers. AgentSquare fixes the
workflow and omits interface semantics, validators, policy monitors, and
durable-state correctness; its ablations chiefly justify the search algorithm,
not the independent necessity of each component. The strongest course design is
therefore a map-plus-deep-dives structure: AgentSquare for the module vocabulary,
SWE-agent for the environment boundary, and Agentix for execution/runtime. If
the primary count must remain fixed, CodeAct is the most overlapping member of
the existing architecture trio and hence the direct comparison point—not an
automatic rejection before the full 19-paper tradeoff is reopened.

[GPTSwarm](../literature/papers/gptswarm.md) and
[MaAS](../literature/papers/maas.md) remain architecture-search comparisons.
GPTSwarm supplies recursive computational graphs; MaAS supplies query-adaptive
operator DAGs and cost allocation. Neither gives as clear a single-agent module
taxonomy as AgentSquare.

## Reading-list v6 resolution — 2026-08-28

The architecture unit is capped at one week. AgentSquare, SWE-agent, and Agentix
are selected as module map → environment boundary → program runtime. CodeAct
moves to instructor comparison: still the strongest expressive-action-language
paper, but more overlapping with SWE-agent than AgentSquare's ingredient map.

## Reading-list v7 placement — 2026-08-29

The 16-meeting teaching list reduces the architecture week to AgentSquare and
SWE-agent: module vocabulary followed by the environment/interface boundary.
[Agentix](../literature/papers/agentix.md) remains a very-high-depth systems
alternate rather than a rejection. Its PLAS/ATLAS program scheduling would be
the first addition if serving performance receives a dedicated meeting;
[CodeAct](../literature/papers/codeact.md) remains the expressive action-language
comparison.
