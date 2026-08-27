# LLMs Can't Plan, But Can Help Planning in LLM-Modulo Frameworks

## Decision

**Strong discussion candidate, not a standalone algorithm paper.** Primary source: [ICML 2024 position-paper record](https://openreview.net/forum?id=Th8JPEmH4z).

## Thesis

The paper disputes the inference that fluent plan text constitutes dependable planning. It proposes an “LLM-Modulo” pattern: models provide approximate knowledge, candidate actions, preferences, or translations; external model-based components check constraints, search for executable plans, and return counterexamples or failures for another iteration.

This is a responsibility allocation argument. Generative components cover open-world knowledge and informal input, while validators and solvers cover closed-world constraints with explicit semantics.

## Evidence and limits

The position synthesizes empirical failures of direct plan generation and examples of verifier/planner-assisted systems. Its value is conceptual breadth rather than a new controlled implementation. “Cannot plan” is deliberately provocative and depends on what counts as planning; models can generate useful plan fragments even when they cannot guarantee executability.

## Course role and comparisons

Use to open a debate around a concrete architecture diagram: model as proposer, formal or programmatic component as critic, and runtime as mediator. LeanDojo, AlphaGeometry, IRIS, CodaMOSA, AgentSpec, and CaMeL instantiate variants of this pattern. LATS is the contrasting model-heavy approach, where the LM also supplies value estimates during search.
