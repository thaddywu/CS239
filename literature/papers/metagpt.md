# MetaGPT: Meta Programming for A Multi-Agent Collaborative Framework

## Decision

**Rejected as a primary reading; retain as a boundary case.** Primary source: [ICLR 2024 proceedings](https://proceedings.iclr.cc/paper_files/paper/2024/hash/6507b115562bb0a305f1958ccc87355a-Abstract-Conference.html).

## What it does

MetaGPT turns software-company standard operating procedures into prompt sequences. Role-labeled agents produce structured intermediate artifacts in an assembly-line workflow. This is a real framework contribution and more structured than unconstrained group chat.

## Why it is not central

The paper's main explanatory variables—human job roles, SOP prompts, and multiple model instances—are entangled. It does not establish that several agents are required instead of a single model executing the same typed workflow, nor does it analyze information propagation, shared-state consistency, or fault containment. The software-generation evaluation emphasizes output scores over repository-grounded maintenance, execution, and controlled ablation of coordination mechanisms.

## Reconsideration condition

Reconsider if a later study reimplements the same SOP as matched single-agent and multi-agent systems, controls token/compute budgets, and measures intermediate-artifact correctness and error propagation. Until then, use a brief excerpt only to teach “multi-agent” as a claim requiring a counterfactual.
