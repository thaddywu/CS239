# SAGA: A Security Architecture for Governing AI Agentic Systems

## Decision

**Strong background, not a final v5 primary.** Primary source:
[NDSS 2026 proceedings](https://www.ndss-symposium.org/ndss-paper/saga-a-security-architecture-for-governing-ai-agentic-systems/).

## One-line idea

Use provider-mediated registration and cryptographic access-control tokens so a
user can govern which agents may discover, contact, and delegate to one another.

## Technical core

SAGA makes agent identity, lifecycle, policy, and inter-agent contact
authorization a protocol rather than prompt etiquette. A provider checks the
recipient's contact policy and issues a one-time key; the agents establish a
shared key, then use an encrypted access token containing an expiry, quota, and
access policy. ProVerif checks token secrecy and authentication. The provider
registry can be replicated and sharded with RAFT.

## Evidence and limits

- Cryptographic and coordination overhead amortizes to tens of milliseconds per
  request and is small relative to LLM latency in the evaluated three tasks.
- The formal model establishes secrecy and authentication under its assumptions;
  it does not establish semantic delegation, policy correctness, or immediate
  revocation of already issued tokens.
- The provider is trusted, Byzantine tolerance is not implemented, and three
  productivity tasks do not establish policy usability at ecosystem scale.

## Course role

Cross-list as security and multi-agent background. The final review found a
conventional authenticated-contact protocol rather than general attenuated task
delegation, so it no longer merits a third full security assignment beside
CaMeL and AgentSpec. Reconsider if a successor adds delegation chains,
attenuation, revocation freshness, or application-level authority semantics.
