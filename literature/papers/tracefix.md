# TraceFix: Repairing Agent Coordination Protocols with TLA+ Counterexamples

## Decision

**Selected for v7 under correctness and runtime assurance; peer reviewed at ACM
CAIS 2026.** It is not used as the second multi-agent architecture paper. Its
course value is generated coordination protocols, interleaving failures,
counterexample repair, and the model-to-runtime conformance gap.

## Mechanism

TraceFix makes an LLM-generated multi-agent coordination protocol an explicit
artifact. It synthesizes a topology IR, fills per-agent PlusCal processes,
model-checks the translated TLA+ with TLC, and feeds counterexample traces back
to a repair agent. The verified topology configures prompts and a runtime
monitor over channels, labels, locks, and counters.

## Evidence

- 48 tasks across 16 coordination families; 30 pass TLC initially and all pass
  after at most four repair iterations.
- The 3,456-run runtime study compares topology monitoring, prompt-only,
  mediator enforcement, and shared chat across model tiers and fault levels.
- Under a fixed monitored runtime, verification reduces deadlock/livelock from
  31.1% to 14.1%; topology-monitored execution reaches 89.4% mean checkpoint
  completion and 81.5% full completion.

## Limits

The model check is bounded and covers coordination safety, not domain-semantic
correctness, starvation, or guaranteed termination. More importantly, the
runtime monitor enforces topology membership rather than the verified PlusCal
state machine; prompt-carried step order explains residual deadlocks. The task
suite is synthetic and protocol-centric.

## Course role

This explains what is new about agent correctness: agents synthesize and then
deviate from a coordination protocol whose rare interleavings create races and
deadlocks. It complements Information Propagation's causal topology analysis
rather than duplicating it.
