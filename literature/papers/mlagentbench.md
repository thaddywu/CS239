# MLAgentBench: Evaluating Language Agents on Machine Learning Experimentation

## Metadata

ICML 2024. [Primary record](https://proceedings.mlr.press/v235/huang24y.html).

## One-line idea

Test whether an agent can inspect an ML codebase, run experiments, interpret
metrics, and improve a baseline under a fixed compute environment.

## Technical core

Thirteen tasks package datasets, code, goals, and evaluation scripts. A ReAct
agent edits and executes experiments, making long-horizon scientific work more
reproducible than free-form research demonstrations.

## Evaluation and limits

Claude v3 averages about 37.5% success in the reported setting; older tasks can
reach 100% while recent tasks fall to zero, suggesting memorization/recency and
planning weaknesses. Thirteen tasks are a small scientific sample and benchmark
success does not establish novel discovery.

## Course placement and decision

**Candidate / Week 10 case or evaluation background.** Good failure evidence,
but primarily a benchmark rather than a reusable mechanism.
