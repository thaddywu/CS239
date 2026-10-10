# Defusing Logic Bombs in Symbolic Execution with LLM-Generated Ghost Code

## Decision

**Selected for reading-list v5; accepted in press at ISSTA 2026.** Primary
source: [ISSTA 2026 research program](https://conf.researchr.org/details/issta-2026/issta-2026-research-papers/35/Defusing-Logic-Bombs-in-Symbolic-Execution-with-LLM-Generated-Ghost-Code).

## Mechanism and evidence

Gordian asks the model to synthesize ghost code only around solver-hostile
fragments: bidirectional inverse relations, solver-friendly surrogate models,
and semantic heap partitions. KLEE and Z3 retain global path reasoning, and
candidate inputs or states are rechecked on the original program. The
transformation therefore preserves the soundness of reported witnesses, though
incomplete ghost code can still miss feasible paths.

On LogicBombs, coverage improves by up to 94.3% and 138.1% over the best KLEE
configuration; component ablations show all three ghost-code forms contribute.
On FDLibM it reaches roughly 92% average coverage and on structured programs
such as libexpat, jq, and bc it reports 79--109% improvements over KLEE, while
using 90--96% fewer tokens than LLM-heavy alternatives.

## Course role

Gordian is the cleanest symbolic-execution reading: the model changes the
representation presented to a solver but never becomes the final oracle.
