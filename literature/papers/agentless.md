# Demystifying LLM-based Software Engineering Agents (Agentless)

## Decision

**Strong candidate and essential counterexample.** Primary source: [FSE 2025 program](https://conf.researchr.org/details/fse-2025/fse-2025-research-papers/85/Demystifying-LLM-based-Software-Engineering-Agents).

## Problem and mechanism

Agentless tests whether expensive open-ended tool loops are needed for repository issue repair. It fixes the computation into three phases: hierarchical localization, repair sampling, and patch validation. Localization moves from files to class/function skeletons to edit lines, combining retrieval and model judgments while aggressively shrinking context. Repair produces small diff candidates. Validation generates reproduction tests, executes them on the original and patched versions, filters regressions, and ranks candidates.

## Evidence

- The paper reports 32% (96/300) in the main ablation configuration and a later 32.67%/98 fixes result on SWE-bench Lite at low cost.
- Combined prompt and embedding file localization contains the ground-truth file in 81.67% of cases; full-file context is worse than compact skeletons.
- Reproduction-test selection raises the ablation result from 25.67% under majority vote to 32%, more than regression tests alone.

## Limits

“Agentless” is a rhetorical boundary: the system still uses repeated model calls and generated executable tests. Evaluation is concentrated on one benchmark family, and reproduction tests can encode the same misunderstanding as patches. Later benchmark contamination and infrastructure corrections complicate raw-score comparisons.

## Course role and comparisons

Pair directly with SWE-agent. Students should identify which benefits arise from interaction, hierarchy, sampling, compact representations, or executable validation—not from the label “agent.”
