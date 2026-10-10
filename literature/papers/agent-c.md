# Enforcing Temporal Constraints for LLM Agents (Agent-C)

## Decision

**Strong preprint challenger to AgentSpec.** Current source is
[arXiv 2512.23738](https://arxiv.org/abs/2512.23738).

## Mechanism

Agent-C expresses temporal, argument, prior-output, and tool-state constraints
in a DSL, translates finite traces and policies into first-order formulas, and
uses incremental Z3 checks during tool-call generation. Open models use
grammar-constrained backtracking to find a compliant alternative; closed models
fall back to rejection and reprompting. The paper proves trace-conformance
soundness relative to the formal specification and observed tool state.

## Evidence

On benign tau-bench retail/airline tasks plus 34 manually constructed
adversarial tasks, Agent-C reports 100% conformance and zero harm across Qwen3,
Claude Sonnet 4.5, and GPT-5. It compares directly with AgentSpec, DynaGuard,
and unrestricted agents; constrained generation improves utility and token use
over whole-call reprompting.

## Limits

The guarantee is only as complete as the manually encoded policy, tool-state
interface, and visible trace. The adversarial set is small and author-created;
the evaluated domains share tau-bench's policy style. Fine-grained constrained
generation also requires model-logit access, unavailable for closed APIs.

## Course role

If published, Agent-C is a serious replacement-or-pairing decision for
AgentSpec: it adds explicit sequence semantics, a formal guarantee, and
constructive constrained generation rather than only intercept-and-fallback.
