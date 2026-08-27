# LEGO-Prover: Neural Theorem Proving with Growing Libraries

## Decision

**Strong candidate.** Primary source: [ICLR 2024 proceedings](https://proceedings.iclr.cc/paper_files/paper/2024/hash/85dca46374dc0f27b4bb5f265b3d17f0-Abstract-Conference.html).

## Problem and mechanism

Long proofs become easier when reusable intermediate lemmas exist. LEGO-Prover shares a verified skill library between a prover and an evolver. The prover decomposes an informal solution into subgoals, retrieves lemmas, formalizes block by block, and stores newly proved lemmas. In parallel, the evolver generalizes or transforms stored lemmas and solves outstanding requests. Only Isabelle-accepted artifacts enter the core lemma store.

The memory is typed and executable, not a transcript: statements and proofs can be copied, composed, and rechecked.

## Evidence

- The reported miniF2F pass rate rises from prior 48.0% to 57.0% on validation and from 45.5% to 50.0% on test.
- More than 20,000 verified skills are created. Removing the growing library costs 4.9 points after 100 attempts; a compute-balanced analysis still shows a smaller 2.1-point benefit.
- Performance advantage grows as the library matures, supporting a compounding-memory claim.

## Limits

The evolver consumes substantial extra tokens, retrieval can surface irrelevant lemmas, and repeated attempts are costly. Formal verification prevents invalid library entries but not useless duplication or bias toward the benchmark's theorem distribution.

## Course role

Use as the strongest agent-memory reading. Contrast with MemGPT: one stores mostly untyped conversational content; the other stores independently verified, reusable capabilities.
