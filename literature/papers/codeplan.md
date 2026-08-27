# CodePlan: Repository-level Coding using LLMs and Planning

## Decision

**Strong candidate and preferred repository-scale reading.** Primary source: [FSE 2024 DOI](https://doi.org/10.1145/3643757).

## Problem and mechanism

A seed edit can change signatures, types, and behavior across callers, overrides, and dependent files. CodePlan represents required edits as a plan DAG. Each node is a code block, instruction, and status; edges record why another edit follows. Incremental dependency analysis, change classification, and a change-may-impact relation extend the plan after each merged edit.

Prompts contain spatial context from the dependency graph and temporal context from predecessor edits. The dependency graph is updated as code changes. A build, type checker, tests, or another oracle validates the final repository; diagnostics become new seed obligations.

## Evidence

- Evaluates C# package migration and Python temporal edits requiring changes across 2–97 files.
- The final FSE program reports five of seven repositories passing validity checks while same-context baselines without planning pass none (the earlier arXiv version reported five of six).
- The oracle-only repair baseline can blame downstream symptoms and even undo the intended seed change; explicit cause/effect planning avoids that failure.

## Limits

Only a small number of repositories and two task families are used, including proprietary cases. Change-may-impact analysis is intentionally incomplete and language-specific. Passing the selected oracle does not establish behavioral equivalence.

## Course role

CodePlan is planning grounded in software semantics, unlike generic tree search. Pair with classical reflexion models to distinguish forward change-impact reasoning from recovering and checking an architecture hypothesis.
