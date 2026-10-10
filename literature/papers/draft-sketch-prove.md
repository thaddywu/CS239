# Draft, Sketch, and Prove: Guiding Formal Theorem Provers with Informal Proofs

## Decision

**Selected for the final 20.** Primary source: [ICLR 2023 OpenReview](https://openreview.net/forum?id=SMa9EAovKMC).

## Problem and mechanism

Direct formal-proof generation forces a model to get mathematical ideas and proof-assistant syntax right simultaneously. DSP decomposes the task:

1. produce or accept an informal proof draft;
2. translate its structure into a formal sketch containing holes;
3. let an off-the-shelf automated prover fill those holes and have the proof assistant check the result.

The sketch communicates global intent while leaving locally searchable obligations to a component better suited for exact reasoning.

## Evidence and limits

The paper reports an increase from 20.9% to 39.3% on its main miniF2F setting and studies both human and generated informal drafts. The decomposition is interpretable: failures can be attributed to informal reasoning, formalization, or hole discharge.

Success still assumes a correct formal theorem statement. A persuasive informal proof can lead to a misleading sketch, and automation may fail for mathematically easy steps that require unavailable library lemmas. Dataset size and olympiad style constrain generalization.

## Course role

Read beside LeanDojo or LEGO-Prover. DSP is the clearest example of an intermediate artifact acting as an interface contract between a generative model and a verifier. Compare with CodePlan's edit-obligation graph.

## Reading-list v5 decision

**Strong candidate, no longer primary.** Technical depth is unchanged. LeanDojo
retains the exact proving slot, while HoarePrompt creates a more software-specific
contrast between program-logic structure and genuine verification.
