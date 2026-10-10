# Final Selection v3 Audit

## Result

The canonical index and [reading-list-v3](../syllabus/reading-list-v3.md)
contain exactly 20 selected primary papers. The allocation is 4 interface/
runtime/multi-agent papers, 5 coding/repository/program-analysis/architecture-
recovery papers, 5 testing/specification/formal-methods papers, and 6 broad
correctness papers. This 4–5–5–6 shape intentionally gives correctness one more
slot than the approximate target because stateful external effects, human control,
and delegated authority were the largest weaknesses in the prior draft.

All 20 are final peer-reviewed conference or journal papers; no preprint or
accepted-in-press item occupies a primary slot. Exact titles, author order,
venue/year, status, and publication-time affiliations were checked against
official proceedings, publisher/author records, or the paper PDF. Cordon and
Revisable by Design were fully inspected but kept out specifically because their
current records are preprints.

## A. Removed from the previous 20

| Removed paper | Reason removed | Replacement | Lesson preserved or improved |
|---|---|---|---|
| Understanding the Information Propagation Effects of Communication Topologies in LLM-based Multi-Agent Systems | CAPE is technically strong, but a two-paper topology block was less important than the missing correctness mechanisms. The instructor-preference search also found no reason to keep two Chinese-university-heavy multi-agent primaries. | Sagas | Multi-Agent Resilience preserves the architecture/fault-propagation discussion; Sagas adds the previously absent problem of faults after committed effects. |
| PropertyGPT | Strong reusable-property pipeline, but overlaps MSG in domain, prover feedback, and generated smart-contract properties. MSG provides clearer clause-specialized roles, selective inlining, and stronger architecture ablations. | Agentic Specification Generator for Move Programs | Formal properties remain primary, with a sharper program-analysis and specialization mechanism. |
| PAT-Agent | Strong planning/CSP#/counterexample loop, but evaluation is small and DSP supplies a more legible intermediate artifact and better-established theorem-proving evidence. Verified affiliations are NUS, Griffith, and Auckland, so removal is not based on a Chinese-university classification. | Draft, Sketch, and Prove | Neural/formal decomposition and exact checking remain, while formal holes make responsibility boundaries easier to analyze. |
| Agentic Memory / AgeMem | Explicit learned memory actions clear the technical bar, but memory is architectural state rather than a two-day destination. Its benchmark rewards do not cover provenance, transactions, authority, or invalidation in deployment. | Fault-tolerant and transactional stateful serverless workflows | Persistent-state management is upgraded from learned store/delete policy to logged effects, exactly-once replay, and transactional isolation. AgeMem remains tutorial background. |
| How Memory Management Impacts LLM Agents | Valuable negative evidence on contamination and evaluator-dependent deletion, but it overlaps the memory tutorial and does not supply the missing recovery or authority mechanism. Its verified affiliations are U.S. universities, not Chinese universities. | Towards Adjustable Autonomy for the Real World | The correctness unit gains a concrete human-control and escalation policy. Memory contamination remains a cross-cutting failure case and explicit literature gap. |
| Microreboot—A Technique for Cheap Recovery | Fine-grained restart is still valuable, but it does not define exactly-once state updates, isolation, or semantic repair of already committed external effects. | Sagas and Beldi | The replacement pair separates semantic compensation in the open world from transactional replay inside a mediated boundary. Microreboot remains systems background. |
| Solving olympiad geometry without human demonstrations | The learned-proposer/symbolic-closure mechanism is excellent, but the application no longer beats central software-analysis, formalization, or correctness gaps for one of 20 days. | Software Reflexion Models | A neuro-symbolic application gives way to a software-specific architecture-recovery abstraction. Science/frontier exposure remains in the separate student activity. |

None of these papers is reclassified as technically weak. They are
`strong_candidate` rather than rejected because the change is a scarce-slot
decision.

## B. Added papers

| Added paper | Gap filled | Clever technical idea | Why it beats the previous alternative |
|---|---|---|---|
| Software Reflexion Models: Bridging the Gap Between Source and High-Level Models | Architecture recovery and reverse engineering | Map source entities to a hypothesized high-level model, lift source relations, and compute convergence, divergence, and absence for iterative hypothesis repair. | RepoGraph and SemRef offer useful representations/refinement, but the reflexion model makes intended architecture and discrepancy semantics explicit. It replaces AlphaGeometry's application slot with a central SE abstraction. |
| Agentic Specification Generator for Move Programs | Software contracts and invariant generation | Clause-specialized generators plus selective function inlining and Move Prover feedback; ablations compare the specialization and feedback mechanisms. | It preserves PropertyGPT's reusable formal-artifact lesson with a clearer architecture and cleaner all-in-one comparison. |
| Draft, Sketch, and Prove | Proof decomposition and synthesis | Compile an informal global proof into a formal sketch whose holes are independently discharged by an off-the-shelf prover. | It is less toolchain-specific than PAT-Agent and creates an unusually clear contract between uncertain reasoning and exact proof search. |
| Sagas | External side effects, action ordering, compensation, forward recovery | Decompose long-lived work into committed transactions with semantic compensators and explicit backward/forward recovery; compensations respect intervening state rather than pretending to restore bytes. | It addresses partially irreversible workflows more directly than Microreboot and exposes when rollback is impossible. |
| Fault-tolerant and transactional stateful serverless workflows | Persistent state, retries, exactly-once effects, isolation | Atomic intent logging, DAAL, invocation identifiers, replay, and a distributed transaction protocol adapted to function-owned state. | It replaces restart boundaries with a stronger state/effect model inside a controlled workflow boundary. |
| Towards Adjustable Autonomy for the Real World | Human oversight and control transfer | Conditional control-transfer strategies plus coordination-changing actions, selected by an MDP over decision quality, response probability, wait cost, and miscoordination. | It fills a missing HCI mechanism; “ask the human” becomes a planned action with costs and failure modes rather than a generic recommendation. |
| SAGA: A Security Architecture for Governing AI Agentic Systems | Identity, authorization, delegation, lifecycle governance | Provider-mediated registry and cryptographically derived access-control tokens with formal protocol analysis. | It adds a correctness dimension not provided by a second topology paper or by CaMeL/AgentSpec: who authorized inter-agent contact and delegation. |

## C. Downgraded to tutorial, background, or optional reading

- **MCP, A2A, Strands, and general harness demonstrations:** instructor tutorial
  material. They define useful ecosystem vocabulary but no single primary paper
  in the corpus clears the independent technical-mechanism bar.
- **ReAct and Reflexion:** historical vocabulary for observation/action and
  verbal feedback. Their prompt-level loops do not displace interface, analysis,
  transaction, or enforcement papers.
- **Toolformer and LLM-Modulo Planning:** strong background. Toolformer teaches
  learned call placement; LLM-Modulo supplies a useful thesis, but neither beats
  the selected systems papers for a complete seminar day.
- **AgeMem and Memory Management Impacts:** required architecture/correctness
  background, not a standalone primary block. They motivate explicit state,
  provenance, invalidation, and evaluator questions used throughout the course.
- **Microreboot:** short systems bridge for restart units and durable-state
  separation; Sagas and Beldi now carry the primary recovery argument.
- **PropertyGPT and PAT-Agent:** strong optional formal readings whose central
  lessons are represented by MSG and DSP with less redundancy.
- **AlphaGeometry, ChemCrow, Coscientist, ChatEDA, and other science/hardware
  applications:** student frontier-scan material unless a future version adds a
  central software mechanism not taught elsewhere.
- **SWE-bench, AgentDojo, and framework/platform papers such as OpenHands:**
  evaluation or implementation context, not primary mechanisms in this set.

## D. Instructor-preference audit

The preference was applied only after technical depth, distinctiveness, and
course fit. Affiliations refer to the publication record, not nationality or
current employment.

| Re-audited paper | Exact lesson sought | Alternative check and decision |
|---|---|---|
| Information Propagation Effects | Causal effect of topology on useful and harmful messages | Sparse Communication Topology, G-Designer, and other learned/debate graphs were checked. The paper remains technically distinctive, but it was removed because only one multi-agent primary survived and fault injection/containment is more central. |
| Multi-Agent Resilience | Controlled fault generation, architecture-dependent degradation, and remediation | No comparably mature preferred-group paper found in the targeted search combines all three. Despite a team including several Chinese universities, it survives on irreplaceable mechanism; its author list also includes CMU and CUHK/CUHK-Shenzhen researchers. |
| PAT-Agent | Counterexample-guided natural-language-to-model synthesis | Publication affiliations are NUS, Griffith, and Auckland; it is not Chinese-university dominated. It is removed on evidence breadth and redundancy, with DSP selected for a cleaner formal-decomposition role. |
| Agentic Memory / AgeMem | Learned long- and short-term memory actions | Wuhan University and Alibaba are the primary affiliations. The paper is removed because memory loses the standalone block; Beldi provides a stronger persistent-state correctness mechanism from Penn/Rutgers. |
| Memory Management Impacts | Controlled memory contamination and deletion | The publication affiliations are Harvard, Georgia, Michigan State, and Minnesota. It is not Chinese-university dominated. Removal is due to slot priority, not institutional preference. |
| PropertyGPT | Retrieved/adapted reusable formal properties | MSG from Georgia Tech and Waterloo is a comparably strong and more explicitly modular alternative, so the tie-break favors MSG. |

The result contains one deliberately retained Chinese-university-heavy primary,
Multi-Agent Resilience. Automatic exclusion would have removed a mechanism for
which the search did not find an equivalent replacement; retaining two papers in
the same subtopic was not justified.

## E. Research-pedigree audit

The final list is not a university ranking. It represents established research
communities whose methods matter to the course:

- **Software engineering and program analysis:** Princeton PLI, UIUC, NUS,
  Microsoft Research India, Penn/Cornell, UBC/Microsoft Research, Georgia
  Tech/Waterloo, and the foundational Washington/Virginia architecture-recovery
  lineage.
- **Systems and databases:** MIT CSAIL/Microsoft Azure Research for workflow
  and Azure for workflow optimization; Penn/Rutgers for transactional serverless execution; Princeton's
  database lineage for sagas.
- **Programming languages and formal methods:** Caltech/NVIDIA/MIT/UCSB/UT
  Austin for LeanDojo; Meta/Cambridge/Washington/AI2/Google/Cornell/Stanford for
  DSP; Georgia Tech/Waterloo for checked Move specifications.
- **Security:** Google/Google DeepMind/ETH for CaMeL; Northeastern for SAGA; SMU
  for AgentSpec; CMU/Anthropic for ImpossibleBench.
- **Human–agent and multi-agent systems:** USC/ISI TEAMCORE for adjustable
  autonomy, plus the cross-institution ICML fault-injection team.

Pedigree changed actual tie-breaks—MSG over PropertyGPT and DSP over PAT-Agent—
but no shallow paper was promoted for affiliation alone.

## F. Does the final list adequately cover correctness of agent-leveraged applications?

### Why the correctness problem changes

In ordinary application code, programmers and middleware normally make control
flow, sequencing, retry, transaction, and authorization decisions explicit.
In an agent-leveraged application, a probabilistic component can interpret the
goal, choose tools and recipients, infer whether state is current, decide that a
step succeeded, choose whether to retry, and reinterpret intent after an error.
Natural-language context is also both data and a potential source of control.
Therefore correctness is not only “did the final output pass?” It includes the
validity of every observation, authority edge, action order, state transition,
external effect, recovery step, and human-control decision along the trace.

### Dimension map

| Correctness dimension | Selected paper(s) | What mechanism it teaches |
|---|---|---|
| Specification / intent | ImpossibleBench; MSG; DSP; AgentSpec | Create direct test/intent conflicts to expose proxy gaming; generate checked contracts by clause type; compile informal structure into exact obligations; express runtime rules outside the model. No checker proves that the chosen formalization completely captures human intent. |
| State freshness / consistency | CodePlan; Beldi; AgentSpec | Revise explicit plan state after dependency-changing edits; log and isolate mediated persistent state with opacity; make freshness predicates enforceable if the monitor can observe versions/timestamps. **Literature gap:** semantic TOCTOU across arbitrary opaque tools and memory stores. |
| Action ordering | CodePlan; Sagas; Beldi; AgentSpec | Maintain dependency-driven edit order; define ordered subtransactions and reverse compensation; serialize transactional effects; enforce temporal action policies. |
| External side effects | Sagas; Beldi; CaMeL | Distinguish compensable from irreversible effects; provide exactly-once behavior inside a mediated boundary; prevent untrusted data from acquiring privileged capabilities. **Literature gap:** uniform semantics for opaque physical and third-party APIs. |
| Retry / recovery | Sagas; Beldi | Choose backward compensation or forward recovery; use persistent intent logs, invocation IDs, and replay without duplicating completed operations. |
| Authorization / delegation | SAGA; CaMeL; AgentSpec | Cryptographically authorize inter-agent contact and lifecycle; associate capabilities with trusted control/provenance; enforce local authorization predicates at each action. **Literature gap:** general revocation/freshness across already-issued tokens and in-flight plans. |
| Information flow / provenance | IRIS; CaMeL | Infer and validate repository-scale taint paths; separate trusted control from untrusted data and track value provenance into capabilities. |
| Runtime enforcement | CaMeL; AgentSpec; SAGA; Beldi | Capability-mediated execution, policy reference monitoring, protocol enforcement, and transactional mediation provide different trusted computing bases. |
| Human oversight | Towards Adjustable Autonomy; ImpossibleBench; SAGA | Plan control transfers under response and coordination costs; provide a deliberate human-escalation exit when artifacts conflict; retain user governance over agent lifecycle/contact. **Literature gap:** operator mental-model freshness after the plan changes. |

The answer is **yes, with explicit gaps**. The block no longer collapses into
prompt injection: it includes specification authority, transactional state,
compensation, exactly-once replay, human control transfer, provenance,
delegation, and external monitoring. It does not claim to solve open-world state
freshness, memory invalidation, policy completeness, or irreversible physical
effects.

## G. Scenario audit: `S0 → S1 → A1/A2 → A3 failure → retry`

1. **The agent observes `S0` and forms a plan.** CodePlan suggests representing
   the plan as explicit obligations rather than hidden chain-of-thought.
   AgentSpec can attach preconditions and temporal rules. MSG/DSP remind students
   that the encoded condition may still be an incomplete translation of intent.
2. **The world changes to `S1`.** Beldi prevents stale/partial views only for
   state inside its transactional substrate. AgentSpec can require a version or
   fresh read before an action only if the adapter exposes it. For arbitrary tool
   ecosystems this remains a literature gap, not a solved cell.
3. **Authority may be stale.** SAGA identifies the principal, registration,
   lifecycle, contact policy, and token used for delegation; CaMeL associates
   privileged capability with trusted control and provenance. Revocation of
   already-issued authority during an in-flight open-world plan remains partial.
4. **`A1` and `A2` execute; `A2` is irreversible.** Beldi can give exactly-once
   execution only inside its mediated boundary. Sagas forces classification of
   `A2` as reversible, compensable, or truly irreversible and rejects the fiction
   that every committed effect can be rolled back.
5. **`A3` fails.** Sagas asks whether to compensate `A2, A1` in reverse or finish
   by forward recovery. Beldi consults persistent intents/results and resumes
   without duplicating a completed call. AgentSpec may block a retry that violates
   a temporal or idempotency rule.
6. **The agent replans and retries.** ImpossibleBench shows why repeated feedback
   can make the agent optimize the validator instead of intent. The monitor and
   transaction log, not a self-critique prompt, must supply independent evidence.
7. **Memory still contains `S0`-derived facts.** The downgraded memory readings
   explain contamination and evaluator-dependent deletion, but no selected paper
   gives a complete cross-system invalidation protocol. This is an explicit
   literature gap and a design requirement for the exercise.
8. **The human thinks the original intent is still active.** Adjustable Autonomy
   makes control transfer and coordination delay explicit; SAGA keeps user
   governance in the agent lifecycle. Neither fully models operator belief after
   a silent plan revision, so the correct design may require a new approval
   boundary and intent-version notification.

A student completing the sequence can therefore name the violated layer instead
of saying only “the agent hallucinated”: stale observation, stale authority,
underspecified intent, non-atomic sequence, uncompensable effect, duplicate retry,
poisoned memory, incomplete monitor visibility, or failed control transfer.

## H. Paper-by-paper quality audit

| Paper | Non-obvious mechanism | Reading-cost, redundancy, and risk judgment |
|---|---|---|
| SWE-agent | ACI as an ablatable bandwidth/feedback design | Worth a day because the interface is independently varied. Some prompt dependence remains, but the contribution is not prompt-only. No other selected paper teaches bounded repository interaction. |
| CodeAct | Persistent executable language as one compositional action space | Directly conflicts with SWE-agent rather than duplicating it. Agent-washing risk is low because interpreter state and executable composition survive removal of the label. |
| Murakkab | Declarative workflow IR plus profile-guided cross-layer optimizer and adaptive runtime | High reading cost is justified by systems depth. It is not a generic framework paper. Its missing side-effect semantics become a deliberate bridge to the final block. |
| Multi-Agent Resilience | Controlled fault transformation/injection tied to topology and remediation | Synthetic faults and correlated inspectors limit claims, but the experiment is causal enough for one day. It is the only multi-agent primary and survives the preference audit on mechanism. |
| AutoCodeRover | Program-structure-aware localization and iterative repair | Shares the repair task with Agentless but not the control structure. Tests remain a weak oracle, which is surfaced rather than hidden. |
| Agentless | Fixed three-phase pipeline as a strong autonomy control | The cleverness is an architectural negative control, not a new prompt. It prevents the list from assuming autonomy is always beneficial. |
| CodePlan | Explicit edit-obligation graph updated by change-impact analysis | Distinct from both repair papers because program analysis mutates planning state after each edit. Strong industrial SE lineage is a secondary tie-break. |
| IRIS | LLM infers semantic taint specifications/context while CodeQL owns reachability | Clear neuro-symbolic responsibility split and repository-scale evidence. False-negative risk from generated specs is a core discussion point, not a reason to duplicate another analyzer. |
| Software Reflexion Models | Computed convergence/divergence/absence between source and a high-level hypothesis | The 1995 date is compensated by an abstraction modern papers still lack. It is software-specific and not selected for historical fame alone. |
| CodaMOSA | Measured search stagnation triggers model generation, then algorithmic search resumes | Re-earned after a 2024–2026 search. It is older than RippleGUItester but has a cleaner hybrid mechanism and oracle. |
| ImpossibleBench | Impossible test/spec variants make every pass evidence of proxy exploitation | Benchmark papers usually face a mechanism penalty; this one passes because the counterfactual construction changes what can be inferred from a score. |
| MSG | Formal-clause specialization, selective inlining, and prover-feedback repair | Beats the redundant PropertyGPT alternative through clearer roles and ablations. Domain specificity to Move is an acknowledged cost. |
| LeanDojo | Traced proof environment, scoped premise retrieval, and exact state transition API | Infrastructure and algorithm are both substantial. It establishes the strongest validator/runtime reference point without duplicating DSP's sketch interface. |
| Draft, Sketch, and Prove | Formal sketch with holes as an interface contract | High mechanism clarity and strong cross-lab proof lineage justify reading cost. It assumes a correct theorem statement, preserving the intent debate. |
| Sagas | Semantic compensation plus forward/backward recovery for long-lived committed work | Old but foundational in the required sense: current agent work has not replaced its effect semantics. No benchmark-recency substitution was made. |
| Beldi | DAAL, intent collection, exactly-once invocation, and distributed opacity | Systems detail is demanding but essential for reasoning about durable retry. It complements rather than duplicates Sagas because its guarantee requires a mediated boundary. |
| Adjustable Autonomy | Costed conditional control-transfer strategy operationalized as an MDP | Old deployment domain and estimated utilities are limitations. No newer inspected HCI paper offered a comparably concrete control-transfer mechanism plus real deployment. |
| CaMeL | Trusted control/data separation with provenance-aware capabilities | Strong construction-based architecture, low prompt-only risk. ACE is a close alternate, but selecting both would reduce philosophical breadth. |
| SAGA | Provider-mediated identity/lifecycle protocol and cryptographic access tokens | Small task evaluation and trusted-provider assumptions limit scope; authorization/delegation is nevertheless unique in the final set. |
| AgentSpec | Stateful policy DSL and reference monitor over proposed actions | Enforcement is external rather than model self-critique. Hook completeness and policy correctness are explicit limits; no selected paper duplicates the general runtime-monitor role. |

## I. Final global audit

| Required area | Primary coverage |
|---|---|
| Agent interfaces / runtime | SWE-agent; CodeAct; Murakkab |
| Architectural styles / multi-agent | Murakkab; Multi-Agent Resilience; SAGA |
| Coding and repository-level reasoning | AutoCodeRover; Agentless; CodePlan |
| Program analysis | IRIS; CodePlan; MSG |
| Architecture recovery / reverse engineering | Software Reflexion Models |
| Testing and oracle quality | CodaMOSA; ImpossibleBench |
| Specification | MSG; ImpossibleBench; AgentSpec |
| Formal verification / autoformalization / proof / synthesis | MSG; LeanDojo; Draft, Sketch, and Prove |
| State, side effects, and recovery | Sagas; Beldi |
| Security, authority, provenance, enforcement | CaMeL; SAGA; AgentSpec; IRIS |
| HCI / human oversight | Towards Adjustable Autonomy |

The set is not dominated by prompt engineering, SWE-bench systems, role-playing,
or application demonstrations. Every primary leaves a substantive algorithm,
representation, runtime, protocol, formal artifact, analysis, or enforcement
mechanism after removing the words “LLM” and “agent.”
