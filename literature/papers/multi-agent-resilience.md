# On the Resilience of LLM-Based Multi-Agent Collaboration with Faulty Agents

## Decision

**Selected for the final 20-paper-day list.** Primary source: [ICML 2025 / PMLR](https://proceedings.mlr.press/v267/huang25ay.html).

## Problem and mechanism

The work asks how collaboration structures behave when one component is incompetent or malicious. AutoTransform and AutoInject create controlled faulty responses. Six systems and three structural families are evaluated on four downstream tasks.

The mitigation mechanisms are explicit: a Challenger allows agents to contest other outputs; an Inspector adds a reviewing component that can identify and correct messages. These are architectural fault-containment choices rather than persona descriptions.

## Evidence and limits

- The hierarchical structure `A -> (B <-> C)` has a 5.5% performance drop under faults, compared with 10.5% and 23.7% for two alternatives.
- Challenger and Inspector recover up to 96.4% of injected errors in the reported configurations.
- Synthetic transformations cannot cover correlated model errors, strategic collusion, poisoned shared memory, or tool-level side effects.
- Adding an Inspector introduces its own common-mode failure and cost; there is no independent trusted oracle.

## Course role and comparisons

Pair with information-propagation topology: one explains diffusion, the other tests containment and recovery. Compare the Inspector to an external verifier in CRITIC or AgentSpec; a model reviewer is not equivalent to a reference monitor.

## Reading-list v5 decision

**Strong candidate, no longer primary.** The fault-injection methodology remains
excellent, but the Inspector and Challenger are not independent recovery or
consistency mechanisms. LAS fills the more underexplored orchestration slot.
