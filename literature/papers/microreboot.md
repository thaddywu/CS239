# Microreboot — A Technique for Cheap Recovery

## Metadata

OSDI 2004. [Primary record](https://www.usenix.org/conference/osdi-04/microreboot%E2%80%94-technique-cheap-recovery).

## One-line idea

Recover an application by restarting the smallest replaceable component while
keeping user/session data outside that component.

## Technical core

The design separates process-like component state from durable data, gives
components restartable lifecycles, and contains dependencies so recovery can be
localized. Requests encountering a restarting component retry or fail quickly.

## Evaluation and limits

J2EE application experiments show order-of-magnitude faster recovery and much
less lost work than full process restart. The approach assumes components can be
made crash-only and state can be externalized; corrupted durable data and
non-idempotent external actions remain hard.

## Course placement and decision

**Selected for Paper Day 17 as the recovery-systems bridge.** It supplies concrete state/restart
abstractions almost entirely missing from verbal agent-recovery papers.
