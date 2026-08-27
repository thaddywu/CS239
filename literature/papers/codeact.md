# Executable Code Actions Elicit Better LLM Agents

## Decision

**Selected for the final 20-paper-day list.** Primary source: [ICML 2024 / PMLR](https://proceedings.mlr.press/v235/wang24h.html).

## Problem and mechanism

Text or JSON tool calls fragment the action space and make multi-tool composition awkward. CodeAct instead makes executable Python the common action language. The interpreter preserves variables and library state, returns actual errors and outputs, and permits the model to revise its next action after each observation. Natural-language turns remain available for user interaction.

The paper also builds CodeActInstruct, roughly 7,000 multi-turn trajectories, and fine-tunes open models for this interaction style. This separates two claims: code is a better interface for already capable models, and training on code-action traces can make smaller models better agents.

## Evidence and limits

- Seventeen models are compared on API-Bank and a new multi-turn benchmark; code actions improve success by as much as 20 percentage points over common alternatives.
- Actual interpreter feedback gives a credible self-debug loop and makes composed actions inspectable.
- Arbitrary code is expressive but dramatically enlarges the security boundary. Sandboxing, authority, side effects, and rollback are assumed rather than solved.
- Benchmarks favor tasks naturally expressible in Python; gains may not transfer to GUI, physical, or transaction-heavy environments.

## Course role and comparisons

Pair with SWE-agent. CodeAct argues for a general, compositional action language; SWE-agent argues for small, LM-specific commands and guardrails. The tension is productive: expressiveness reduces orchestration friction but increases validation and confinement obligations.
