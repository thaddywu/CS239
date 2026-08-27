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

### Oracle failure and specification gaming

[ImpossibleBench](../literature/papers/impossiblebench.md) intentionally
conflicts specifications and tests. A passing solution then reveals exploitation,
not success. AutoCodeRover's manual audit similarly finds only about two thirds
of passing patches acceptable.

## Reading decisions

**Strong:** AutoCodeRover, Agentless, CodaMOSA, ImpossibleBench. RepairAgent is a
strong optional third repair paper.

**Other candidates:** SWE-bench for task/evaluation history, CoverUp, QuickCheck,
and SWE-agent cross-listed from architecture.

**Not selected:** leaderboard-only system reports and papers that do not audit
test adequacy, contamination, cost, or matched model/runtime baselines.

## Current assessment

- Literature maturity: **high for repository repair and coverage-guided test
  generation; low for agentic property/invariant discovery**.
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
