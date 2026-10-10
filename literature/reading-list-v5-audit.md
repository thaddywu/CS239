# Reading-list v5 audit

Date: 2026-08-27. This pass re-opened every v4 primary, then searched the
identified gaps rather than restarting the survey. A paper survived only when
its main contribution remained interesting with the LLM treated as an oracle or
proposal generator. Final count: **19 primary papers; 11 retained, 8 added, and
8 removed from v4 primary status**.

## Major changes from v4

- Replaced the diffuse software-understanding block with **Program Analysis and
  Structured Reasoning**. NESA, Gordian, HoarePrompt, and IRIS now expose four
  distinct boundaries: relational fixed points, solver-aiding transformations,
  program-logic-shaped language reasoning, and model-completed taint analysis.
- Reduced three multi-agent topology/fault papers to one causal-topology paper
  plus LAS's dynamic workflow scheduler. Agentix separately adds whole-program
  serving and critical-path scheduling.
- Retained Agentless as the repair-autonomy control, but replaced AutoCodeRover
  and CodaMOSA with AutoCodeSherpa's executable issue explanations and patch
  rejection. ImpossibleBench remains the adversarial oracle-quality reading.
- Replaced Move-specific MSG with ARTEMIS's requirements-to-LTL pipeline and
  logarithmic distinguishing-trace interaction. RFCAudit adds a different
  conformance problem: connecting long normative documents to repository code.
- Retained only one theorem-proving primary, LeanDojo. Draft--Sketch--Prove
  remains strong background; HoarePrompt earns the second program-logic slot by
  making the formal-versus-structured-natural-language boundary debatable in a
  software-correctness setting.
- Moved Sagas out of the primary set. Semantic compensation remains required
  instructor context, but the audit did not find a modern peer-reviewed
  agent-native replacement worthy of a full assignment. The absence is recorded
  as a gap rather than filled with an old paper or a 2026 preprint.

## Re-audit of every v4 primary

| v4 paper | v5 outcome | Decision rationale |
|---|---|---|
| SWE-agent | Retain | Still the strongest ablatable demonstration that the agent-computer interface changes outcomes. |
| CodeAct | Retain | Its executable action language remains the clean opposite design to a constrained interface. |
| Information Propagation Topologies | Retain | The causal intervention and learned sparse topology are more explanatory than benchmark-only topology comparisons. |
| CARD | Move to candidate | Condition-aware graph generation is deep, but overlaps the retained topology lesson and says little about task allocation or shared state. |
| Multi-Agent Resilience | Move to strong candidate | Controlled fault injection is excellent evidence; Challenger/Inspector are weaker as independent containment mechanisms, and LAS adds a missing scheduler. |
| CodePlan | Move to strong candidate | The evolving change-obligation DAG remains valuable, but no longer fits a separate generic understanding block and is less semantic than the new analysis papers. |
| IRIS | Retain | CodeQL-owned reachability plus model-generated taint specifications remains a uniquely clear symbolic/probabilistic division. |
| AutoCodeRover | Move to strong candidate | Strong AST-aware repair agent, but overlaps Agentless's repair question; AutoCodeSherpa adds an independent executable validation artifact. |
| Agentless | Retain | The fixed-pipeline control remains essential to evaluating whether autonomy is actually necessary. |
| CodaMOSA | Move to strong candidate | The stagnation-triggered search/model handoff is exemplary, but AutoCodeSherpa provides the more current and course-distinct issue-to-property mechanism. |
| ImpossibleBench | Retain | Its impossible specifications make test exploitation observable and challenge every validation paper in the list. |
| Agentic Specification Generator | Move to strong candidate | Clause specialists and Move Prover feedback are deep; ARTEMIS is broader and makes semantic human validation algorithmic. |
| LeanDojo | Retain | The exact environment, traced premises, kernel feedback, and novel-premise split remain unmatched as a course reference point. |
| Draft, Sketch, and Prove | Move to strong candidate | Still excellent decomposition, but LeanDojo covers exact proving and HoarePrompt creates a more software-specific correctness tension. |
| Sagas | Move to strong candidate/background | Exceptionally relevant compensation semantics, but the original is 1987 and the requested recency rule is decisive. |
| CaMeL | Retain | Provenance, capability flow, and trusted-control separation remain a distinct construction-based security model. |
| AgentSpec | Retain | The policy DSL and external action monitor remain the strongest general runtime-enforcement lesson. |
| SAGA | Retain | Its provider trust is substantial, but cryptographic inter-agent identity and delegation are not supplied by CaMeL or AgentSpec. |
| Plan-Then-Execute | Retain | The 2x2 study provides rare modern negative evidence about planning/execution involvement, workload, and trust. |

## Technical audit of selected papers

| Paper | Main mechanism | Technical depth | Unique lesson | Closest overlap | Keep confidence |
|---|---|---|---|---|---|
| SWE-agent | Bounded ACI with specialized commands, observation formatting, feedback, and guardrails | High | Interface affordances are part of the algorithm and can be ablated | CodeAct | Very high |
| Executable Code Actions | Persistent executable Python action language | High | Expressive composition and state can replace a large fixed tool vocabulary, at a confinement cost | SWE-agent | Very high |
| Agentix | PLAS attained-service scheduling and ATLAS distributed critical-path scheduling | Very high | Serve an agent as a dependency-bearing program, not a bag of requests | LAS; Murakkab | Very high |
| Information Propagation Topologies | CAPE causal interventions plus EIB-Learner sparse graph search | High | Topology determines both useful information and error diffusion | CARD; Multi-Agent Resilience | Very high |
| LLM-as-Scheduler | Cheap gate plus LLM routing over exit/test/refine/reroute decisions | High | Dynamic orchestration is an accuracy/cost control problem beyond message topology | Agentix; CARD | High |
| Agentless | Fixed localization, repair, and validation pipeline | High | Open-ended autonomy needs a strong structured-pipeline control | AutoCodeRover | Very high |
| AutoCodeSherpa | Executable input/infection/output conditions as PBTs and internal formulas | Very high | A symbolic explanation can localize and reject patches independently of a repair agent | CodaMOSA; MSG | High |
| ImpossibleBench | Deliberately inconsistent test/specification tasks | High | Passing tests can be direct evidence of gaming rather than correctness | AutoCodeSherpa | Very high |
| NESA | Restricted Datalog policies over symbolic and lazy neural relations | Very high | A fixed-point relational engine can constrain where model semantics enter static analysis | IRIS; LogicLoc | Very high |
| Gordian | LLM-generated inverse, surrogate, and heap-partition ghost code for KLEE/Z3 | Very high | Let the model repair solver representations while exact execution rechecks witnesses | NESA; HoarePrompt | Very high |
| HoarePrompt | Natural-language strongest postconditions and k-induction | High | PL-shaped structure improves reasoning but is not itself a proof; the gap is measurable | Gordian; LeanDojo | High |
| IRIS | Model-inferred taint specifications compiled into CodeQL plus path triage | Very high | Probabilistic semantic proposal and symbolic reachability can have separate owners | NESA; ACTaint | Very high |
| ARTEMIS | Structured-NL/LTL translation plus balanced distinguishing traces | Very high | Human semantic validation can be posed as efficient candidate discrimination | MSG; PAT-Agent | Very high |
| RFCAudit | Hierarchical semantic index and demand-driven code queries per RFC property | High | Long-document/software conformance requires explicit repository state and retrieval protocols | IRIS; CodePlan | High |
| LeanDojo | Traced Lean environment, premise retrieval, tactic execution, and kernel checking | Very high | Exact state and an independent checker change both agent design and evaluation | Draft--Sketch--Prove | Very high |
| CaMeL | Trusted/untrusted control separation with provenance-aware capabilities | Very high | Prompt injection is an information-flow/confused-deputy problem, not a string filter | AgentSpec; ACE | Very high |
| AgentSpec | Stateful policy DSL and external reference monitor | Very high | Safety policy can be independently enforced at the action boundary | CaMeL; ProbGuard | Very high |
| SAGA | Provider registry and cryptographic authorization/delegation tokens | Very high | Multi-agent identity and delegated authority need protocol semantics | CaMeL; AgentSpec | High |
| Plan-Then-Execute | Factorial study of planning versus execution involvement | High | Human review can help, harm, or fail to calibrate trust; more oversight is not monotonic | Adjustable Autonomy | Very high |

## Strong new discoveries

- **NESA (FSE 2026)** is the Datalog-style work sought by the prompt. Restricted
  policies, fixed-point execution, lazy semantic relations, and ablations make
  it substantially more than “LLM plus static-analysis tool.”
- **Gordian (ISSTA 2026)** found an unusually clean hybrid boundary: the model
  creates solver-aiding ghost code; KLEE/Z3 retain global reasoning; candidate
  witnesses are rechecked on original code.
- **AutoCodeSherpa (ISSTA 2026)** turns issue explanations into executable
  properties and formulas, then demonstrates independent patch rejection and
  downstream Agentless improvements.
- **ARTEMIS (ICSE 2026)** combines formalization with a non-trivial human-query
  algorithm; balanced distinguishing traces attack intent fidelity rather than
  merely checking LTL syntax.
- **Agentix (NSDI 2026)** and **LLM-as-Scheduler (ACL 2026)** fill two different
  runtime gaps: scheduling whole dependency-bearing agent programs and routing
  semantic workflow stages.
- **RFCAudit (ASE 2025)** is the best inspected expansion beyond conventional
  repair: a persistent semantic index and demand-driven query interface connect
  RFC properties to large implementations, with meaningful ablations.

## Serious challengers inspected but not selected

| Paper | Status | Why it does not change the final 19 |
|---|---|---|
| LogicLoc / Neurosymbolic Repository-Level Code Localization | Candidate, preprint | LLM-synthesized Datalog and mutation feedback are promising, but NESA is published, more general, and more disciplined. |
| PAGENT | Candidate, ISSTA 2026 accepted in press | Static analysis guides exploit generation, but the task and mechanism are narrower than Gordian and AutoCodeSherpa. |
| ProbGuard | Strong candidate, ASE 2026 accepted in press | Predicate abstraction, learned DTMCs, and CTL prediction are deep; the small evaluation falls below its own practical PAC conditions. |
| LemmaNet | Strong candidate, ASE 2026 accepted in press | Offline lemma discovery plus online proof-state adaptation is the strongest near-term challenger; recheck the final paper before freeze. |
| Event-B Agent | Candidate, FSE 2026 | Relevant formal-model synthesis/repair, but inspected evidence did not displace ARTEMIS or LeanDojo. |
| ACTaint | Candidate, ASE 2025 | Meaningful taint specialization, but IRIS has the clearer symbolic-reachability boundary and broader lesson. |
| Semia | Candidate, preprint | Constraint-guided lifting of agent skills into Datalog is exact-fit, but publication and faithful-representation evidence are not mature enough. |
| Deductive Steering | Candidate, ISSTA 2026 accepted in press | SMT consequence checks steer fault localization, synthesis, and invariant reasoning, but only abstract-level evidence was available; encoding failures and ablations could not be audited. |
| AMA | Rejected as primary | Memory roles add lifecycle operations, not defined shared-state consistency, concurrency, or isolation. |
| H-MAS | Rejected as primary | A real serving scheduler, but “agents” are controller roles rather than the LLM-agent programs the course studies. |

Other screened directions included model-serving schedulers, Datalog workflow
applications outside software engineering, conventional performance/configuration
agents, LLM-guided query optimization, and prompt-heavy architecture recovery.
None provided a stronger mechanism/evidence pair than the selected readings.

## Remaining literature gaps

1. **External side effects and transactions.** No peer-reviewed modern agent
   runtime integrates durable intent logs, idempotency, semantic compensation,
   isolation, and recovery across heterogeneous tools. Sagas and Beldi remain
   background; Cordon, ACRFence, and Agentic Transaction remain preprints.
2. **Approval and authority at commit time.** Plan-Then-Execute measures review,
   but does not bind approval to an exact action, world-state version, authority
   epoch, or expiration condition. The exact-fit commit-time work is preprint-only.
3. **Concurrent shared state.** The multi-agent literature studies graphs,
   debate, roles, and fault propagation far more often than consistency,
   synchronization, conflict resolution, or transactional memory.
4. **Soundness of model-derived semantic facts.** NESA, IRIS, RFCAudit, and
   ARTEMIS all expose productive symbolic/model boundaries, but none can prove
   that the model supplied the complete intended facts or property.
5. **Agentic program synthesis.** Deductive Steering is the strongest newly
   found solver-guided candidate across synthesis and invariant generation, but
   only abstract-level accepted-in-press evidence was auditable. No paper cleared
   the primary bar for a fully inspected CEGIS/SMT/grammar-guided agent loop.
6. **Other thin but potentially valuable Agentic SE areas.** Database/query
   reasoning, configuration and deployment repair, performance diagnosis,
   dependency evolution, and modern architecture recovery did not yield a
   primary paper at this bar. These remain search routes, not forced weeks.

## Freeze recommendation

Treat the 19-paper list as stable enough to schedule. Before the actual syllabus
freeze, recheck only accepted-in-press AutoCodeSherpa, Gordian, ProbGuard,
LemmaNet, and Deductive Steering for final proceedings/artifacts. A changed version, new soundness
result, or substantially stronger evaluation would justify reopening a slot;
recency or benchmark rank alone would not.
