# SWE-agent: Agent-Computer Interfaces Enable Automated Software Engineering

## Decision

**Strong candidate and likely week-one anchor.** Primary source: [NeurIPS 2024 proceedings](https://proceedings.neurips.cc/paper_files/paper/2024/hash/5a7c947568c1b1328ccc5230172e1e7c-Abstract-Conference.html).

## Problem and mechanism

The paper defines the agent-computer interface (ACI) as both the actions exposed to a model and the observations/history returned after actions. SWE-agent supplies concise repository search, bounded file viewing, line-oriented editing, test/shell execution, syntax guardrails, and context-history processing. Failed or malformed actions return targeted feedback; old observations are collapsed to keep the working context current.

Four design principles recur: commands should be simple, meaningful work should require few calls, feedback should be informative but concise, and guardrails should stop error propagation early.

## Evidence

- On the original 2,294-instance SWE-bench, GPT-4 Turbo resolves 12.47%; on SWE-bench Lite it resolves 18%, versus 11% for the shell-only agent.
- A 300-task ablation shows material changes from interface choices: linting improves the editor variant; summarized search beats iterative result-by-result search; a 100-line window beats both 30 lines and a full file; compressed recent history beats full history.
- The interface transfers imperfectly but meaningfully to Claude 3 Opus, suggesting more than model-specific prompt tuning.

## Limits

Interface choices were developed partly by inspecting a small hand-picked development set, and evaluation uses costly closed models. Passing repository tests remains a partial correctness oracle. The paper improves recoverability but does not provide transactionality, policy enforcement, or semantic rollback.

## Course role and comparisons

Read beside Agentless: if a deterministic staged pipeline can match or beat open-ended agents, which ACI capabilities are actually necessary? CodeAct provides the opposite interface philosophy—one powerful language rather than a narrow command set.
