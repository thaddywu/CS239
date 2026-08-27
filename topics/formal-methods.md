# Autoformalization, Formal Methods, and Theorem Proving

## Why this cluster matters

Proof assistants offer nearly ideal agent infrastructure: typed observable
state, small executable actions, precise failure feedback, scoped libraries, and
a validator the model cannot persuade. They let the course study architecture
without confusing fluency for correctness.

## Mechanism map

### Environment and retrieval

[LeanDojo](../literature/papers/lean-dojo.md) traces Lean source and proof states,
provides a gym-like interaction API, and retrieves accessible premises. Its
novel-premise split tests library generalization rather than near-duplicate proof
memorization.

### Decomposition through intermediate artifacts

[Draft, Sketch, and Prove](../literature/papers/draft-sketch-prove.md) maps an
informal draft to a formal sketch with holes, which an existing prover fills.
The sketch is an interface contract between uncertain global reasoning and exact
local discharge.

### Verified, growing memory

[LEGO-Prover](../literature/papers/lego-prover.md) creates, evolves, retrieves,
and reuses a library of kernel-verified lemmas. It is the corpus's strongest
example of memory whose entries have enforceable validity and compositional use.

### Neural proposal plus symbolic closure

[AlphaGeometry](../literature/papers/alphageometry.md) learns auxiliary
constructions and lets a symbolic engine exhaust their consequences. The
learned component expands the search language; the symbolic component certifies
deduction.

### Autoformalization as validation

*Don't Trust: Verify* translates quantitative problems and candidate solutions
to Isabelle and rejects internal inconsistency. It bridges proof technology to a
general agent-verification pattern, but a wrong formalization can be perfectly
proved.

## Reading decisions

**Strong:** LeanDojo; Draft, Sketch, and Prove; LEGO-Prover; AlphaGeometry.

**Other candidate:** Don't Trust: Verify. A single week should use two primary
papers plus one optional; trying to cover all proof systems would become a list.

## Current assessment

- Literature maturity: **high** for proof search, interaction, and verified
  artifacts; medium for faithful autoformalization.
- Technical depth: very high.
- Course suitability: very high even for an SE audience, provided readings are
  framed around runtime design, interfaces, memory, and verification.

## Gaps and next searches

- Faithfulness of informal-to-formal statements; proof correctness does not
  repair a mistranslated requirement.
- Proof-agent recovery policies and cost-aware search, not only pass rate.
- Formal software properties and contracts at repository scale.
- Citation chaining from LeanDojo/LEGO-Prover into 2025–2026 proof-assistant
  systems, with careful checks for benchmark leakage and compute scaling.
