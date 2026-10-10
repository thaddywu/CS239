# Defeating Prompt Injections by Design (CaMeL)

## Decision

**Strong alternate after the v7 audit.** Primary source: [IEEE SaTML 2026 author record](https://www.floriantramer.com/publications/camel25/).

## Problem and mechanism

An ordinary agent places trusted user instructions and untrusted tool data in one model context, then lets that model control privileged calls. CaMeL separates these responsibilities. A privileged model derives a program/control flow from trusted input; a quarantined model can parse untrusted data but cannot modify that control flow. Values carry fine-grained capability/provenance tags. Deterministic policies inspect tool, arguments, flows, and capabilities before execution.

This is an information-flow and confused-deputy design, not another prompt asking the model to ignore malicious text.

## Evidence

- On the current AgentDojo evaluation, CaMeL reports zero successful benchmark attacks in the main table while retaining substantial task utility; the aggregate under-attack utility is 66.7% in the reported configuration.
- Normal/strict modes expose the security–utility tradeoff, and the paper details unsupported dynamic cases rather than claiming universal coverage.
- Policies can express who may use a value and where it may flow, providing a concrete link to capability systems.

## Limits

The planner can mistranslate ambiguous user intent, supported programs/tools require annotations, and complex dynamic control can force confirmation or refusal. Guarantees are relative to the policy, capability propagation, and trusted computing base. Availability and semantic misuse within an allowed flow remain concerns.

## Course role

CaMeL remains technically excellent; it was not removed for lack of depth.
V7 chooses ACE because ACE exposes the trusted-plan-to-static-check-to-isolated-
execution path as one end-to-end security architecture and has a stronger
systems-security publication record. CaMeL is the first replacement if the
instructor prefers its privileged/quarantined-model split and provenance-aware
capabilities. Compare AgentSpec: CaMeL constrains information/control flow by
construction; AgentSpec monitors domain rules over action traces.
