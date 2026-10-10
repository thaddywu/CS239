# Atomix: Timely, Transactional Tool Use for Reliable Agentic Workflows

## Decision

**Strong preprint frontier; not eligible as a published primary.** Current
source is [arXiv 2602.14849](https://arxiv.org/abs/2602.14849).

## Mechanism

Atomix interposes adapters at the tool boundary and separates execution from
settlement. A transaction records read/effect scopes, seals its footprint, waits
for per-resource progress frontiers, revalidates reads, and settles effects by
class: bufferable calls are delayed, irreversible calls are gated, and already
externalized reversible calls are compensated on abort.

## Evidence

The approximately 2,000-line single-process prototype is tested on faulted
tau-bench, WebArena, OSWorld, multi-agent and speculation workloads, and
irreversible SMTP/webhook effects against nine mechanism-matched baselines.
The paper reports zero conflict-cycle witnesses under forced overlap and zero
classified-before-externalization leaks in 500 invalid-send trials, while
preserving all 500 valid sends.

## Limits

Safety depends on complete adapter mediation, correct scopes/effect classes and
frontier advancement. Distributed crash-safe exactly-once, semantic validation,
and atomic release across multiple heterogeneous irreversible endpoints are out
of scope; the latter is impossible without tool-side commit support. Several
baselines are reimplementations in a common harness rather than full ports.

## Course role

This is the exact modern counterpart to the old Sagas/Beldi instructor context:
it explains why restoring agent memory does not undo an email, booking, or REST
mutation, and supplies explicit settlement semantics for faults, speculation,
and concurrent agents. Recheck publication status before syllabus freeze.
