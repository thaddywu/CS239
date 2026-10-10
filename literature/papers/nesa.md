# NESA: Relational Neuro-Symbolic Static Program Analysis

## Decision

**Selected for reading-list v5.** Primary source: [FSE 2026 publisher record](https://doi.org/10.1145/3808161).

## Mechanism and evidence

NESA expresses an analysis as a small restricted-Datalog policy. A parser
materializes syntactic relations, an LLM supplies explicitly declared semantic
relations, and a fixed-point evaluator joins both kinds of facts. Lazy,
incremental prompts request only neural relations needed by the current rule
frontier. Policies of 5--13 rules cover slicing and six bug classes; reported
results include 91.5% precision and 84.6% recall for slicing, strong synthetic
bug results, and 13 real memory-leak bugs that were found and fixed.

The important ablation is structural: unconstrained neural constructors sharply
degrade results, while incremental evaluation skips 30--83% of prompting rounds.
The symbolic engine disciplines inference but does not make LLM-produced alias
or semantic facts sound; context sensitivity and many-source/sink scaling remain
limitations.

## Course role

NESA is the clearest answer to the requested Datalog family. Compare its
LLM-populated relational facts with IRIS's model-generated CodeQL specifications
and Gordian's solver-aiding but execution-rechecked ghost code.
