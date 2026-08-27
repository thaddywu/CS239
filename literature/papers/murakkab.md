# Murakkab: Resource-Efficient Agentic Workflow Orchestration in Cloud Platforms

## Decision

**Selected for the final 20-paper-day list.** Primary source: [OSDI 2026 proceedings](https://www.usenix.org/conference/osdi26/presentation/chaudhry).

## One-line idea

Expose an agentic workflow declaratively so an optimizer and adaptive runtime
can jointly choose models, hardware, and execution configuration under accuracy,
latency, energy, and cost SLOs.

## Technical core

Murakkab decouples control logic from model/hardware bindings, profiles component
alternatives, searches cross-layer configurations, multiplexes resources, and
reconfigures as load or SLOs change. This is a genuine systems-runtime mechanism,
not another prompting pattern.

## Evidence and limits

- Across evaluated workflows, it reports up to 2.8× lower GPU use, 3.7× lower
  energy, and 4.3× lower cost while retaining target SLOs.
- Static workflow evaluations and a dynamic LiveCodeBench case exercise both
  optimization and adaptive execution.
- Arrival traces approximate agent workloads using cloud chat/coding traffic;
  most workload quality is measured by benchmark accuracy rather than semantic
  safety or long-running side effects.

## Course role

Best systems paper for the runtime/harness topic. It adds a missing design point:
the agent graph is an optimizable program whose execution policy belongs outside
the model.
