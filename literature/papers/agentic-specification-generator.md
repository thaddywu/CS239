# Agentic Specification Generator for Move Programs

## Decision

**Strong candidate.** Primary source: [ASE 2025 proceedings DOI](https://doi.org/10.1109/ASE63991.2025.00110).

## One-line idea

MSG assigns different Move specification clauses to specialized agents and uses
static inlining plus Move Prover feedback to synthesize reusable contracts.

## Technical core

Separate generators handle `aborts_if`, `modifies`, `ensures`, and loop
invariants; their outputs are ensembled and repaired against compiler/prover
feedback. Selective function inlining exposes facts hidden behind callees
without expanding everything, making program analysis part of generation.

## Evidence and limits

- The system produces verifiable specifications for 300 of 357 functions (84%)
  and 14 of 17 functions requiring loop invariants.
- The specialized agent design reaches 84% function coverage versus 53.5% for
  an all-in-one generator; removing prover feedback lowers coverage to 70.9%.
- Results are confined to Move/Aptos, and complex nested abort conditions remain
  a common failure.

## Course role

Strong optional bridge among testing, program analysis, and formal methods. It
shows that “multi-agent” is useful when roles correspond to distinct formal
languages and validators, not software-company personas.
