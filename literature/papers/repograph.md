# RepoGraph: Enhancing AI Software Engineering with Repository-level Code Graph

## Metadata

ICLR 2025. [Primary record](https://proceedings.iclr.cc/paper_files/paper/2025/hash/4a4a3c197deac042461c677219efd36c-Abstract-Conference.html).

## One-line idea

Expose a repository code graph as a plug-in navigation/context layer for coding
systems instead of relying only on text retrieval.

## Technical core

RepoGraph extracts repository-level structural relationships and supplies graph
navigation/retrieval to otherwise different software agents. The representation
helps locate definitions and dependencies beyond a local context window without
requiring each agent to rebuild structure from text.

## Evaluation and limits

The paper reports improvements across four methods on SWE-bench and CrossCodeEval,
supporting portability. Graph quality is language/parser-dependent, edges capture
implemented structure rather than architectural intent, and improved downstream
scores do not isolate every retrieval decision.

## Course placement and decision

**Candidate / Week 5 optional.** Useful competing representation; CodePlan is
stronger because its graph actively creates and updates edit obligations.
