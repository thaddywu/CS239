# HoarePrompt: Structural Reasoning About Program Correctness in Natural Language

## Decision

**Rejected as a primary reading after the final v5 adversarial review.** Primary
source: [ICSE 2026 research program](https://conf.researchr.org/details/icse-2026/icse-2026-research-track/164/HoarePrompt-Structural-Reasoning-About-Program-Correctness-in-Natural-Language).

## Mechanism and evidence

HoarePrompt propagates prompted natural-language state descriptions through a
CFG. Loops are unrolled three times before another prompt generalizes their
effect; this is called k-induction but does not construct or check an inductive
invariant. A final model call classifies whether the resulting description
satisfies the requirement. On CoCoClaNeL the reported relative MCC gains are
large, but absolute MCC is only 0.159--0.259 and the full method consumes
roughly 39--64 times the baseline tokens.

The calculus gives the model a program-logic-shaped scaffold, not a proof:
state descriptions and the final entailment classifier remain fuzzy, absolute
classification performance is modest, and the benchmark consists mainly of
contest programs.

## Course role

The paper remains useful background for distinguishing program-logic-shaped
prompting from verification, but the structure is not enough for a scarce full
assignment. LemmaNet replaces it with source-aware intermediate artifacts that
are independently proved and applied to a real Frama-C/Rocq verification
condition. Reconsider only if a future version gives executable semantics or a
soundness boundary to the propagated states.
