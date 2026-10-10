# CS 239 Reading List v7 — Technical-Depth Audit

This version is the proposed **16-paper teaching list** for Fall 2026. It is
smaller than the v6 research pool and maps one-to-one to the 16 paper-discussion
meetings. The selection rule is mechanism first: a primary paper should expose
an algorithm, abstraction, interface, language, protocol, runtime, verifier, or
decision-relevant negative result that can sustain a technical discussion.

Fifteen readings are mechanism-first. **ImpossibleBench is the only
evaluation-first exception**: its contradictory specification/test construction
makes specification gaming logically observable, which gives the course a
clean negative result that no retained mechanism paper supplies.

## V7 at a Glance

| Week | Course question | Readings |
|---|---|---|
| 1 | What are the ingredients and operational boundaries of an agent? | AgentSquare; SWE-agent |
| 2 | How are multiple agents organized, and how does information move through them? | Evolving Orchestration; Information Propagation |
| 3 | How can coding agents produce executable evidence rather than patches alone? | AutoCodeSherpa; NESA |
| 4 | When do tests lie, and when can untrusted neural help remain checkable? | ImpossibleBench; Gordian |
| 5 | How should learned semantics interact with program and specification analysis? | IRIS; RFCAudit |
| 6 | How are intended meanings elicited and exact proof obligations discharged? | ARTEMIS; LemmaNet |
| 7 | How can agent authority and action traces be constrained outside the model? | ACE; AgentSpec |
| 8 | How do we check coordination and safely evolve persistent user intent? | TraceFix; Semantic Commit |

## Paper-by-Paper Audit

| # | Paper | Main technical object | Depth | Audit verdict and sharpest limitation |
|---:|---|---|---|---|
| 1 | **AgentSquare** | Uniform planning/reasoning/tool/memory modules plus evolutionary architecture search | High | Keep as the staff-led ingredient map. Its ablations validate the search procedure more clearly than the intrinsic value of each module, so teach it as a design-space abstraction rather than a settled architecture. |
| 2 | **SWE-agent** | Agent-computer interface with bounded commands, observations, feedback, and guardrails | High | Keep. The interface is a concrete SE artifact with component evidence; it does not itself solve transactionality, policy, or semantic validation. |
| 3 | **Evolving Orchestration** | RL orchestrator that selects heterogeneous agents and induces a collaboration graph | High | Keep for organization and dynamic allocation. The agents are still mostly reasoning-call tuples, with little durable state, authority, concurrency, or effect semantics. |
| 4 | **Information Propagation** | Counterfactual Agent Propagation Effect and a GNN topology optimizer | High | Promote into the scheduled list. It makes insight and error diffusion causal rather than merely comparing graph scores; its evidence remains benchmark-episode-centric and does not cover authenticated messages or shared state. |
| 5 | **AutoCodeSherpa** | Issue-derived input, infection, and output properties used for localization and patch rejection | Very high | Keep. Executable properties create evidence separate from the final patch, though a mistaken generated property can systematically misdirect both localization and rejection. |
| 6 | **NESA** | Restricted Datalog, parser facts, lazily queried neural relations, and fixed-point evaluation | Very high | Keep. It gives an unusually crisp neural/symbolic boundary; soundness still depends on the model-supplied semantic relations. |
| 7 | **ImpossibleBench** | Automatically constructed specification/test contradictions with unambiguous cheating labels | Medium (exception) | Keep only as a negative-result paper. It reveals reward hacking, access-control, feedback-loop, and monitor failures, but it contributes a diagnostic construction rather than a new correctness mechanism. |
| 8 | **Gordian** | LLM-generated inverse relations, surrogate models, and heap partitions for KLEE/Z3 | Very high | Keep. Generated ghost code may be wrong without entering the trusted result because witnesses are replayed on the original program; incompleteness and solver bias remain. |
| 9 | **IRIS** | Model-generated taint specifications plus CodeQL reachability and contextual triage | Very high | Keep. It sharply separates semantic coverage from exact dataflow propagation, while source/sink and triage judgments remain model-dependent. |
| 10 | **RFCAudit** | Hierarchical RFC index and demand-driven specification-to-code queries | High | Keep, but mark as a fragile slot. Indexing and query ablations are real; the final semantic conformance judgment is still model-owned rather than independently proved. |
| 11 | **ARTEMIS** | Candidate temporal formulas plus low-complexity distinguishing traces for human validation | Very high | Keep. Its balanced trace selection turns ambiguity resolution into a technical query problem, but the guarantee ends at the supported requirements language and the human answer. |
| 12 | **LemmaNet** | Source-aware lemma synthesis, proof-state adaptation, Frama-C obligations, and Rocq checking | Very high | Keep. It is a genuine agent/verifier system with exact acceptance; accepted-in-press status and the cost/coverage limits require a pre-quarter proceedings recheck. |
| 13 | **ACE** | Trusted abstract plans, app-specific concrete plans, static lattice IFC, and isolated capability execution | Very high | Promote over CaMeL. It provides an end-to-end security architecture; its guarantee relies on ahead-of-time restricted plans, trusted schemas/matching, isolation, and the enforcement runtime. |
| 14 | **AgentSpec** | Stateful policy DSL and external reference monitor over agent events/actions | Very high | Keep. It supports discussion of complete mediation and temporal policy state; enforcement cannot compensate for omitted events, a wrong policy, or harmful behavior that the policy permits. |
| 15 | **TraceFix** | Coordination topology IR, PlusCal/TLA+/TLC counterexamples, iterative repair, and runtime monitoring | Very high | Move from multi-agent architecture to correctness/runtime assurance. The model check is bounded, and the runtime monitor enforces topology rather than the full verified state machine—precisely the model-to-runtime gap worth discussing. |
| 16 | **Semantic Commit** | Knowledge-graph impact analysis, conflict detection, scoped resolution, and mixed-initiative review | High | Keep as the mechanism-bearing SE+HCI paper. Its small study and lack of temporal/provenance/concurrency semantics limit generality, but the impact-analysis pipeline is deeper than an approval-interface study. |

## Changes from the Scheduled v6 Draft

- **Information Propagation replaces TraceFix in Week 2.** This keeps the
  multi-agent week about architecture and communication ingredients.
- **TraceFix moves to Week 8 correctness/runtime assurance.** Its core is a
  checked and monitored coordination protocol, not an architecture taxonomy.
- **ACE replaces CaMeL as the primary secure-architecture paper.** CaMeL remains
  a technically excellent first alternate; ACE gives the cleaner full path from
  trusted intent structure to static checking and isolated execution.
- **Semantic Commit becomes the sole primary HCI/intent paper.**
  Plan-Then-Execute becomes supporting evidence because its main contribution is
  a user study rather than a new correctness mechanism.
- **Agentix and LeanDojo remain strong alternates.** Both are deep, but the
  16-meeting list cannot add a serving week or a second theorem-proving meeting.

## Publication Rechecks Before the Quarter

Recheck final proceedings for AutoCodeSherpa, Gordian, and LemmaNet. PSearch is
an especially relevant watch-list paper because its MCTS patch-search state may
be a stronger repair mechanism, but it was not promoted without a full paper
and auditable ablations.
