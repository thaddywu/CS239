# PAGENT: Program Analysis Guided LLM Agent for PoC Generation

## Decision

**Candidate, not selected; accepted in press at ISSTA 2026.** Current source:
[arXiv 2604.07624](https://arxiv.org/abs/2604.07624).

PAGENT uses static rule analysis plus sanitizer profiling and coverage to guide
proof-of-concept generation, reporting a 132% improvement over a prior agentic
baseline. It is more structured than prompt-only exploit generation, but its
security task is narrower and the symbolic/proposal boundary is less generally
illuminating than Gordian or AutoCodeSherpa.
