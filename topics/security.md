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

**Strong primaries:** AgentDojo, CaMeL, AgentSpec, ACE.

**Strong background:** SAGA for authenticated inter-agent contact and provider
lifecycle assumptions, not general task delegation.

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

## Final-selection v3 update — 2026-08-27

The final set uses CaMeL, SAGA, and AgentSpec because their trusted computing
bases are genuinely different: provenance/capability-separated control,
cryptographic identity and inter-agent authorization, and application-specific
runtime policy enforcement. ACE remains a very strong alternate to CaMeL but
would duplicate the plan/dataflow enforcement philosophy more than SAGA's
delegation mechanism. Security is embedded in a broader correctness block with
Sagas, Beldi, and adjustable autonomy so prompt injection is not treated as the
whole correctness problem.

## Reading-list v4 update — 2026-08-27

CaMeL, AgentSpec, and SAGA remain primary because they enforce different
relations: provenance/capability flow, application action policies, and
inter-agent identity/delegation. SAGA re-earns its slot despite its trusted
provider and limited task evaluation because the other two do not cover
inter-agent authority. [Temporary Authority, Permanent Effects](../literature/papers/temporary-authority-permanent-effects.md)
is the most direct new freshness/TOCTOU candidate but remains a preprint.
*Governance by Construction* is rejected as a short demo that overlaps
AgentSpec's stronger reference-monitor lesson.

## Reading-list v5 update — 2026-08-27

CaMeL, AgentSpec, and SAGA remain the authority/enforcement core. The expanded
Agentic SE search adds [RFCAudit](../literature/papers/rfcaudit.md) as a selected
protocol-conformance auditor and records [ACTaint](../literature/papers/actaint.md),
[ProbGuard](../literature/papers/probguard.md), and [Semia](../literature/papers/semia.md)
as serious challengers. ProbGuard's predicate/DTMC/CTL design is technically
deep, but its small empirical sample does not meet the practical PAC conditions;
Semia's Datalog skill audit remains preprint-only. These do not alter the three
distinct trusted computing bases in the primary security block.

## Final adversarial review — 2026-08-28

The primary security pair is now CaMeL and AgentSpec: provenance/capability-aware
information flow versus a stateful external reference monitor. SAGA moves to
background after protocol-level inspection. It establishes token secrecy and
authentication for provider-mediated contact, but not policy correctness,
delegation-chain semantics, attenuation, or immediate revocation of outstanding
tokens. This sharper classification reopens delegated authority as a genuine
coverage gap rather than claiming it is solved.

ProbGuard remains a strong candidate but does not replace the pair: its
predicate/DTMC/CTL boundary is interesting, while the practical evaluation uses
far fewer traces than its useful PAC bounds and its safest intervention sharply
reduces completion.

## Supplied-list enforcement audit — 2026-08-28

The supplied list exposes a fast-moving preprint frontier around the selected
CaMeL/AgentSpec pair:

- [Agent-C](../literature/papers/agent-c.md) adds formally defined temporal
  constraints, incremental SMT checks, and compliant constrained generation.
- [Language-Based Agent Control](../literature/papers/lbac.md) types the entire
  application and recursive subagents, supporting provenance, attenuated
  capabilities, and information flow in one host language.
- [VIGIL](../literature/papers/vigil.md) lifts skill prose and traces into
  finite-trace SMT policies, but still trusts trace visibility and LLM policy
  compilation.
- [ToolGuard](../literature/papers/toolguard.md) is peer reviewed and compiles
  company policy prose to pre-tool guard code, but its one-domain preliminary
  evidence and inability to catch omitted required actions make it background.

No current primary is displaced solely by a preprint. Agent-C and LBAC require
publication rechecks because they are genuine mechanism challengers rather than
minor variants.

## Reading-list v7 placement — 2026-08-29

[ACE](../literature/papers/ace.md) becomes the scheduled secure-architecture
primary after full-paper review. Its trusted abstract plan, app-specific
concrete plan, static lattice information-flow check, and isolated
capability-mediated execution form one end-to-end architecture. The important
limits are equally explicit: ahead-of-time restricted plans constrain dynamic
replanning and mutable behavior, while schemas, plan matching, isolation, and
the enforcement runtime join the trusted base.

[AgentSpec](../literature/papers/agentspec.md) remains selected for a different
abstraction: stateful policies over observable action traces. [TraceFix](../literature/papers/tracefix.md)
joins the broader correctness block because it checks and repairs coordination
protocols, then reveals a gap between the verified state machine and runtime
topology enforcement.

[CaMeL](../literature/papers/camel.md) moves to strongest alternate, not because
it lacks depth. Its privileged/quarantined-model split and provenance-aware
capabilities remain an excellent alternative; v7 prefers ACE's complete
plan-to-check-to-execution path and stronger systems-security venue. Agent-C,
LBAC, and Atomix remain technically important preprints rather than primaries.
