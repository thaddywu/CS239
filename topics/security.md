# Agent Security, Authorization, and Information Flow

## Threat model

An agent becomes a confused deputy when untrusted content can steer a model that
holds the user's tools, secrets, and authority. Prompt injection is therefore
not primarily a bad-string classification problem. It is a control/data-flow,
authorization, provenance, and complete-mediation problem.

## Mechanism map

### Dynamic security evaluation

[AgentDojo](../literature/papers/agentdojo.md) executes legitimate tasks and
injection goals in stateful tool environments, reporting both utility and attack
success. InjecAgent gives broad static coverage of indirect injections. ToolEmu
uses a model-emulated sandbox to cheaply generate risky states and evaluate
behavior, trading scale for simulator/evaluator trust.

### Information-flow separation and capabilities

[CaMeL](../literature/papers/camel.md) derives control flow from trusted input,
quarantines interpretation of untrusted data, tags values with capabilities and
provenance, and checks policies before calls. Its guarantee is architectural and
relative to a trusted computing base—not a claim that the model learned to
ignore attacks.

### Runtime policy enforcement

[AgentSpec](../literature/papers/agentspec.md) defines triggers, predicates, and
enforcement decisions in a policy DSL and intercepts actions outside the model.
RefineAct translates intent into Prolog goals and checks planned action
pre/postconditions; it is accepted for ASE 2026 and remains a watch candidate.

### Foundational vocabulary

Saltzer and Schroeder supply least privilege, fail-safe defaults, complete
mediation, separation of privilege, and least common mechanism. These principles
explain *why* an instruction-only defense cannot be a reference monitor.

## Reading decisions

**Strong:** AgentDojo, CaMeL, AgentSpec.

**Other candidates:** ToolEmu, InjecAgent, RefineAct, Saltzer–Schroeder excerpt.

**Rejected as primary:** *Towards Verifiably Safe Tool Use* is a promising ICSE
NIER agenda without a full implementation/evaluation. Prompt-hardening papers
with no authority boundary are weaker alternatives, not equivalent defenses.

## Current assessment

- Literature maturity: **high for prompt-injection evaluation; medium/high for
  architectural enforcement; low for delegation and revocation**.
- Technical depth: very high in CaMeL and AgentSpec.
- Course suitability: very high and now strong enough for its own week.

## Gaps and next searches

- Delegated, attenuated, revocable capabilities across sub-agents and services.
- Persistent-memory confidentiality/integrity and cross-session contamination.
- Compositional policies when tool results become inputs to other tools.
- Availability, denial-of-wallet, and semantic misuse inside allowed flows.
- Formal statements of trusted computing base and policy completeness.
- Follow-up comparisons among CaMeL, AgentSpec, and RefineAct on a common task
  and threat model.
