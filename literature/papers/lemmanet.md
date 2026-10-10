# LemmaNet: Automated Lemma Discovery in Agentic Program Verification

## Decision

**Selected in the final v5 review; accepted in press at ASE 2026.** Primary
source: [ASE 2026 research program](https://conf.researchr.org/details/ase-2026/ase-2026-research-track/26/Automated-Lemma-Discovery-in-Agentic-Program-Verification).

## Mechanism

Frama-C first generates the proof-targeted VC. An offline program semantic
analyzer asks the model to express and prove a simpler source-level,
semantics-aware VC in Rocq; an obligation-aligned synthesizer then proposes
proved helper lemmas bridging that representation to the Frama-C VC. During
proof search, an adaptive lemma maintainer retrieves these lemmas and an online
adapter revises statements or representations in response to exact proof-state
errors. Ill-formed lemmas and their dependents are discarded; refined assertions
receive separate subproofs.

The semantics-aware VC is guidance, not trusted evidence. Soundness comes from
ultimately discharging the original Frama-C VC and every dependent helper lemma
in Rocq; the model is outside the trusted computing base. An incorrect semantic
interpretation can waste search or lose completeness but cannot validate an
unchecked proof.

## Evidence and limits

On 941 VCs from SV-COMP and NTP4VC, using the same GPT-5.2 backend and a
10-minute/100-step budget, LemmaNet proves 364 versus AutoRocq's 287, Copra's
240, and CoqHammer's 123. Removing offline synthesis, online adaptation, or the
program semantic analyzer reduces the total to 328, 302, and 301 respectively.
The strongest qualitative result is that 61 of 69 uniquely solved proofs using
helper lemmas bridge source- and verifier-level representations.

Limits are explicit: only 364/941 VCs are solved; most offline lemmas are short
single-purpose facts; adaptation can over-fixate and crowd out a simpler proof;
and evaluation uses one closed model, Rocq 8.18, Frama-C, and C programs. The
accepted paper and artifact are available, but final proceedings metadata should
still be rechecked after ASE 2026.

## Course role

Selected alongside LeanDojo, not instead of it. LeanDojo teaches the exact
interactive environment and retrieval boundary; LemmaNet teaches how uncertain
program comprehension can synthesize and adapt intermediate proof artifacts
without entering the validity boundary. It replaces HoarePrompt, whose
program-logic terminology did not yield checked semantics.
