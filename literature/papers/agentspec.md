# AgentSpec: Customizable Runtime Enforcement for Safe and Reliable LLM Agents

## Decision

**Selected for the final 20-paper-day list.** Primary source: [ICSE 2026 program](https://conf.researchr.org/details/icse-2026/icse-2026-research-track/29/AgentSpec-Customizable-Runtime-Enforcement-for-Safe-and-Reliable-LLM-Agents).

## Problem and mechanism

Safety instructions inside a prompt are not enforcement. AgentSpec supplies a compact policy language whose rules define triggers, predicates over state/history/action arguments, and enforcement decisions. A runtime monitor intercepts actions and applies rules outside the model. Policies are customizable across coding, embodied, and autonomous-driving settings; the work also studies LLM-generated rules.

## Evidence

- The evaluation reports prevention of over 90% of unsafe code-agent actions, all tested embodied hazards, and legal compliance for autonomous-vehicle scenarios, with millisecond-scale rule overhead.
- Automatically generated embodied-agent rules reach 95.56% precision but only 70.96% recall; other domains also expose missed risky actions.
- The gap between hand-authored and generated policy quality is an important result: generating a rule is not the same as enforcing a correct rule.

## Limits

Rules cover anticipated properties and visible events. Semantic state hidden from the monitor, unsafe but individually legal action sequences, and underspecified policies remain open. Cross-domain percentages are not directly comparable, and broad guarantees require a clearly stated threat/system model.

## Course role

Use as the direct “software engineering for agents” reading: specification language, monitor, adaptation, and evaluation. Pair with CaMeL or RefineAct, and with ImpossibleBench to discuss conflicts among natural-language requirements, tests, and runtime policies.
