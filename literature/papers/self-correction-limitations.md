# Large Language Models Cannot Self-Correct Reasoning Yet

## Decision

**Strong negative-result candidate.** Primary source: [ICLR 2024 proceedings](https://proceedings.iclr.cc/paper_files/paper/2024/hash/8b4add8b0aa8749d80a34ca5d941c355-Abstract-Conference.html).

## Question and result

The paper separates intrinsic self-correction—revising without new external information—from correction using oracle feedback, labels, execution, or tools. Across reasoning tasks, generic instructions to recheck frequently reduce accuracy. Models struggle to distinguish a correct initial answer from an incorrect one and can be persuaded away from correct work.

It also controls for sampling in multi-agent debate: under comparable response budgets, apparent debate gains can be no better than self-consistency/majority aggregation. Interaction should not receive causal credit when independent samples explain the result.

## Limits

The conclusion is about the evaluated models and prompting regimes, not an impossibility theorem. Stronger later models, trained verifiers, calibrated uncertainty, or structured environments can change the result. “Cannot” should be taught as an empirical warning, not a timeless fact.

## Course role

This is the conceptual hinge of the reliability week. Compare Reflexion's verbal memory, CRITIC's external tools, theorem-prover feedback, and AgentSpec's independent runtime rules. Ask students to label the new information introduced at every claimed recovery step.
