# SWE-bench: Can Language Models Resolve Real-World GitHub Issues?

## Metadata

ICLR 2024. [Primary record](https://proceedings.iclr.cc/paper_files/paper/2024/hash/edac78c3e300629acfe6cbe9ca88fb84-Abstract-Conference.html).

## One-line idea

Evaluate issue resolution by applying a generated patch to a real repository
snapshot and executing the issue's tests.

## Technical core

The benchmark pairs 2,294 GitHub issues from 12 Python repositories with code
snapshots and executable tests, requiring repository localization and multi-file
reasoning. It turns software maintenance into an environment-level task rather
than function completion.

## Evaluation and limits

Initial retrieval-and-generation baselines perform poorly, motivating agents.
Later use exposed contamination, infrastructure, flaky-test, and test-adequacy
concerns; benchmark variants are not directly interchangeable. A passing patch
can still violate intent.

## Course placement and decision

**Candidate / Week 3 background.** Essential field context, but a benchmark is
not the technical mechanism the seminar should center.
