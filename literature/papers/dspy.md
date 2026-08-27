# DSPy: Compiling Declarative Language Model Calls into State-of-the-Art Pipelines

## Metadata

ICLR 2024. [Primary record](https://proceedings.iclr.cc/paper_files/paper/2024/hash/f1cf02ce09757f57c3b93c0db83181e0-Abstract-Conference.html).

## One-line idea

Express LM computations as declarative, parameterized modules and compile them
against a task metric instead of hand-tuning prompt strings.

## Technical core

Programs compose signature-driven modules into text-transformation graphs. A
compiler generates/chooses demonstrations and parameters to optimize the whole
pipeline, including retrieval and agent-loop case studies. The important SE
abstraction is separation of logic, LM invocation, and optimizer.

## Evaluation and limits

Case studies cover math, multi-hop retrieval, complex QA, and agent control;
compiled small-model pipelines can compete with larger manually prompted ones.
Metrics may be incomplete or gameable, compilation consumes data/compute, and
dynamic long-lived state is not the primary concern.

## Course placement and decision

**Candidate / Week 2 optional.** Strong programming-model paper, but broader
than agent runtime and less central than the interface/verifier comparison.
