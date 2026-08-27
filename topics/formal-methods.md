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

### Specifications and model checking

- [PAT-Agent](../literature/papers/pat-agent.md) plans and emits CSP# models,
  checks them with PAT, and repairs them from counterexamples. A full-pass model
  is internally verified but may still misrepresent the natural-language system.
- [Agentic Specification Generator](../literature/papers/agentic-specification-generator.md)
  generates different Move contract clauses with specialized agents and uses
  static inlining plus prover feedback.
- [PropertyGPT](../literature/papers/propertygpt.md) transfers reusable formal
  properties to unseen smart contracts and checks them with a dedicated prover.

## Reading decisions

**Strong:** LeanDojo; Draft, Sketch, and Prove; LEGO-Prover; AlphaGeometry;
PAT-Agent. The two specification-generation papers are strong cross-listings.

**Other candidate:** Don't Trust: Verify. A single week should use two primary
papers plus one optional; trying to cover all proof systems would become a list.

## Current assessment

- Literature maturity: **high** for proof search, interaction, verified
  artifacts, and checker-guided model/specification synthesis; medium for
  faithful autoformalization.
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

## Due diligence audit — 2026-08-27

### Previously believed

Theorem proving already supported a technically deep week; autoformalization was
promising but thin on faithful software-system models and repository contracts.

### New papers checked

- Fully inspected PAT-Agent, PropertyGPT, and Agentic Specification Generator.
- Checked Event-B Agent (FSE 2026 program) and *Automated Lemma Discovery in
  Agentic Program Verification* (ASE 2026 program); both are important successors
  but lacked a final proceedings record at audit time and did not displace the
  verified additions.
- Inspected recent formal-method and PL venue programs for agentic model repair,
  contract generation, and verified-code work rather than searching only for
  “agent” in titles.

### Important additions

- [PAT-Agent](../literature/papers/pat-agent.md): planning, CSP# synthesis,
  counterexample-guided repair; **very high technical depth** and a strong
  model-checking primary.
- PropertyGPT and Agentic Specification Generator: **very high technical depth**
  cross-listings that connect formal properties to software code.

### Stronger replacements

PAT-Agent should replace LEGO-Prover as the second Week 6 primary when the goal
is mechanism breadth; LEGO-Prover remains the strongest verified-memory optional.
LeanDojo remains the best environment/interface primary.

### Judgment

**UPHELD overall; the autoformalization subtopic is materially strengthened.**

### Why

The week now spans interactive proof environments, natural-language model
synthesis, counterexample repair, and property generation rather than two
theorem-proving systems. Formal validation still cannot prove that an inferred
statement captures user intent, which supplies the central classroom dispute.
