# Agents for Testing and Program Repair

## Scope and evaluation model

A repair system contains at least four logically distinct problems: localization,
patch proposal, oracle construction, and candidate selection. “Resolved” often
means that available tests pass; it does not imply semantic correctness. The map
therefore tracks both the control loop and the strength/independence of evidence.

## Mechanism map

### Repository repair controllers

- [SWE-agent](../literature/papers/swe-agent.md): open-ended interaction through
  a carefully designed ACI.
- [AutoCodeRover](../literature/papers/autocoderover.md): structure-aware search,
  iterative retrieval, optional SBFL, and bounded test feedback.
- [RepairAgent](../literature/papers/repairagent.md): repair-specific tools plus
  a finite-state controller.
- [Agentless](../literature/papers/agentless.md): fixed hierarchical localization,
  patch sampling, and executable reproduction-test selection.

These systems form a control-spectrum experiment: general loop → domain-guided
loop → FSM → deterministic pipeline. Raw pass rates are less instructive than
which decisions are delegated to the model.

### Test generation

- [CodaMOSA](../literature/papers/codamosa.md) invokes an LM only when
  evolutionary coverage search plateaus, then feeds successful tests back into
  search.
- CoverUp iterates on concrete coverage gaps and shows feedback accounts for a
  large fraction of its gain.
- QuickCheck supplies the missing foundational abstraction: executable
  properties plus generators, rather than example tests alone.

### Reusable properties and specifications

- [PropertyGPT](../literature/papers/propertygpt.md) retrieves and adapts
  invariants, pre-/postconditions, and rules, then uses compiler/static-analysis
  feedback and a prover to turn generations into reusable verification inputs.
- [Agentic Specification Generator](../literature/papers/agentic-specification-generator.md)
  separates Move clause languages across specialized agents and uses selective
  inlining plus Move Prover feedback, including loop invariants.

These are not full QuickCheck-style property-based testing systems: they do not
jointly synthesize generators and shrink counterexamples. They do establish a
substantial property/specification-generation cluster beyond example tests.

### Oracle failure and specification gaming

[ImpossibleBench](../literature/papers/impossiblebench.md) intentionally
conflicts specifications and tests. A passing solution then reveals exploitation,
not success. AutoCodeRover's manual audit similarly finds only about two thirds
of passing patches acceptable.

## Reading decisions

**Strong:** AutoCodeRover, Agentless, CodaMOSA, ImpossibleBench, PropertyGPT,
and Agentic Specification Generator. RepairAgent is a strong optional third
repair paper.

**Other candidates:** SWE-bench for task/evaluation history, CoverUp, QuickCheck,
and SWE-agent cross-listed from architecture.

**Not selected:** leaderboard-only system reports and papers that do not audit
test adequacy, contamination, cost, or matched model/runtime baselines.

## Current assessment

- Literature maturity: **high for repository repair and coverage-guided test
  generation; medium for domain-specific property/invariant discovery; low for
  end-to-end generator/property/shrinker systems**.
- Technical depth: high where program structure, search, or executable evidence
  constrains the loop.
- Course suitability: very high; it supports a concrete agent-vs-pipeline debate.

## Gaps and next searches

- Property and invariant synthesis that survives beyond one generated patch.
- Patch validation with independently derived tests, metamorphic relations,
  differential execution, and formal contracts.
- Evaluation beyond Python/SWE-bench and beyond passing visible tests.
- Recovery from destructive or partially applied edits, including transactional
  workspace state and dependency/build migrations.

## Due diligence audit — 2026-08-27

### Previously believed

Repair and coverage-guided generation were mature, but agentic property-based
testing was too thin for a standalone unit and durable property generation was
largely missing.

### New papers checked

- Fully inspected PropertyGPT (NDSS 2025) and Agentic Specification Generator
  (ASE 2025).
- Screened Fuzz4All, TitanFuzz, LLM metamorphic/property papers in recent SE
  programs, and workshop papers *From Prompts to Properties* and LLanMER.
- For repair, checked Amur (ASE 2025), CausalRepair (ISSTA 2026), and AROP
  (ICSE 2026); none changes the Agentless-centered control-spectrum story.

### Important additions

- [PropertyGPT](../literature/papers/propertygpt.md): reusable formal property
  generation with independent checking; **very high technical depth**.
- [Agentic Specification Generator](../literature/papers/agentic-specification-generator.md):
  modular contract and invariant generation with prover feedback; **very high
  technical depth**.

Both support graduate discussion about compilation versus semantic adequacy,
specification authority, and whether prover feedback is independent evidence.

### Stronger replacements

No repair primary is replaced. The two specification papers replace the earlier
absence of a modern property-generation reading, not QuickCheck's foundational
role. No stronger peer-reviewed alternative found in this audit for the current
repair pair or for CodaMOSA's search/LLM division of labor.

### Judgment

**WEAKENED overall: repair and testing UPHELD; property-based testing WEAKENED.**

### Why

LLMs now generate reusable, prover-checked properties and invariants, so “only
example tests” is no longer accurate. The strict PBT claim still stands because
the literature does not yet offer a mature agent loop that jointly maintains
properties, generators, shrinking, and regression semantics across repositories.
