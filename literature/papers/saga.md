# SAGA: A Security Architecture for Governing AI Agentic Systems

## Decision

**Strong candidate.** Primary source: [NDSS 2026 proceedings](https://www.ndss-symposium.org/ndss-paper/saga-a-security-architecture-for-governing-ai-agentic-systems/).

## One-line idea

Use provider-mediated registration and cryptographic access-control tokens so a
user can govern which agents may discover, contact, and delegate to one another.

## Technical core

SAGA makes agent identity, lifecycle, policy, and inter-agent authorization a
protocol rather than prompt etiquette. ProVerif models token secrecy and
authentication. The provider registry can be replicated and sharded, while
agents enforce user-defined contact policies on messages.

## Evidence and limits

- Cryptographic and coordination overhead amortizes to tens of milliseconds per
  request and is small relative to LLM latency in the evaluated three tasks.
- The formal model establishes protocol properties under its assumptions; the
  implementation explores provider replication with crash-fault-tolerant RAFT.
- The provider is trusted, Byzantine tolerance is not implemented, and three
  productivity tasks do not establish policy usability at ecosystem scale.

## Course role

Cross-list in security and multi-agent systems. It fills the previously missing
authorization/delegation design point without replacing the stronger topology
and fault-propagation readings.
