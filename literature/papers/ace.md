# ACE: A Security Architecture for LLM-Integrated App Systems

## Decision

**Selected for v7.** Primary source: [NDSS 2026 proceedings](https://www.ndss-symposium.org/ndss-paper/ace-a-security-architecture-for-llm-integrated-app-systems/).

## One-line idea

Build an abstract plan only from trusted information, map it to installed apps,
statically check secure information flow, and enforce capability/data barriers
while executing the trusted structure.

## Technical core

Abstract–Concrete–Execute prevents malicious app content from rewriting the
control plan. Structured plans compile to a representation checked against
information-flow constraints, while runtime isolation mediates data and
capabilities between apps. This combines plan integrity and complete mediation.

## Evidence and limits

- The evaluation spans InjecAgent, Agent Security Bench, and tool-use utility;
  it measures both injection containment and the cost of plan restrictions.
- Abstract plans are made ahead of time. This constrains dynamic replanning,
  mutable state, dynamic code, and other behaviors outside ACE's restricted
  execution language.
- The guarantee trusts user intent, planner boundaries, app schemas, abstract
  to concrete plan matching, isolation, and the enforcement runtime.
  Allowed-but-harmful actions and planning failures remain possible.

## Course role

Primary secure-architecture reading in v7. ACE makes the whole enforcement path
auditable: trusted abstract plan, app binding, static information-flow check,
then isolated capability-mediated execution. Compare it with AgentSpec's
general event-policy monitor and keep CaMeL as the closest alternate.
