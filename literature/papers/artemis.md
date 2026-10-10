# Automating Requirements Formalization: Using LLMs and Low-Complexity Distinguishing Traces for Semantic Validation

## Decision

**Selected for reading-list v5.** Primary source: [ICSE 2026 Research Track record](https://conf.researchr.org/details/icse-2026/icse-2026-research-track/287/Automating-Requirements-Formalization-Using-LLMs-and-Low-Complexity-Distinguishing-T).
The assigned DOI had not yet resolved to a populated ACM page when rechecked on
2026-08-31, so the course links use the official program page with the abstract.

## Mechanism and evidence

ARTEMIS translates unstructured requirements through FRETish/property-pattern
structure into LTL, then decomposes competing formalizations and asks a user to
classify short distinguishing traces. A balanced trace-selection strategy
eliminates roughly half of the remaining candidates per answer, giving a
logarithmic rather than linear interaction pattern.

Across five safety-critical datasets it reports 1.57x the accuracy of the
strongest baseline. The largest case needs 11 user traces rather than 93, and
cases with more than ten candidates use 2.52x fewer traces on average. However,
14.22% of requirements still yield no plausible candidate within 1,000 tries;
the expert is simulated, traces are bounded to length 20, and the true property
must fit the supported structured language.

## Course role

ARTEMIS replaces domain-specific contract generation with a broader and more
explicit model of semantic validation: human effort is spent distinguishing
formal meanings, not editing model prose.
