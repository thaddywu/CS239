# GPTScan: Detecting Logic Vulnerabilities by Combining GPT with Program Analysis

## Decision

**Strong candidate, usually a companion rather than the sole reading.** Primary source: [ICSE 2024 program](https://conf.researchr.org/details/icse-2024/icse-2024-research-track/114/GPTScan-Detecting-Logic-Vulnerabilities-in-Smart-Contracts-by-Combining-GPT-with-Pro).

## Problem and mechanism

Smart-contract logic vulnerabilities depend on business scenarios and properties that are difficult to encode as generic syntactic rules. GPTScan uses a model for scenario and property matching and to locate key variables/statements. Program analysis then validates whether the required data and control relationships actually hold.

The responsibility split is deliberate: probabilistic components narrow the search using semantic descriptions; deterministic analysis rejects candidates whose program relations do not support the claimed vulnerability.

## Evidence and limits

- The paper reports over 90% precision at the token-contract decision, over 70% recall, and coverage of 57% of evaluated projects.
- Programmatic confirmation removes roughly two thirds of the false positives from the model-only stage and contributes to finding nine previously unknown vulnerabilities.
- The vulnerability templates, Solidity semantics, and benchmark construction make transfer to general languages uncertain.
- Static confirmation improves precision but is not a proof of exploitability; model-created candidates determine what is never analyzed.

## Course role

Pair with IRIS to compare two placements of semantics: IRIS mines taint specifications then performs whole-program flow analysis; GPTScan matches natural-language scenarios/properties then checks focused relations. IRIS is the stronger single primary reading.
