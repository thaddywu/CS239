# Agentix: An Efficient Serving Engine for LLM Agents as General Programs

## Decision

**Strong alternate after the v7 audit.** Primary source: [USENIX NSDI 2026](https://www.usenix.org/conference/nsdi26/presentation/luo).

## Mechanism and evidence

Agentix treats an agent as a program with identifiable calls, dependencies, and
cumulative service rather than as independent chat requests. PLAS schedules
single-engine programs using attained service; ATLAS estimates distributed
critical paths and combines preemption with load balancing. Across the reported
agent workloads it provides 4--15x program throughput at comparable latency
relative to vLLM, including up to 8x on one engine and 1.5x over MLFQ.

Its boundary is equally useful: the runtime optimizes observable, instrumented
LLM-call graphs and does not reason about semantic correctness, external-effect
transactions, or tool-state consistency.

## Course role

This is the strongest systems-runtime alternate and separates program-level
scheduling from model-request batching. It leaves the scheduled list only
because agent plus multi-agent architecture is capped at two weeks and v7
prioritizes ingredients, interfaces, orchestration, and communication over
serving performance.
