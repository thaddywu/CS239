# SelfPiCo: Self-Guided Partial Code Execution with LLMs

## Metadata

ISSTA 2024. [DOI](https://doi.org/10.1145/3650212.3680368).

## One-line idea

When partial Python code encounters an undefined value or dependency, query a
model for a typed stand-in, execute again, and use runtime feedback to revise it.

## Technical core

The loop intercepts missing runtime objects, constructs contextual prompts,
generates values or dummy implementations, and validates them through continued
execution. It makes partial execution possible where conventional stubbing fails.

## Evaluation and limits

The paper reports executing roughly 72.7–83.3% of target lines under different
settings and demonstrates runtime type-error detection. Predicted values can
diverge from real environments and observations are not sound program semantics.
The contribution is closer to dynamic analysis than autonomous agency.

## Course placement and decision

**Candidate / program-analysis optional.** Retained for technical novelty, but
IRIS/GPTScan better fit the course's agent–analysis responsibility question.
