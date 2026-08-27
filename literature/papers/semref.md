# Semantic-Enhanced Automatic Refinement of Architecture Recovery Results Using LLMs

## Decision

**Candidate.** Primary source: [ICSE 2026 research-track program](https://conf.researchr.org/details/icse-2026/icse-2026-research-track/72/Semantic-Enhanced-Automatic-Refinement-of-Architecture-Recovery-Results-Using-LLMs).
The conference record is authoritative for peer review, but no final proceedings
or DOI record was located during the audit.

## One-line idea

SemRef uses LLM semantic judgments plus source dependencies to refine module
clusters produced by ten existing architecture-recovery tools.

## Technical core

Rather than label retrieval “understanding,” the system starts from an explicit
recovered architecture, detects misplaced modules, iteratively restructures the
hierarchy, and checks each move against dependency evidence. It also generates
module summaries after structural refinement.

## Evidence and limits

- Across nine systems and 90 tool/project inputs, all starting recoveries improve;
  reported normalized gains span 17.72–43.35% over five recovery metrics.
- Ablations identify iterative refinement as the largest contribution, with
  semantic and structural stages contributing differently.
- Nine projects and known ground-truth decompositions limit external validity;
  LLM leakage/hallucination remain threats, and recovered clusters still do not
  necessarily equal design intent.

## Course role

Important direct counterexample to the claim that modern work stops at repository
retrieval. It weakens—but does not yet overturn—the “no standalone agentic
architecture-recovery week” judgment because it is one strong system, not a
diverse mechanism cluster.
