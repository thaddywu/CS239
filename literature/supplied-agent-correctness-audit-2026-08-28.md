# Supplied Agent-Correctness List Audit — 2026-08-28

## Audit question

Which items in the supplied list add a genuinely agent-specific correctness,
security, recovery, or HCI mechanism without falling back to old foundational
literature, benchmark accumulation, or agent washing?

## Fully inspected and recorded in the canonical index

- **TraceFix** — selected published primary: generated coordination protocol,
  TLC counterexamples, repair, and runtime monitoring.
- **Atomix** — strongest unpublished transaction/effect-semantics paper.
- **Agent-C** — strong unpublished temporal-policy challenger to AgentSpec.
- **Language-Based Agent Control** — strong unpublished PL/capability/IFC
  challenger to CaMeL.
- **VIGIL** — good unpublished skill-contract monitor, but overlaps AgentSpec.
- **Semantic Commit** — selected published SE+HCI primary on changing persistent
  intent.
- **ToolGuard** — published and usable as background, but narrower than AgentSpec.
- **SagaLLM** — published, but rejected as a primary after method/evaluation review.

## Already in the knowledge base

- **AgentSpec** is selected.
- **Semia** is a preprint candidate.

## Useful frontier items, publication not established strongly enough for a primary

- **Progent**, **PFI**, **ClawLess**, and **SkillScope** explore privilege,
  prompt-flow integrity, system-level mediation, and task-conditioned least
  privilege. They remain follow-up candidates, but the current published pair
  already covers a stronger common foundation.
- **MANTRA**, **Multi-User Large Language Model Agents**, **Hierarchical
  Alignment**, and **Lean4Agent** are relevant watch items for compliance
  benchmark synthesis, multiple principals, instruction conflict, and formal
  trajectory modeling. Their present evidence does not justify displacing a
  published mechanism.
- **SAFEFLOW**, **Collaborative Memory**, **SkVM/SkillRT**, and the skill
  scheduling-structural-logical representation are interesting runtime designs;
  Atomix presents the clearest correctness boundary among this group.
- **The Verifier Tax** is a useful empirical warning about horizon-dependent
  safety/success tradeoffs, but it is not itself an enforcement abstraction.

## Benchmark-only cluster

tau-bench, SafeToolBench, ST-WebAgentBench, TRAJECT-Bench, OpenAgentSafety, and
ATBench improve task, safety, or trajectory diagnosis coverage. They can supply
evaluation cases or a lecture table, but assigning several would turn the
correctness unit into benchmark comparison rather than mechanism comparison.
MANTRA belongs near this cluster despite its SMT validation of generated
benchmark specifications.

## Correctness-adjacent but not the missing syllabus mechanism

- Weak-Link Optimization, Guided Collaboration, Mixture of Thoughts, advisor
  models, FrugalGPT, RouterEval, LLMRouterBench, generic model routing, SE-task
  routing, and agent distillation primarily optimize cost, allocation, or model
  capability.
- These may be good systems/performance papers, but they do not explain how an
  agent application remains correct when policies evolve, actions interleave,
  authority changes, or external effects cannot be undone.

## Excluded by recency or identification rule

- **Cedar** and **How We Built Cedar** are strong authorization/verification
  work, but are 2024 non-agent foundations and are unnecessary under the
  current recency preference.
- The exact scholarly records for **Agent Policy Enforcement**, **Obligation-
  Aware Agent-C**, **Zero Trust for AI Agents**, and **A Framework for Extracting
  Access Control Policies from Natural Language Artifacts** were not verified
  from the supplied titles; no metadata was guessed.
- **SkillRT** and **SkVM** appear to name the same 2026 skill-runtime paper, not
  two independent readings.

## Final course decision

The instructor approved both **TraceFix** and **Semantic Commit** as primaries,
bringing the final list to 19 papers. TraceFix supplies the formal/runtime
coordination mechanism; Semantic Commit supplies the complementary SE+HCI view
of evolving intent. **Atomix** remains a clearly labeled frontier handout and a
publication-status watch item.
