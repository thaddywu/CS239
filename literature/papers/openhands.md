# OpenHands: An Open Platform for AI Software Developers as Generalist Agents

## Metadata

ICLR 2025. [Primary record](https://proceedings.iclr.cc/paper_files/paper/2025/hash/a4b6ad6b48850c0c331d1259fc66a69c-Abstract-Conference.html).

## One-line idea

Provide an open, sandboxed runtime and extensible action/skill layer for multiple
software-agent implementations and evaluation tasks.

## Technical core and architecture

The platform separates agent logic from a Docker-backed runtime exposing shell,
files, code editing, browsers, and observations. AgentSkills adapt ACI utilities;
arbitrary images improve task reproducibility and dependency control.

## Evaluation and limits

The paper evaluates several agents across 13 benchmarks/tasks and documents
runtime capabilities. Breadth is the artifact's strength and the reading's
weakness: platform, models, prompts, and tasks vary, so causal mechanism claims
are less focused than SWE-agent's ACI ablations.

## Course placement and decision

**Candidate / Week 1 or Week 10 optional.** Important infrastructure and project
reference, not one of the two primary architecture readings.
