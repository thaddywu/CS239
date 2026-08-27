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

[ACE](../literature/papers/ace.md) splits planning into a trusted abstract plan
and app-specific concrete plan, statically checks information flow, and enforces
data/capability barriers during execution. It is a distinct plan-integrity design,
not merely a second prompt-injection classifier.

### Runtime policy enforcement

[AgentSpec](../literature/papers/agentspec.md) defines triggers, predicates, and
enforcement decisions in a policy DSL and intercepts actions outside the model.
RefineAct translates intent into Prolog goals and checks planned action
pre/postconditions; it is accepted for ASE 2026 and remains a watch candidate.

### Authorization and inter-agent governance

[SAGA](../literature/papers/saga.md) uses provider-mediated registration and
cryptographic access-control tokens to enforce user policy on inter-agent
communication. ProVerif establishes protocol properties under a trusted-provider
model; semantic misuse inside an authorized exchange remains out of scope.

### Foundational vocabulary

Saltzer and Schroeder supply least privilege, fail-safe defaults, complete
mediation, separation of privilege, and least common mechanism. These principles
explain *why* an instruction-only defense cannot be a reference monitor.

## Reading decisions

**Strong:** AgentDojo, CaMeL, AgentSpec, ACE, SAGA.

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

## Due diligence audit — 2026-08-27

### Previously believed

AgentDojo, CaMeL, and AgentSpec already supported a full week spanning dynamic
evaluation, information/control-flow separation, capabilities, and event-policy
monitoring; delegation and revocation were the clearest gaps.

### New papers checked

- Fully inspected ACE and SAGA (NDSS 2026).
- Checked IsolateGPT as ACE's direct predecessor/attack target and Rennervate as
  a model/attention-level defense; neither displaced the system-architecture
  readings.
- Searched 2022–2026 S&P, USENIX Security, CCS, NDSS, SaTML, and SE venues for
  sandboxing, taint, capabilities, authorization, provenance, and policy—not
  only papers labeled prompt injection.

### Important additions

- [ACE](../literature/papers/ace.md): trusted abstract planning, static secure
  information flow, and execution barriers; **very high technical depth**.
- [SAGA](../literature/papers/saga.md): cryptographic inter-agent authorization
  and lifecycle governance; **very high technical depth**.

Together they fill plan integrity and delegation/authorization design points and
support a class comparing distinct trusted computing bases.

### Stronger replacements

ACE is a strong alternate to CaMeL, not a wholesale replacement: CaMeL isolates
trusted control from untrusted data, while ACE protects a two-level plan and app
execution. SAGA fills a missing role. No stronger peer-reviewed alternative
found in this audit for AgentSpec's general policy-DSL/runtime-monitor role.

### Judgment

**UPHELD.**

### Why

The strongest old candidates survive, and the additions make the week less
monocultural: benchmark, model-level defense, runtime monitor, dataflow/
capability architecture, trusted-plan architecture, and cryptographic
authorization are separable philosophies. Sandboxing/OS confinement and common
cross-paper evaluation remain underdeveloped.
