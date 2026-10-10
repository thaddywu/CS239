# ACRFence: Preventing Semantic Rollback Attacks in Agent Checkpoint-Restore

## Decision

**Rejected as a primary reading pending peer review and stronger evaluation.**
Primary record: [arXiv 2603.20625](https://arxiv.org/abs/2603.20625).

ACRFence identifies a specifically agentic retry hazard: after checkpoint
restore, a probabilistic agent may synthesize a semantically new request, so an
ordinary idempotency key does not prevent duplicate payment or reuse of expired
authority. It records irreversible effects and enforces replay-or-fork
semantics. The Action Replay and Authority Resurrection threat model is highly
relevant, but current evidence is a proof of concept rather than a mature
peer-reviewed runtime evaluation.

