# Toolformer: Language Models Can Teach Themselves to Use Tools

## Decision

**Strong candidate.** Primary source: [NeurIPS 2023 proceedings](https://proceedings.neurips.cc/paper_files/paper/2023/hash/d842425e4bf79ba039352da0f658a906-Abstract-Conference.html).

## Problem and mechanism

Tool use is treated as a learning problem: decide whether to call an API, which API to call, its arguments, and how to incorporate the returned text. A pretrained LM samples candidate calls inside ordinary text. Calls are executed, and a filtering rule retains examples only when access to the returned result sufficiently lowers the loss of predicting later tokens. Fine-tuning on these self-labeled examples teaches the model to insert calls without changing the base architecture.

The paper covers a small fixed tool set (calculator, calendar, search, question answering, and translation). The important abstraction is not the tools themselves but the loss-based selection of useful call sites.

## Evidence and limits

- The 6.7B-parameter model improves zero/few-shot results across several downstream tasks and can retain general language-model behavior.
- Filtering and tool-specific thresholds are technically consequential; this is more than prompting an API schema.
- Execution is essentially atomic and tools are trusted. Long-horizon state, recovery, permissions, and adversarial outputs are outside scope.
- Tool definitions and demonstrations still encode substantial human design. Self-supervision does not imply open-ended tool discovery.

## Course role and comparisons

Use as the learned-tool-use pole against ReAct's prompting and CodeAct's runtime/action-space design. It supports the question: should responsibility for a call live in model weights, a compiler/runtime, or an external policy? Pair with CaMeL to reveal that learning *when* to call says nothing about whether a call is authorized.
