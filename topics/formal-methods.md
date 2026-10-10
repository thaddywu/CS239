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

## Final-selection v3 update — 2026-08-27

The final formal sequence is MSG → LeanDojo → Draft, Sketch, and Prove. These
teach three different contracts between uncertain and exact components:
generated software specifications checked by Move Prover; exact interactive
proof state plus retrieval/search; and informal global structure compiled into
formal holes discharged by a prover. PAT-Agent remains a strong optional
model-checking reading, but DSP has the cleaner decomposition and higher evidence
quality for the single available proof/synthesis slot. AlphaGeometry moves to
student frontier material because its mechanism is excellent but application-
specific and no longer beats a central software or correctness mechanism.

## Reading-list v5 update — 2026-08-27

The v5 core is [ARTEMIS](../literature/papers/artemis.md) followed by
[LeanDojo](../literature/papers/lean-dojo.md). ARTEMIS uses structured language
and balanced distinguishing traces to validate intended requirements; LeanDojo
assumes a formal statement and exposes exact proof state and kernel checking.
[HoarePrompt](../literature/papers/hoareprompt.md) is assigned in program
analysis precisely because its program-logic structure is not a proof.

MSG and Draft--Sketch--Prove move to strong alternatives rather than being
downgraded technically. [LemmaNet](../literature/papers/lemmanet.md) is the most
important accepted-in-press recheck; [Event-B Agent](../literature/papers/event-b-agent.md)
remains a candidate pending stronger comparative evidence.

## Final adversarial review — 2026-08-28

[LemmaNet](../literature/papers/lemmanet.md) replaces HoarePrompt. Full-paper
inspection found an offline semantics-aware VC, obligation-aligned proved helper
lemmas, an adaptive lemma store, and proof-state-guided online revision. The
original Frama-C VC and every imported/refined lemma are checked in Rocq, so an
incorrect model interpretation harms search completeness rather than proof
validity. Component ablations on 941 VCs support the mechanism.

LeanDojo remains primary for a different reason: it defines the exact
environment, retrieval boundary, and kernel-feedback interaction. Draft–Sketch–
Prove, Agentic Specification Generator, and PAT-Agent remain strong alternatives
but do not displace this environment-versus-adaptive-artifact pair.

## Reading-list v7 placement — 2026-08-29

The schedule has one proof meeting, so [LemmaNet](../literature/papers/lemmanet.md)
is the primary: it connects source semantics and Frama-C verification
conditions to adaptive helper lemmas that Rocq checks exactly.
[LeanDojo](../literature/papers/lean-dojo.md) remains the strongest alternate and
is not downgraded technically; it would replace LemmaNet if the instructor
prefers the foundational proof-environment, retrieval, and action-interface
lesson over agentic program verification.
