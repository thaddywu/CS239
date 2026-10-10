# GPTSwarm: Language Agents as Optimizable Graphs

## Decision

**Candidate.** Primary source: [ICML 2024 proceedings](https://proceedings.mlr.press/v235/zhuge24a.html).

## Mechanism and evidence

GPTSwarm unifies agents as computational graphs: nodes are LLM, tool, or
ordinary-function operations, while edges carry information. Graphs compose
recursively into multi-agent hierarchies; separate optimizers update node
prompts and communication edges.

This is a clean answer to how components are wired rather than merely added.
The experiments span reasoning, coding, crosswords, and tool use, but optimize
heterogeneous task-specific graphs and do not isolate a stable set of
architecture ingredients. Only communication edges are optimized; internal
node topology, shared-state semantics, and scaling beyond the tested small
graphs remain open.

## Course role

Good historical bridge from hand-built agent loops to architecture search.
AgentSquare is newer and gives a clearer planning/reasoning/tool/memory
vocabulary; MaAS gives the stronger query-adaptive cost-allocation follow-up.

