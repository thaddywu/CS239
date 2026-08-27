# Agent Failure Recovery and Reliability

## Failure model

Recovery requires at least: a detector, new evidence or diagnosis, a preserved
good state, a bounded corrective action, and a criterion for resuming. Current
LM-agent literature is much stronger on rewriting an answer than on recovering
from partially executed external effects.

## Mechanism map

### Intrinsic reflection

Reflexion stores verbal lessons derived from task feedback and conditions later
attempts on them. It is influential and often effective, but the memory is
unverified and “verbal reinforcement learning” does not update model parameters.

[Large Language Models Cannot Self-Correct Reasoning Yet](../literature/papers/self-correction-limitations.md)
shows that asking for a recheck without new information often harms accuracy;
some debate gains reduce to extra sampling. This is the required control result.

### Evidence-grounded correction

[CRITIC](../literature/papers/critic.md) adds search, execution, or another tool
whose observation can falsify a claim. The key variable is not the number of
reflection turns but the independence and relevance of the evidence.

Theorem provers, tests, static analyzers, and runtime policies are stronger
instances of the same pattern, with different oracle quality.

### Structural recovery

Microreboot restarts fine-grained components while preserving durable state and
shows much lower recovery cost than full process restart. Crash-Only Software is
retained as its earlier design thesis but superseded as the main evaluated
reading.

Multi-Agent Resilience adds textual fault injection, challenge, and inspection,
but does not address durable side effects.

## Reading decisions

**Strong:** CRITIC; self-correction limitations.

**Other candidates:** Reflexion; Microreboot; Multi-Agent Resilience cross-listed.
Crash-Only is superseded by Microreboot for a primary systems excerpt.

## Current assessment

- Literature maturity: **medium for detection/retry; low for stateful recovery,
  rollback, and exactly-once effects**.
- Technical depth: high in the negative study and classic recovery systems;
  medium in verbal reflection loops.
- Course suitability: high as a cross-cutting reliability week, especially when
  paired with runtime enforcement.

## Gaps and next searches

- Checkpoints that include tool state, credentials, memory, and repository
  versions, with explicit invalidation rules.
- Idempotency keys, sagas/compensating actions, transactions, and replay for
  agent tool protocols.
- Failure taxonomies based on traces and external effects, not answer errors.
- Recovery under a faulty verifier or corrupted memory.
- Transfer from recovery-oriented computing, workflow engines, and distributed
  systems into contemporary agent runtimes.

## Due diligence audit — 2026-08-27

### Previously believed

Agent reliability papers mainly revise text or retry calls; mature work on
rollback, checkpoint/restart, idempotency, compensation, and exactly-once
external effects had not transferred into LLM-agent runtimes.

### New papers checked

- Targeted 2022–2026 OSDI, SOSP, NSDI, EuroSys, ASPLOS, ATC, ICSE, FSE, ASE,
  and workflow/recovery terminology rather than general “self-correction.”
- Checked Murakkab and recent long-running agent-runtime work for checkpoints,
  replay, or compensating actions; Murakkab optimizes execution but does not
  recover external side effects.
- Checked recent transaction/undo/replay systems such as intermittent-computing
  work as possible predecessors; no direct LLM-agent adaptation survived the
  relevance threshold.

### Important additions

None. The ACL memory-management study is relevant to corrupted persistent state,
but it studies record addition/deletion rather than transactional tool recovery.

### Stronger replacements

No stronger peer-reviewed alternative found in this audit. Microreboot remains
the most useful systems bridge, not evidence that agent recovery is solved.

### Judgment

**UPHELD.**

### Why

The targeted systems/workflow search did not uncover a peer-reviewed LLM-agent
runtime with explicit checkpoint boundaries, durable logs, idempotency keys,
compensating actions, or exactly-once side-effect semantics. This absence is an
important negative result and should remain a central Week 8 design exercise.
