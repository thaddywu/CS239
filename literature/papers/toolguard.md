# Towards Enforcing Company Policy Adherence in Agentic Workflows (ToolGuard)

## Decision

**Published candidate/background, not a primary replacement.** EMNLP 2025
Industry Track.

## Mechanism and evidence

ToolGuard maps fragments of a company policy document to mutating tools,
generates executable guard code offline, tests the code syntactically and with
unit tests, and runs the guards before tool invocation. It is deterministic at
runtime and offers a concrete compiler-versus-monitor decomposition.

The evaluation uses the tau-bench Airlines domain with 14 tools. It is useful
evidence that compiling prose policies into code remains difficult, but the
paper itself describes the results as preliminary.

## Limits and course role

Only pre-invocation violations are observable: the framework cannot detect a
required action that the agent omits. It is evaluated on one domain with concise
policies and a limited tool set. AgentSpec offers a more general state/history
policy language and stronger multi-domain evaluation, so ToolGuard works better
as an enterprise-policy case study than another assigned paper.
