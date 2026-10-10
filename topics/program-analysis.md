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

### Analysis validates generated specifications and structures

- [Agentic Specification Generator](../literature/papers/agentic-specification-generator.md)
  selectively inlines callees and invokes Move Prover while generating clauses.
- [PropertyGPT](../literature/papers/propertygpt.md) uses compiler/static-analysis
  diagnostics to repair formal properties before a dedicated prover checks them.
- [SemRef](../literature/papers/semref.md) uses dependency analysis to constrain
  semantic refinement of recovered module structures.

## Reading decisions

**Strong:** IRIS; GPTScan. Cross-list AutoCodeRover, CodePlan, or Agentic
Specification Generator depending on the week's focus.

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

## Due diligence audit — 2026-08-27

### Previously believed

IRIS and GPTScan formed a strong security-centered neuro-symbolic pair, but the
cluster was narrow outside vulnerability analysis and lacked explicit contracts
for LLM-induced unsoundness.

### New papers checked

- Fully inspected Agentic Specification Generator, PropertyGPT, and SemRef for
  the points where static/dependency analysis changes an agent decision.
- Checked AROP (ICSE 2026), Amur (ASE 2025), CausalRepair (ISSTA 2026), and
  recent resource-flow/slicing work; none supplied a more general analysis-agent
  contract than the current primaries.
- Rechecked program-analysis and verification sessions in ICSE, FSE, ASE, ISSTA,
  PLDI, POPL, OOPSLA, CAV, TACAS, and FM programs.

### Important additions

Agentic Specification Generator is the most important cross-listing: specialized
generation is constrained by inlining and prover feedback; **very high technical
depth**. PropertyGPT and SemRef broaden the validator roles but remain domain
specific.

### Stronger replacements

No stronger peer-reviewed alternative found in this audit for IRIS's repository-
scale taint-specification split or GPTScan's scenario-plus-analysis pipeline.

### Judgment

**UPHELD.**

### Why

The new papers broaden program analysis into specification and architecture
artifacts, but they reinforce rather than overturn the core responsibility split:
the model proposes semantic facts and deterministic analysis checks a narrower
relation. The topic supports a merged neuro-symbolic week, not a broad standalone
survey of every analysis family.

## Final-selection v3 update — 2026-08-27

IRIS, CodePlan, Software Reflexion Models, and MSG all enter the final 20, but
each analysis has a different semantic contract: taint reachability, edit impact,
architecture discrepancy, and selective inlining for contract generation. This
is sufficient breadth for program analysis to remain a cross-theme spine rather
than a separate survey block.

## Reading-list v5 update — 2026-08-27

The earlier “merged spine” judgment is strengthened into a dedicated mechanism
block:

- [NESA](../literature/papers/nesa.md): restricted Datalog fixed points over
  parser and neural relations;
- [Gordian](../literature/papers/gordian.md): solver-aiding ghost code with
  KLEE/Z3 and original-program witness checks;
- [HoarePrompt](../literature/papers/hoareprompt.md): natural-language strongest
  postconditions and k-induction without a formal guarantee;
- [IRIS](../literature/papers/iris.md): model-generated taint specifications
  with CodeQL-owned reachability;
- [RFCAudit](../literature/papers/rfcaudit.md): hierarchical semantic indexing
  and demand-driven conformance queries.

[LogicLoc](../literature/papers/logicloc.md), [ACTaint](../literature/papers/actaint.md),
[Semia](../literature/papers/semia.md), and [Deductive Steering](../literature/papers/deductive-steering.md)
are recorded challengers. Deductive Steering is the closest program-synthesis/
invariant-generation result, but only abstract-level evidence was available.
The common
unresolved question is whether omitted or hallucinated neural facts can be
detected independently; deterministic downstream execution alone does not give
semantic completeness.

## Final adversarial review — 2026-08-28

HoarePrompt is no longer primary. Full inspection showed prompted CFG state
summaries, three loop unrolls followed by model generalization, and a model-owned
final entailment classification—not sound strongest-postcondition transfer or
k-induction. [LemmaNet](../literature/papers/lemmanet.md) takes the slot because
source-level understanding produces helper lemmas that must be proved and then
used to discharge the original Frama-C VC in Rocq.

The retained analysis spine is NESA → Gordian/IRIS → RFCAudit, with LemmaNet
cross-listed as the exact-verification endpoint. LogicLoc, ACTaint, Semia, and
Deductive Steering remain explicit challengers, not silent deletions.
