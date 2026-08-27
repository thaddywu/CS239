# AutoCodeRover: Autonomous Program Improvement

## Decision

**Selected for the final 20-paper-day list.** Primary source: [ISSTA 2024 DOI record](https://doi.org/10.1145/3650212.3680384); [author PDF](https://haifengruan.com/assets/pdf/autocoderover_issta24.pdf).

## Problem and mechanism

Generic shell exploration wastes context and ignores software structure. AutoCodeRover gives an LLM repository-aware search APIs over classes and methods, iteratively expands context, and hands the collected locations to a patch generator. When tests exist, spectrum-based fault localization (SBFL) ranks suspicious methods and guides retrieval. Generated patches are run against tests and can be regenerated in a bounded loop.

## Evidence

- On 300 SWE-bench Lite issues, one run resolves 19% in about 195 seconds with roughly 37k tokens/$0.43 per instance in the paper's setting; three runs reach 26%.
- Adding SBFL moves the reported resolved count from 57 to 66 (19% to 22%).
- Manual assessment says roughly two thirds of test-passing patches are acceptable, directly exposing the inadequacy of benchmark tests as a complete oracle.

## Limits

The code-search controller and termination remain model decisions; analysis is used as a hint rather than a sound constraint. Results use an early SWE-bench era and closed models. SBFL depends on a reproducible failing test and can mislead when coverage is poor.

## Course role and comparisons

Use as the best bridge from classic debugging to agentic repair. Compare with SWE-agent's general interface, Agentless's deterministic hierarchy, RepairAgent's finite-state control, and IRIS's tighter neuro-symbolic division of labor.
