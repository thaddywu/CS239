# ACE: A Security Architecture for LLM-Integrated App Systems

## Decision

**Strong candidate.** Primary source: [NDSS 2026 proceedings](https://www.ndss-symposium.org/ndss-paper/ace-a-security-architecture-for-llm-integrated-app-systems/).

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

- ACE reports 100% security on all 1,054 InjecAgent cases and near-complete
  security on Agent Security Bench under its stated threat model.
- Utility remains at least 84% on InjecAgent with stronger planners, while model
  choice and planning failures create a real security/utility tradeoff.
- The guarantee trusts user intent, abstract-plan construction boundaries, app
  schemas, and the enforcement runtime; allowed-but-harmful actions remain.

## Course role

Primary alternate to CaMeL. ACE makes trusted plan structure explicit and is
well suited to compare dataflow/capability enforcement with AgentSpec's general
event-policy monitor.
