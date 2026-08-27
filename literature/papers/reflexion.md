# Reflexion: Language Agents with Verbal Reinforcement Learning

## Metadata

NeurIPS 2023. [Primary record](https://proceedings.neurips.cc/paper_files/paper/2023/hash/1b44b878bb782e6954cd888628510e90-Abstract-Conference.html).

## One-line idea

Convert task feedback into a verbal reflection, store it in episodic memory,
and condition a later attempt on that text without updating model weights.

## Technical core

An actor produces a trajectory, an evaluator supplies scalar or textual feedback,
and a reflection model writes a compact lesson. The next actor prompt includes
recent lessons, creating a retry loop with persistent natural-language state.

## Evaluation and limits

Experiments cover decision-making, programming, and reasoning tasks and show
substantial improvement over repeated attempts. The evaluator may leak privileged
feedback; reflections are neither verified nor guaranteed causal; memory can
preserve wrong diagnoses. The “reinforcement learning” label is metaphorical
because parameters do not change.

## Course placement and decision

**Candidate / Week 8 optional.** Teach only beside the intrinsic self-correction
negative result and CRITIC's external evidence.
