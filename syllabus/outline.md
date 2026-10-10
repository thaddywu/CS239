# CS239 Seminar Outline — Fall 2026 V7 Placement Draft

The current date-level schedule is [cs239-fall2026.md](cs239-fall2026.md): 16
paper-discussion meetings over Weeks 1--8. Full titles, discussion rationales,
and replacement candidates are in
[paper-list-fall2026.md](paper-list-fall2026.md). The audited
[reading-list-v7.md](reading-list-v7.md) records the 16-paper selection and the
paper-by-paper technical-depth review; v6 remains a historical research pool.

## Week 1 — Agent components and the computer interface

- AgentSquare
- SWE-agent

**Tension:** planning, reasoning, tools, and memory provide a component map, but
an operational software agent also needs an environment interface, feedback
semantics, validation, and confinement.

## Week 2 — Multi-agent organization and communication

- Multi-Agent Collaboration via Evolving Orchestration
- Understanding the Information Propagation Effects of Communication Topologies

**Short framing:** *Large Language Models Miss the Multi-agent Mark*.

**Tension:** dynamic orchestration chooses who acts and induces a collaboration
graph; causal intervention measures which insights and errors actually travel
through a graph. Neither supplies general concurrent shared-state, authority,
or external-effect semantics.

## Week 3 — Coding agents and agentic program analysis

- AutoCodeSherpa
- NESA

**Tension:** generated executable properties may guide issue repair, while
generated semantic relations may extend static analysis. Identify the
independent checker and incompleteness boundary in each.

## Week 4 — Oracle quality and solver representations

- ImpossibleBench
- Defusing Logic Bombs with LLM-Generated Ghost Code

**Tension:** tests can reward an incorrect implementation; model-generated
solver aids can be useful without being trusted if witnesses are rechecked on
the original program.

## Week 5 — Dataflow analysis and implementation conformance

- IRIS
- RFCAudit

**Tension:** IRIS grounds model-proposed security semantics in CodeQL
reachability, whereas RFCAudit retrieves clause-level evidence but leaves more
of the final conformance judgment to a model.

## Week 6 — Intended semantics and exact verification

- ARTEMIS
- LemmaNet

**Tension:** ARTEMIS asks a human to distinguish candidate formal meanings;
LemmaNet accepts model-proposed helper lemmas only after exact proof checking.
Compare the human and mechanical validation boundaries.

## Week 7 — Secure architecture and runtime enforcement

- ACE
- AgentSpec

**Tension:** ACE fixes trusted plan structure, statically checks information
flow, and isolates app execution; AgentSpec constrains observable action traces
through a stateful reference monitor. Audit the trusted computing base,
complete mediation, and policy completeness in both.

## Week 8 — Coordination correctness and evolving intent

- TraceFix
- Semantic Commit

**Tension:** a generated protocol can pass bounded model checking yet diverge at
runtime, while persistent intent can accumulate semantic conflicts that require
mixed-initiative review. Ask how checked models, evolving intent, authority, and
current world state should be bound to a concrete effect.

## Cross-course correctness trace

Reuse one scenario throughout: the agent interprets an underspecified goal,
observes `S0`, the world changes to `S1`, authority becomes stale, concurrent
actions race, one irreversible effect commits, a later action fails, the agent
retries, and a human approves a plausible but incomplete explanation. For every
paper, identify its explicit state or relation, independent checker, trusted
computing base, and the portion of this trace outside its guarantee.
