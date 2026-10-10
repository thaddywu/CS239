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

[SemRef](../literature/papers/semref.md) is the first direct modern counterexample
found in this audit: it takes explicit recovered module structures from existing
tools, uses LLM semantics plus dependencies to refine them, and evaluates the
result against architecture ground truth. It refines a hypothesis rather than
independently discovering and checking design intent.

## Reading decisions

**Strong:** CodePlan; Software Reflexion Models as foundational contrast.
**Direct modern candidate:** SemRef, with a publication-record caveat.

**Other candidates:** RepoGraph, RepoCoder. Agentless and AutoCodeRover are
cross-listed under repair.

**Rejected claim pattern:** repository summarization or retrieval presented as
architecture recovery without a model, mapping, discrepancy semantics, or
validation procedure.

## Current assessment

- Literature maturity: **high for repository context, medium for dependency-aware
  planning, and low/medium for genuinely agentic architecture recovery**.
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

## Due diligence audit — 2026-08-27

### Previously believed

Repository retrieval and change-impact planning were mature, but modern agentic
architecture recovery lacked an explicit architecture plus evaluation against
conformance or ground truth.

### New papers checked

- Fully inspected SemRef (ICSE 2026 research track).
- Checked IGSIL (ASE 2025), GraphCoder (ASE 2024), and *Beyond Lexical:
  Functional Semantics and Fusion for Precise Architecture Recovery* (SANER
  2026). These cover issue localization/code graphs or stronger non-agent
  recovery baselines, but not the same direct mechanism.
- Rechecked the classical reflexion-model citation path and current architecture
  tracks, including dependency graphs, design recovery, and conformance terms.

### Important additions

[SemRef](../literature/papers/semref.md): iterative semantic/dependency refinement
of recovered module structures; **high technical depth** and suitable as a
modern primary/contrast after its proceedings record is resolved.

### Stronger replacements

SemRef is a stronger direct architecture-recovery reading than RepoGraph or
RepoCoder, but it does not replace CodePlan for change-impact planning or
Software Reflexion Models for explicit discrepancy semantics.

### Judgment

**WEAKENED.**

### Why

The categorical claim that modern work stops at retrieval is false: SemRef
directly improves recovered architectures and tests against ground truth. One
LLM-assisted refinement system does not yet provide enough independent
mechanisms for a standalone week, and its final proceedings/DOI record was not
located. Repository understanding remains well supported as a merged module.

## Final-selection v3 update — 2026-08-27

[Software Reflexion Models](../literature/papers/software-reflexion-models.md)
is promoted to a full primary day. A new targeted check also found *A Holistic
Approach to Design Understanding Through Concept Explanation* (TSE 2025), but
only its abstract and metadata were inspectable in this pass, so it is recorded
as `skimmed` rather than promoted. SemRef remains the most direct modern LLM
candidate but still lacks a final proceedings record. The final sequence uses
CodePlan for changing edit obligations, IRIS for whole-program dataflow, and
reflexion models for explicit high-level hypotheses and discrepancy semantics.

## Reading-list v4 update — 2026-08-27

Software Reflexion Models moves to background rather than consuming a primary
slot. The focused modern check added three decision points:

- [RepoProbe](../literature/papers/repoprobe.md) supplies strong negative
  evidence and a checklist-based architecture-understanding benchmark, but no
  recovery mechanism.
- [Automated Software Architecture Design Recovery](../literature/papers/automated-architecture-design-recovery.md)
  evaluates prompting and self-reflection but does not isolate a deep agentic
  abstraction.
- [Can Agents reconstruct microservice architecture?](../literature/papers/can-agents-reconstruct-microservice-architecture.md)
  is an informative early negative result with a lightweight role-guided method.

The primary readings are therefore CodePlan and IRIS. The absence of a modern
agentic recovery paper at the required depth is recorded as a literature gap,
not filled with a weaker paper.

## Reading-list v5 update — 2026-08-27

The decision is upheld but the previous “CodePlan and IRIS are the primary
readings” statement is superseded. The generic understanding block is removed;
IRIS remains under program analysis, CodePlan becomes a strong maintenance
alternative, and RepoProbe remains negative evaluation background. No newly
screened 2023--2026 recovery paper supplied a maintained architecture model or
analysis mechanism strong enough to force this topic back into the syllabus.
