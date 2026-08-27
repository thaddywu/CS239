# LeanDojo: Theorem Proving with Retrieval-Augmented Language Models

## Decision

**Strong candidate and formal-environment anchor.** Primary source: [NeurIPS 2023 proceedings](https://proceedings.neurips.cc/paper_files/paper/2023/hash/4441469427094f8873d0fecb0c4e1cee-Abstract-Datasets_and_Benchmarks.html).

## Problem and mechanism

Proof models need exact environment interaction and access to a huge, dependency-constrained premise library. LeanDojo instruments Lean to extract proof states, tactics, premises, and source locations, and supplies a programmatic environment in which a prover can execute tactics and receive kernel feedback.

ReProver retrieves accessible premises and conditions tactic generation on them. “In-file negatives” provide hard retrieval negatives. The environment and traced corpus are at least as important as the particular model: they define observable state and legal actions for future agents.

## Evidence

- The benchmark extracts 98,734 theorems/proofs, 217,776 tactics, and roughly 130K premises from 3,384 mathlib files.
- A novel-premises split requires test proofs to use premises not observed in training, countering inflated random-split results.
- Retrieval improves over non-retrieval baselines, especially where relevant library knowledge cannot fit in context.

## Limits

Tactic imitation inherits scarcity and style bias from human proofs. Success depends on a pinned Lean/mathlib version, and theorem-statement correctness is assumed. Kernel acceptance guarantees the generated proof, not that the original informal intent was formalized faithfully.

## Course role

Use to show what an unusually strong agent runtime looks like: typed state, executable actions, precise failure feedback, scoped resources, and an unforgeable validator. Compare its interface design with SWE-agent and its retrieval with RepoCoder.
