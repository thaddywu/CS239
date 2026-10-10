# From Language Models to Agentic AI

## Decision

**Candidate and the closest current one-paper engineering overview.** Verified
against the [Cognitive Computation version of record](https://doi.org/10.1007/s12559-026-10619-1),
published 24 August 2026.

## Architecture and evidence

Bajoria et al. propose six modules: perception/input encoding, memory,
reasoning/planning, tool interface, actuation, and feedback/oversight. They then
classify systems along autonomy, tool use, collaboration, and safety/governance,
and discuss single-agent loops, tool integration, multi-agent coordination,
failure modes, process-level evaluation, and deployment controls.

This is unusually close to the course's desired system boundary because it
distinguishes the tool interface from external actuation and makes oversight a
first-class loop. The limitation is evidence: the architecture is a synthesis
of prior systems, not a mechanism validated through controlled experiments.
The paper is also only days old at this audit, so there is no field uptake yet,
and portions of the bibliography are broader than the architectural claims.

## Course role

Use selected architecture/taxonomy sections as instructor framing. Do not use
it to replace AgentSquare or SWE-agent: those papers create technical arguments
about composition/search and the agent-computer boundary that a survey cannot.
