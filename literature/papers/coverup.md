# CoverUp: Effective High Coverage Test Generation for Python

## Metadata

FSE 2025. [Primary record](https://conf.researchr.org/details/fse-2025/fse-2025-research-papers/112/CoverUp-Effective-High-Coverage-Test-Generation-for-Python).

## One-line idea

Iteratively show a model concrete coverage gaps and execute revised tests until
coverage stops improving.

## Technical core

CoverUp couples LLM test generation to coverage measurement and targeted
feedback rather than one-shot prompts. Execution errors and uncovered regions
become context for the next generation round.

## Evaluation and limits

The paper reports median statement coverage around 80%, above CodaMOSA's 47% in
its comparison, and attributes nearly 40% of achieved coverage to iteration. The
comparison spans different system assumptions; coverage does not establish
assertion strength or fault detection, and Python dominates.

## Course placement and decision

**Candidate / Week 4 optional.** Useful newer feedback-loop result; CodaMOSA is
the more revealing hybrid-algorithm primary.
