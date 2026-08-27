# Architecture and Repository Understanding

## Scope and a crucial distinction

Repository understanding includes retrieval, navigation, dependency models,
change-impact reasoning, and architectural hypothesis testing. Most current
“repo-level” agent papers solve the first three. They should not be described as
architecture recovery without an explicit high-level model and conformance test.

## Mechanism map

### Iterative textual context

RepoCoder alternates retrieval and generation for repository-level completion.
Agentless hierarchically narrows file → skeleton → edit location. These methods
show that concise selected context can beat feeding whole files, but they recover
task-relevant text, not design intent.

### Structural repository representations

RepoGraph supplies a code graph as a plug-in navigation layer and improves
multiple coding systems. AutoCodeRover exposes class/method-aware search APIs.
Both make structure actionable while remaining mostly task-local.

### Change-impact planning

[CodePlan](../literature/papers/codeplan.md) maintains a dependency graph and an
edit-obligation DAG. Each edit can create derived obligations, so the plan and
repository model co-evolve. This is currently the strongest agentic mechanism
in the cluster.

### Architecture conformance

[Software Reflexion Models](../literature/papers/software-reflexion-models.md)
map source facts into a hypothesized high-level model and compute convergence,
divergence, and absence. The human supplies the hypothesis and mapping; the tool
makes disagreement explicit. This is the standard that current “understanding”
claims usually do not meet.

## Reading decisions

**Strong:** CodePlan; Software Reflexion Models as foundational contrast.

**Other candidates:** RepoGraph, RepoCoder. Agentless and AutoCodeRover are
cross-listed under repair.

**Rejected claim pattern:** repository summarization or retrieval presented as
architecture recovery without a model, mapping, discrepancy semantics, or
validation procedure.

## Current assessment

- Literature maturity: **high for repository context, medium for dependency-aware
  planning, low for genuinely agentic architecture recovery**.
- Technical depth: very high in CodePlan and classical reflexion models.
- Course suitability: high only after merging repository planning with the
  architecture-recovery critique; not enough evidence for a standalone modern
  “agents recover architecture” week.

## Gaps and next searches

- Agents that propose architectural hypotheses/mappings and submit them to an
  independent conformance engine.
- Evaluation against maintained architecture documents and expert decisions,
  not only issue resolution.
- Model evolution after partial failure: invalidation, stale summaries, and
  incremental dependency/architecture updates.
- Forward/backward citation search around reflexion models plus ICSE/FSE/ASE
  architecture-recovery tracks using LLM terminology without assuming agency.
