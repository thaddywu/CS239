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
