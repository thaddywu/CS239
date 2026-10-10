# PropertyGPT: LLM-driven Formal Verification of Smart Contracts through Retrieval-Augmented Property Generation

## Decision

**Strong candidate; MSG receives the v3 specification slot.** Primary source: [NDSS 2025 proceedings](https://www.ndss-symposium.org/ndss-paper/propertygpt-llm-driven-formal-verification-of-smart-contracts-through-retrieval-augmented-property-generation/).

## One-line idea

Retrieve expert-written smart-contract properties, adapt them to new code, use
compiler/static-analysis feedback to repair them, rank them, and discharge them
with a dedicated prover.

## Technical core

PropertyGPT generates invariants, pre-/postconditions, and rules rather than
only example tests. Retrieval provides reusable specification patterns;
iterative compiler feedback rejects malformed properties; multi-dimensional
ranking selects candidates; formal verification turns a plausible property into
an executable analysis artifact.

## Evidence and limits

- On 90 ground-truth properties, the paper reports 80% recall and 64% precision;
  feedback repair raises the compilable fraction from 63% to 87%.
- It detects 26 of 37 evaluated CVEs/incidents and reports 12 previously unknown
  vulnerabilities, but these outcomes mix property generation and prover power.
- The method is specific to Solidity/Certora-style properties, and semantic
  equivalence labels require expert judgment.

## Course role

The strongest correction to the earlier “no durable property generation” claim.
Pair with QuickCheck to distinguish property discovery from generator/shrinker
semantics and with ImpossibleBench to discuss specification authority.
