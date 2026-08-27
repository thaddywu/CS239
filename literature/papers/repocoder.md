# RepoCoder: Repository-Level Code Completion Through Iterative Retrieval and Generation

## Metadata

EMNLP 2023. [Primary record](https://aclanthology.org/2023.emnlp-main.151/).

## One-line idea

Alternate repository retrieval and code generation so each draft becomes a
better query for the next context round.

## Technical core

An initial retrieval supplies cross-file context; a generator proposes code;
the draft and surrounding code refine later retrieval. RepoEval provides line-
and API-level completion tasks grounded in repositories.

## Evaluation and limits

Iterative retrieval improves over one-shot and local-context baselines by more
than ten points on reported metrics. Completion is narrower than issue repair,
the loop has no tool side effects or validation, and lexical/embedding relevance
is not architecture recovery.

## Course placement and decision

**Candidate / Week 5 background.** A useful predecessor for repository-context
loops, but not a primary agent paper.
