# The Protection of Information in Computer Systems

## Metadata

Proceedings of the IEEE, 1975. [Author-hosted publication](https://web.mit.edu/Saltzer/www/publications/protection/).

## One-line idea

Security depends on system-wide design principles—least privilege, fail-safe
defaults, complete mediation, separation of privilege—not secrecy of mechanism.

## Technical core

The paper organizes protection goals, access control, authentication, and
capability-like authority, then derives design principles for small, auditable
enforcement mechanisms. These principles define what a reference monitor must do
outside an untrusted decision maker.

## Evaluation and limits

This is a conceptual systems paper, not a modern empirical benchmark. Examples
and hardware assumptions are dated, but the principles precisely diagnose agent
failures: ambient credentials violate least privilege; prompt-only checks violate
complete mediation; permissive fallback violates fail-safe defaults.

## Course placement and decision

**Candidate / short Week 9 background.** Use excerpts to analyze CaMeL and
AgentSpec, not to turn the seminar into a general security-history course.
