# Steering Tree-of-Thought Reasoning via Deductive Verification

## Decision

**Candidate, not selected; accepted in press at ISSTA 2026.** Primary source:
[ISSTA 2026 research program](https://conf.researchr.org/details/issta-2026/issta-2026-research-papers/109/Steering-Tree-of-Thought-Reasoning-via-Deductive-Verification).

## Mechanism and available evidence

Deductive Steering makes each proposed Tree-of-Thought step carry both natural
language and an SMT formula. A solver accepts the step only when its formula is
a logical consequence of accumulated constraints, checked through
unsatisfiability of `Phi and not phi`; counterexamples drive refinement and
failed verification triggers backtracking. The official abstract reports five
benchmarks spanning fault localization, program synthesis, and loop-invariant
generation, with 11.4--17.2 percentage-point accuracy gains and 27--45% fewer
tokens across multiple models.

The paper is an exact-fit constraint-guided challenger. It is not selected
because only the official abstract/program record was available in this audit:
benchmark construction, encoding failures, solver coverage, ablations, and
limitations could not be inspected at the strong-candidate standard. Recheck
the final paper before syllabus freeze; do not infer a sound end-to-end result
from verified steps when model-generated encodings may omit semantics.
