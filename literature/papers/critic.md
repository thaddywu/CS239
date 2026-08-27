# CRITIC: Self-Correction with Tool-Interactive Critiquing

## Decision

**Strong candidate.** Primary source: [ICLR 2024 proceedings](https://proceedings.iclr.cc/paper_files/paper/2024/hash/fef126561bbf9d4467dbb8d27334b8fe-Abstract-Conference.html).

## Problem and mechanism

A model asked to critique itself has no new evidence. CRITIC instead lets it invoke external tools—such as search and a code interpreter—to test claims, observe results, formulate a critique, and revise the answer. Iteration is grounded in environment observations rather than the model's confidence alone.

## Evidence and limits

The paper evaluates question answering, mathematical/programming tasks, and toxicity-related settings, with tool-interactive revision generally improving initial answers and intrinsic critique baselines. The strongest evidence occurs where tools return objective signals.

Tool outputs are not automatically authoritative: search can retrieve poisoned or ambiguous sources, and a code interpreter checks only the encoded computation. The model still decides what to test, can misread evidence, and may stop prematurely. Some tasks use model-based evaluation.

## Course role

Pair with *Large Language Models Cannot Self-Correct Reasoning Yet*. Together they replace the vague slogan “reflection helps” with a conditional claim: correction is credible when a runtime introduces relevant, independent evidence and preserves it in the loop.
