# Agents for Program Analysis

## Scope and responsibility split

The productive question is not whether an LLM “understands code.” It is where a
probabilistic semantic guess enters a program-analysis pipeline and which claims
remain checkable afterward.

## Mechanism map

### Model supplies specifications; analysis supplies reachability

[IRIS](../literature/papers/iris.md) extracts repository APIs, asks a model for
CWE-specific source/sink roles, compiles them into CodeQL, computes whole-program
taint paths, and uses contextual model reasoning to triage alerts. The two model
stages improve recall and usability; the static engine supplies interprocedural
evidence.

### Model supplies scenarios; analysis confirms relations

[GPTScan](../literature/papers/gptscan.md) maps smart-contract code to
logic-vulnerability scenarios and properties, then validates the necessary
control/data relationships. It is narrower than IRIS but its false-positive
reduction is a clear neuro-symbolic result.

### Analysis guides an acting repair system

AutoCodeRover uses spectrum-based fault localization to prioritize repository
context. CodePlan uses dependencies and change-may-impact relations to generate
future edit obligations. Here analysis changes *where the agent acts*, rather
than only classifying code.

### Models enable analysis execution

SelfPiCo predicts values/types for missing dependencies so partial Python code
can execute. This is a technically interesting dynamic-analysis use, though its
“agent” character is weaker and its course fit narrower.

## Reading decisions

**Strong:** IRIS; GPTScan. Cross-list AutoCodeRover or CodePlan depending on the
week's focus.

**Other candidate:** SelfPiCo.

**Weaker alternatives:** method-level vulnerability classifiers with no
repository analysis or executable confirmation. They use code as text and do
not address the program-analysis question.

## Current assessment

- Literature maturity: **medium**. Security analysis supplies two strong cases;
  general agent–analysis interfaces remain sparse.
- Technical depth: very high for IRIS; high for GPTScan and CodePlan.
- Course suitability: high as a “neuro-symbolic software engineering” week,
  but probably too narrow as “agents for program analysis” alone.

## Gaps and next searches

- Explicit soundness/unsoundness contracts for model-inferred specifications.
- Incremental analyses that update after agent edits and explain invalidation.
- Agents that choose among analyses based on cost and uncertainty.
- Static-analysis false-negative studies, not only false-positive reduction.
- Transfer beyond security: types, concurrency, resource leaks, performance, and
  architecture conformance.
