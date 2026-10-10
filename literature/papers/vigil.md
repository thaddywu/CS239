# VIGIL: Runtime Enforcement of Behavioral Specifications in AI Agent Skills

## Decision

**High-quality preprint candidate.** Current source is
[arXiv 2606.26524](https://arxiv.org/abs/2606.26524).

## Mechanism

VIGIL abstracts raw tool executions into typed events, compiles natural-language
skill requirements into a finite-trace policy language, grounds temporal,
argument, and cross-call value-flow relations, and checks each statement with
SMT. It localizes the invocation and trace context responsible for a violation.

## Evidence

The main corpus contains 152 real agent traces, including 72 violations. VIGIL
finds 69 of them (95.8% recall) at 89.6% precision and reports 34 confirmed
specification or execution defects across deployed skill ecosystems. Ablations
show large losses from removing argument grounding or policy structure.

## Limits

The trusted event collector cannot see effects hidden inside opaque scripts;
LLM compilation can drop semantic qualifiers and over-block benign calls. Thus
SMT checking is exact only after a fallible policy/trace lifting step. Average
end-to-end checking takes 4.38 seconds, dominated by policy compilation.

## Course role

VIGIL is a useful frontier handout on multi-call skill contracts, but overlaps
AgentSpec's runtime-enforcement slot and is not yet peer reviewed.
