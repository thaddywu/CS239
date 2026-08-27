# Don't Trust: Verify — Grounding Quantitative Reasoning with Autoformalization

## Metadata

ICLR 2024. [Primary record](https://proceedings.iclr.cc/paper_files/paper/2024/hash/0a79ecda13603817de4cdfc68b417e89-Abstract-Conference.html).

## One-line idea

Autoformalize a problem and candidate solution in Isabelle and use consistency
checking to rank or reject model answers.

## Technical core

The model translates informal quantitative statements and reasoning into formal
artifacts. Isabelle checks whether the candidate is internally consistent with
the formalized problem; the result becomes a selection heuristic rather than an
unverified self-critique.

## Evaluation and limits

Across GSM8K, MATH, and MultiArith, the method consistently beats vanilla
majority voting and improves GSM8K by more than 12% in the reported setting. A
wrong translation may be formally consistent, so autoformalization faithfulness
remains outside the kernel's guarantee.

## Course placement and decision

**Candidate / Week 6 optional.** Best bridge from theorem proving to general
agent validation; less technically complete than LeanDojo or LEGO-Prover.
