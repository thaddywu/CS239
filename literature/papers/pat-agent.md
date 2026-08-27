# PAT-Agent: Autoformalization for Model Checking

## Decision

**Strong candidate.** Primary source: [ASE 2025 proceedings DOI](https://doi.org/10.1109/ASE63991.2025.00176).

## One-line idea

A planning model structures a natural-language system description, a generator
emits CSP#, and PAT counterexamples drive iterative model repair.

## Technical core

The plan extracts processes, state, synchronization, and properties before code
generation. PAT then distinguishes compilation from satisfaction of assertions;
counterexample traces return machine-checkable evidence to a bounded repair
loop. The formal model remains an inferred hypothesis, not a proof that the
natural-language intent was translated faithfully.

## Evidence and limits

- On 40 systems, the full pipeline reaches 100% compilation and full-pass after
  up to five repair rounds, while direct baselines have 37.5–52.5% full-pass.
- Removing repair or planning materially lowers the full-pass rate, supporting
  both mechanisms rather than mere extra sampling.
- The corpus and repair rules are PAT/CSP#-specific; a passing model can still
  omit behavior present in the intended system.

## Course role

Use as the autoformalization/model-checking primary beside LeanDojo. It broadens
the formal week beyond theorem search and creates a sharp debate about model
fidelity versus checker-certified internal consistency.
