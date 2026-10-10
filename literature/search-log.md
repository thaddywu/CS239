# Literature Search Log

This file records search reasoning and dead ends, not every literal query.

## 2026-08-26 — Round 0: repository and scope audit

### Starting state

The workspace was empty and was not a Git repository. Initialized Git and added
the persistent schema/protocol before searching, so rejected work and future
gaps would not disappear between sessions.

### Scope decomposition

Expanded the user's topic list into mechanism terms:

- action spaces, agent-computer interfaces, tool learning, tool protocols;
- planner/executor, search, model-based verification, context and typed memory;
- communication topology, aggregation, correlated errors, faulty agents;
- repair localization, fault localization, coverage guidance, properties,
  oracle adequacy, specification gaming;
- taint/dataflow analysis, neuro-symbolic analysis, partial execution;
- proof environments, premise retrieval, proof sketches, autoformalization,
  verified skill libraries;
- repository graphs, change impact, conformance, reflexion models;
- checkpoint/replay, intrinsic versus external feedback, microreboot;
- indirect injection, confused deputy, information flow, capabilities,
  reference monitor, runtime enforcement;
- autonomous experimentation, EDA, OS agents, closed-loop validation.

## 2026-08-26 — Round 1: broad venue and terminology landscape

### Routes searched

1. AI venues: ICLR, ICML/PMLR, NeurIPS, ACL/EMNLP Anthology.
2. Software-engineering venues: ICSE, FSE, ISSTA, ASE programs/proceedings.
3. Systems/security: USENIX OSDI/HotOS, IEEE SaTML, classic protection work.
4. Domain venues: Nature/Nature Machine Intelligence and IEEE TCAD.
5. Citation anchors: ReAct, SWE-bench, QuickCheck, software reflexion models,
   crash-only/microreboot, Saltzer–Schroeder.

Metadata was accepted only from proceedings, publisher pages, DBLP for the old
FSE record, or author publication pages where proceedings were not yet posted.
arXiv is marked as preprint rather than silently treated as peer reviewed.

### Main discoveries

- Interfaces form a coherent lineage: ReAct → Toolformer/CodeAct → SWE-agent;
  DSPy and OpenHands address programming/runtime layers.
- Repair contains a strong autonomy spectrum: SWE-agent → AutoCodeRover and
  RepairAgent → Agentless, plus the non-agent CodaMOSA hybrid.
- Formal systems supply the clearest validator-in-the-loop evidence: LeanDojo,
  Draft–Sketch–Prove, LEGO-Prover, AlphaGeometry.
- Security has progressed from benchmark-only work (InjecAgent, AgentDojo,
  ToolEmu) to architectural enforcement (CaMeL, AgentSpec, RefineAct).

### Early rejections retained

- MetaGPT and ChatDev: real frameworks, but role/SOP workflows do not isolate a
  necessary multi-agent mechanism or matched single-agent control.
- OS-Copilot: workshop/preprint evidence and broad component claims.
- ChipNeMo: domain adaptation rather than an agent action/runtime mechanism.

## 2026-08-26 — Round 2: comparison and full-method inspection

### Full-text checks

Inspected methods, experimental setup, ablations, limitations, and key tables
for the strongest clusters rather than relying on abstracts. Examples:

- SWE-agent: command/search/editor/window/history/lint ablations; shell-only
  control; model transfer.
- AutoCodeRover: structure-aware API search, SBFL integration, bounded validation,
  cost, and manual patch audit.
- Agentless: three-stage control, hierarchical localization, skeleton context,
  reproduction-test selection, and ablations.
- CodePlan: plan DAG, incremental dependency update, change-may-impact rules,
  spatial/temporal context, oracle loop, and final FSE 5/7 result (older arXiv
  reports 5/6).
- IRIS: candidate extraction, model-inferred taint specifications, CodeQL paths,
  contextual filtering, 120-vulnerability benchmark, false-discovery results.
- LeanDojo/LEGO-Prover: environment extraction, novel-premise split, verified
  library data structures, compute-balanced memory ablation.
- communication topology: counterfactual agent propagation metric and explicit
  error/insight diffusion.
- CaMeL/AgentSpec: trusted components, policies/capabilities, utility-security
  results, generated-policy recall, and enforcement limitations.

### Comparisons that changed ranking

- SWE-agent is retained for ACI evidence, not its now-obsolete raw leaderboard
  number. Agentless is required as the deterministic control.
- CodaMOSA outranks many “test agents” because it states exactly when search
  stalls and what the LM contributes.
- LEGO-Prover outranks generic memory papers for the memory week because every
  reusable entry is independently verified.
- Multi-agent topology and injected-fault papers outrank persona/team papers.
- IRIS and CodePlan make stronger “agentic SE” readings than generic coding
  platforms because symbolic software facts control the loop.

## 2026-08-26 — Round 3: gap-directed searches and dead ends

### Architecture recovery

Searched repository understanding, code graphs, feature location, architecture
recovery, conformance, and LLM refinement. Found strong repository retrieval and
change planning (RepoCoder, RepoGraph, CodePlan) but little peer-reviewed work in
which an agent proposes an architectural model/mapping and a separate engine
checks it. Classical software reflexion models expose this missing step.

**Decision:** merge architecture recovery with repository-scale reasoning and
teach the distinction; do not manufacture a standalone modern week.

### Property-based testing and runtime validation

Searches returned QuickCheck as the foundational generator/property abstraction,
CodaMOSA and CoverUp for coverage feedback, and ImpossibleBench for test
exploitation. Few papers make agents synthesize durable properties or invariants
that become independent validators.

**Gap:** property discovery, metamorphic relations, and invariant maintenance are
more important next searches than another SWE-bench agent.

### Failure recovery

Agent searches mostly returned verbal reflection/retry. Citation expansion into
recovery-oriented computing found Crash-Only Software and Microreboot, which
provide state separation and fine-grained restart but have not been convincingly
translated into agent runtimes.

**Gap:** checkpoint/replay, idempotency, transactions, compensating actions, and
recovery from external side effects.

### Science, systems, and hardware

Chemistry searches found Coscientist and ChemCrow with real physical loops;
hardware found ChatEDA and ChipNeMo; OS search found OS-Copilot. The area is
application-rich but does not yet offer enough isolated, reusable mechanisms for
a required week. Hardware is the thinnest subarea.

**Decision:** make this a comparative/student-led case session, not a forced
core week. Revisit after citation chaining from Coscientist and ChatEDA.

## 2026-08-26 — Round 4: 2025–2026 recency and negative controls

### Multi-agent reliability

Followed debate citations into sparse topology, EMNLP 2025 causal information
propagation, and ICML 2025 faulty-agent resilience. Also checked the ICLR 2024
self-correction study, whose matched-budget analysis warns that debate gains can
reduce to sampling. This supplied the missing negative control.

### Security/runtime enforcement

Checked current authoritative publication status:

- CaMeL is peer reviewed at IEEE SaTML 2026.
- AgentSpec is an ICSE 2026 research-track paper.
- RefineAct is accepted to ASE 2026 but, as of this search date, is marked
  `accepted_in_press` because the conference/proceedings are later.
- *Towards Verifiably Safe Tool Use* is an ICSE 2026 NIER paper and is retained
  as a rejected primary due to its early-stage evidence.

### Stop condition for this build

The core weeks now have competing mechanisms and negative controls, while weak
areas have explicit gaps rather than filler. Additional broad search would add
volume without changing the initial syllabus. The next iteration should start
from the gap cells in `coverage.md`, not repeat this landscape search.

## 2026-08-27 — Due-diligence / omission audit

### Starting point and adversarial questions

Read the canonical CSV, all topic maps, coverage, earlier search decisions,
syllabus, and candidate notes before searching. The audit tried to falsify the
least stable conclusions: no standalone memory week, no reusable LLM-generated
properties, no direct modern architecture recovery, no transactional agent
recovery, adequate enforcement-design diversity, and stable repair/multi-agent
primary choices.

## 2026-08-28 — Supplied agent-correctness and runtime list audit

### Starting state and gap

Re-read the canonical index, security, multi-agent, recovery, HCI, architecture,
coverage, rejection notes, and final outline before following the supplied list.
The target was not generic agent safety: it was Miryung's question about what
correctness problems appear when an agent dynamically chooses tool sequences,
coordinates peers, carries persistent intent, and commits effects through APIs.

### Verification and full-text inspection

Verified final records for TraceFix (ACM CAIS 2026), ToolGuard (EMNLP 2025
Industry), SagaLLM (PVLDB 2025), and Semantic Commit (UIST 2025). Kept Atomix,
Agent-C, VIGIL, and Language-Based Agent Control explicitly at preprint status.
For all eight, inspected the mechanism, experimental setup, central results or
ablations, and limitations rather than relying on abstracts.

### Decisions that changed the map

- TraceFix is the strongest published addition: TLA+/TLC counterexample repair
  plus runtime coordination monitoring addresses agent-specific interleavings.
- Atomix is the clearest modern external-effect semantics, but remains a
  preprint and therefore a frontier handout.
- Agent-C and LBAC are real challengers to AgentSpec and CaMeL respectively;
  publication status, not mechanism depth, is the current barrier.
- Semantic Commit is the best published supplied option for the SE+HCI edge.
- SagaLLM was rejected as a primary after full review; its experiments do not
  substantiate durable transaction guarantees.

### Broad-list triage

Safety benchmark papers were retained as evaluation resources rather than
primary mechanisms. Routing, cascades, advisor, distillation, and weak-link
optimization do not fill the correctness gap. Cedar and related 2024
authorization work were not reintroduced under the recency preference. Titles
without an authoritative exact record were left unverified rather than guessed.
The full grouped rationale is recorded in
`literature/supplied-agent-correctness-audit-2026-08-28.md`.

### Instructor decision

The instructor approved both TraceFix and Semantic Commit as primary readings.
The canonical index and syllabus now contain 19 papers: TraceFix joins the
communication/coordination block, while Semantic Commit joins the final
oversight/evolving-intent block. Atomix remains explicitly marked as an
unpublished frontier reading.

### Venue and citation routes

- Inspected 2022–2026 programs/proceedings across ICSE, FSE, ASE, ISSTA, SANER,
  ICSME; PLDI, POPL, OOPSLA, CAV, TACAS, FM; SOSP, OSDI, NSDI, EuroSys, ASPLOS,
  ATC; S&P, USENIX Security, CCS, NDSS, SaTML; and NeurIPS, ICML, ICLR, ACL,
  EMNLP, NAACL, AAAI, IJCAI.
- Followed citation/author chains from MemGPT, LEGO-Prover, QuickCheck,
  CodaMOSA, Agentless, CodePlan, Software Reflexion Models, Microreboot, CaMeL,
  AgentSpec, and the current multi-agent topology/fault papers.
- Expanded terminology to property/specification/invariant generation,
  autoformalization/model repair, architecture refinement, dependency graphs,
  durable workflows, authorization, and information flow; discovery did not
  depend on “agent” appearing in a title.

### Full-method inspections added to the corpus

Inspected method, setup, a central result/ablation, and limitations for ten
papers: AgeMem; the ACL memory-management empirical study; PropertyGPT; Agentic
Specification Generator; PAT-Agent; SemRef; Murakkab; ACE; SAGA; and G-Designer.
All ten are recorded in `papers.csv` with decision notes. Eight are strong
candidates; SemRef and G-Designer are candidates because the former has a
proceedings-record caveat and the latter is less explanatory than the existing
topology primary.

### Screened but not added

- Memory-R1 and HiAgent overlap the stronger ACL memory pair; RMM, THEANINE,
  Hindsight, ARTEM, and CA3Mem are narrower/domain-specific.
- Event-B Agent and *Automated Lemma Discovery in Agentic Program Verification*
  are important upcoming successors without final proceedings records at the
  audit date.
- IGSIL and GraphCoder concern localization/context graphs rather than explicit
  architecture recovery; SANER 2026 non-agent recovery work strengthens the
  baseline but not the agent-mechanism cluster.
- Amur, CausalRepair, and AROP add repair/analysis variants but do not challenge
  Agentless's structured-pipeline control or change the selected repair pair.
- IsolateGPT is ACE's predecessor; Rennervate is a model-level security design;
  neither adds a more useful course role than the retained architecture set.
- Recent scientific-agent and AFM evaluations add useful domain failures but no
  reusable runtime mechanism beyond the selected cases.

### Publication and metadata audit

- Rechecked title, author order, year, venue, publication status, and URL for all
  48 pre-existing `candidate`/`strong_candidate` records against proceedings,
  publisher metadata, OpenReview, ACL Anthology, USENIX, or DOI/Crossref records.
- Corrected the exact ICSE title to *RepairAgent: An Autonomous, LLM-Based Agent
  for Program Repair*.
- Corrected the FSE 1995 URL to ACM DOI `10.1145/222124.222136`. A later
  version-of-record check against the publication PDF and author page restored
  the full title *Software Reflexion Models: Bridging the Gap Between Source and
  High-Level Models*.
- Confirmed MemGPT remains a preprint, CaMeL is SaTML 2026, AgentSpec is an ICSE
  2026 research-track paper, and RefineAct should remain `accepted_in_press`.
- Recorded SemRef as `peer_reviewed_program_no_proceedings_record`: the ICSE
  research-track/program record is authoritative, but no final DOI/proceedings
  record was found. No venue was inferred from arXiv alone.

### Judgments after attempted falsification

- **Overturned:** memory/context management now supports a focused week.
- **Weakened:** reusable property/specification generation is real, but strict
  QuickCheck-style PBT is not a mature agent subfield; direct architecture
  recovery exists but is not yet a diverse standalone cluster; systems runtime
  is no longer mechanism-thin because of Murakkab.
- **Upheld:** repair primaries; multi-agent topology/fault primaries; formal and
  security standalone weeks; program-analysis responsibility split; coding
  agents as a cross-course thread; no mature transactional agent recovery.

### Stop condition

The search stopped when new results were either mechanism duplicates, weaker
publication types, domain applications, or papers that would not change a
candidate comparison or syllabus slot. The audit added ten decision-relevant
papers rather than rebuilding the landscape.

## 2026-08-27 — Final 20-paper-day selection and metadata verification

### Scope

Re-read the canonical CSV, all topic maps, coverage assessment, syllabus draft,
and every decision note. The existing pool was sufficient, so this was a
selection and verification pass rather than a new discovery search; no papers
were added.

### Selection decisions

- Selected exactly 20 primary papers and recorded the re-ranking in
  `literature/final-selection-audit.md`.
- Preserved only mechanism-distinct clusters: constrained versus expressive
  interfaces; causal topology versus injected-fault containment; analysis-
  guided versus fixed-pipeline repair; test search versus oracle exploitation;
  constructive versus failure-oriented memory; information-flow versus
  event-policy enforcement.
- Promoted Microreboot despite its age because fine-grained restart and durable-
  state separation fill a current agent-runtime gap that retry papers do not.
- Kept Toolformer, LLM-Modulo, RepairAgent, MSG, LEGO-Prover, DSP, intrinsic
  self-correction, CRITIC, ACE, SAGA, G-Designer, and SemRef as named background
  or near misses, with explicit redundancy reasons rather than silent omission.

### Publication and affiliation verification

Rechecked all 20 selections against official proceedings, publisher pages,
ACL Anthology, PMLR, USENIX, or the version-of-record PDF. Author institutions
in `syllabus/reading-list-draft.md` come from the paper's publication record,
not inferred current employment. The check also confirmed final peer-reviewed
status for the 2026 ACL, ICLR, OSDI, SaTML, and ICSE papers used in the draft.

### Final shape

The draft contains 20 paper days, two Document Review days, and one five-minute
student frontier-scan session. Its center of gravity is repository-scale coding,
analysis, testing, specification, formal checking, memory reliability, and
recovery; architecture, applications, and safety form the entry and synthesis
units.

## 2026-08-27 — Final-selection v3 targeted gap search

### Starting point and gap test

Re-read `papers.csv`, every paper note and topic map, coverage, both earlier
audits, the outline, and the 20-paper draft before searching. Re-ranking exposed
four decision-relevant gaps: architecture recovery had no primary; CodaMOSA had
not been tested against 2024–2026 alternatives; formal-method slots were too
narrow; and correctness lacked transactions, external side effects, authority
freshness, and human control transfer.

### Search routes

- Architecture recovery: ICSE/FSE/ASE/TSE/SANER programs and citation paths from
  reflexion models, using design understanding, conformance, concept recovery,
  change impact, and neuro-symbolic analysis terms.
- Testing: ICSE/FSE/ASE/ISSTA 2024–2026 proceedings for coverage-guided,
  mutation, GUI/differential, oracle, property, and specification generation.
- Recovery/state: OSDI/SOSP/NSDI/EuroSys and database/workflow literature using
  durable execution, exactly once, semantic transactions, sagas, compensation,
  idempotence, partial execution, and revision/reversibility terms.
- Human oversight: JAIR/AAMAS/HCI and cited mixed-initiative work using
  adjustable autonomy, transfer of control, escalation, response uncertainty,
  and team miscoordination.
- Multi-agent preference audit: proceedings and citation-neighbor search for
  preferred-group alternatives with controlled fault injection and containment,
  not role prompts or aggregate debate accuracy.

### Papers fully inspected

- [RippleGUItester](papers/rippleguitester.md), ISSTA 2026: candidate, not a
  replacement for CodaMOSA.
- [Beldi](papers/beldi.md), OSDI 2020: selected for exactly-once replay,
  stateful transactions, and workflow isolation.
- [Sagas](papers/sagas.md), SIGMOD 1987: selected for semantic compensation and
  forward/backward recovery.
- [Towards Adjustable Autonomy](papers/towards-adjustable-autonomy.md), JAIR
  2002: selected for transfer-of-control strategies and MDP operationalization.
- [Cordon](papers/cordon.md), arXiv 2026: exact-fit agent semantic-transaction
  preprint, rejected from the primary list pending peer review.
- [Revisable by Design](papers/revisable-by-design.md), arXiv 2026: useful
  reversibility taxonomy, rejected because synthetic/judge-based preprint
  evidence does not clear the primary bar.

The TSE 2025 *A Holistic Approach to Design Understanding Through Concept
Explanation* was inspected at abstract/metadata depth and recorded as `skimmed`;
the full method/evaluation was not accessible, so no promotion was inferred.
The ISSTA 2026 coverage/mutation-score replicability study was also recorded as
`skimmed` and retained as evaluation context rather than a mechanism primary.

### Selection consequences

- Promoted Software Reflexion Models, MSG, Draft–Sketch–Prove, SAGA, Beldi,
  Sagas, and Adjustable Autonomy.
- Removed the second multi-agent paper, both memory papers, PropertyGPT,
  PAT-Agent, Microreboot, and AlphaGeometry from the 20 primary slots; all remain
  recorded with explicit non-rejection rationales.
- CodaMOSA survived the new testing search because its stagnation-triggered handoff
  and return to evolutionary search remain the clearest hybrid mechanism.
- Kept one Chinese-university-heavy paper, Multi-Agent Resilience, after no
  comparably direct preferred-group fault-injection/containment paper was found.

### Metadata and evidence checks

Author order, venue, year, publication status, and affiliations for every final
paper were checked against official proceedings, publisher pages, or the
publication PDF. Key corrections include Cornell as Saikat Dutta's IRIS
affiliation; Anthropic as Nicholas Carlini's ImpossibleBench affiliation; the
full reflexion-model title; and exact publication affiliations for MSG, DSP,
SAGA, Beldi, Sagas, and Adjustable Autonomy.

### Stop condition

Search stopped when each structural gap had either a selected, fully inspected
paper or an explicit literature gap, and additional results were preprints,
mechanism duplicates, weaker evidence, or application cases. The canonical CSV
now contains 72 records and exactly 20 `selected` entries.

## 2026-08-27 — Reading-list v4 structural refinement

### Starting point and bounded questions

Re-read the v3 list, canonical CSV, coverage matrix, outline, relevant topic
maps, and decision notes. This was not a new landscape survey. Search was
limited to four questions raised by the revised eight-week structure:

1. Is there a stronger multi-agent communication/coordination mechanism than a
   resource-orchestration paper plus one fault-injection study?
2. Has modern agentic architecture recovery matured enough to replace a 1995
   foundational primary?
3. Is there peer-reviewed agent-native work on durable effects, rollback,
   transactionality, or commit-time consistency?
4. Is there modern LLM-agent HCI evidence strong enough to replace the 2002
   adjustable-autonomy primary?

### New papers inspected and recorded

- [CARD](papers/card.md), ICLR 2026: fully inspected and selected for adaptive
  condition-aware topology generation.
- [State Delta Encoding](papers/state-delta-trajectory.md), EMNLP 2025: fully
  inspected and retained as communication background because it requires
  white-box hidden-state transfer.
- *MultiAgentBench*, ACL 2025: skimmed; useful protocol benchmark but not a
  mechanism primary.
- [RepoProbe](papers/repoprobe.md), ASE 2026: fully inspected and retained as a
  strong alternative/negative control for architecture-aware comprehension.
- [Automated Software Architecture Design Recovery](papers/automated-architecture-design-recovery.md),
  ECSA 2025, and [Can Agents reconstruct microservice architecture?](papers/can-agents-reconstruct-microservice-architecture.md),
  ESEM 2026 Emerging Results: inspected and rejected as primary because the
  mechanisms remain prompting/self-reflection or lightweight role-guided
  exploration.
- [Plan-Then-Execute](papers/plan-then-execute.md), CHI 2025: fully inspected
  and selected. The 2×2 study shows that planning/execution involvement can
  help or harm, does not reliably calibrate trust, and adds cognitive load.
- [ACRFence](papers/acrfence.md), *Agentic Transaction*, and
  [Temporary Authority, Permanent Effects](papers/temporary-authority-permanent-effects.md):
  inspected as exact-fit 2026 preprints. They sharpen checkpoint replay,
  semantic ACID, TOCTOU, and authorized-commit questions but do not clear the
  peer-reviewed primary bar.
- [Governance by Construction](papers/governance-by-construction.md), ACM CAIS
  2026: rejected as a short demo overlapping AgentSpec.

### Decisions

- Replaced Murakkab with CARD and restored Information Propagation Topologies;
  retained Multi-Agent Resilience after placing causal/adaptive coordination
  mechanisms before it.
- Moved Software Reflexion Models to background and recorded modern agentic
  architecture recovery as a gap. RepoProbe is an alternative evaluation
  reading, not a forced recovery mechanism.
- Retained CodaMOSA after the prior 2024–2026 comparison.
- Assigned Sagas by default and made Beldi an alternative, avoiding two
  foundational systems papers for one correctness subquestion.
- Replaced Adjustable Autonomy with Plan-Then-Execute as the modern primary;
  retained the 2002 MDP paper as a formal alternative.
- Retained SAGA because delegation/identity remains unique despite its trusted
  provider and narrow evaluation.
- Corrected Cordon's author list against the current arXiv record; the earlier
  local author metadata was inconsistent with that authoritative source.

### Stop condition

Search stopped after every disputed v3 slot had either changed, re-earned its
role, or become an explicit gap. The v4 working set contains 19 primary papers;
additional hits were preprints, benchmark-only work, short demos, or weaker
prompt-based variants that would not alter the eight-week structure.

## 2026-08-27 — Reading-list v5 mechanism refinement

### Prior state read before searching

Re-read the canonical CSV, v4 list and decisions, coverage matrix, full search
log, syllabus outline, selected/strong-candidate notes, and the architecture,
agentic-development, program-analysis, formal-methods, multi-agent,
testing/repair, security, failure-recovery, human-interaction, and
architecture-recovery maps. The search began from four gaps left by v4:

1. symbolic and relational analysis beyond CodePlan/IRIS, especially Datalog;
2. task allocation and scheduling beyond multi-agent communication topology;
3. deeper Agentic SE mechanisms outside generic repair, including requirements,
   conformance, security, systems/performance, synthesis, and constraints;
4. modern agent-native treatment of external effects and human control binding.

Every v4 primary was then re-audited under the oracle counterfactual before any
new paper was promoted.

### Search routes

- Searched FSE, ICSE, ISSTA, ASE, PL/security venues, proceedings pages, arXiv
  records, and citation paths using Datalog, logic programming, static analysis,
  slicing, dataflow, taint, abstract interpretation, symbolic execution, ghost
  code, SMT, constraints, invariants, model checking, and code-property graphs.
- Searched NSDI/OSDI/SOSP/EuroSys and ACL/EMNLP agent-workflow literature for
  whole-program serving, critical paths, admission/routing, task allocation,
  scheduling, shared memory, consistency, concurrency, and fault containment.
- Searched requirements formalization, traceability, RFC/specification
  conformance, exploit generation, proof/lemma synthesis, configuration,
  performance diagnosis, database/query reasoning, and software evolution.
- Repeated transaction, idempotency, compensation, checkpoint, replay,
  commit-time authorization, approval freshness, and control-transfer searches
  using systems vocabulary rather than only the word “agent.”

### Fully inspected and selected

- [NESA](papers/nesa.md), FSE 2026: restricted Datalog policy language,
  symbolic/neural relations, lazy fixed-point evaluation, slicing/bug studies,
  component ablations, real findings, and limitations inspected. This is the
  exact Datalog family recalled in the prompt.
- [Agentix](papers/agentix.md), NSDI 2026: PLAS and ATLAS algorithms,
  single/distributed engine setup, throughput/latency results, comparisons, and
  program-observability boundary inspected.
- [LLM-as-Scheduler](papers/llm-as-scheduler.md), ACL 2026: gate/scheduler
  division, routing actions, token/latency results, gate and scheduler ablations,
  routing error, and domain limits inspected.
- [AutoCodeSherpa](papers/autocodesherpa.md), ISSTA 2026 accepted in press:
  input/infection/output conditions, PBT/internal formulas, generation and
  refinement, manual labels, repair/localization effects, cross-model and
  component evidence inspected.
- [Gordian](papers/gordian.md), ISSTA 2026 accepted in press: inverse functions,
  surrogate models, heap partitions, KLEE/Z3 integration, original-program
  checks, LogicBombs/FDLibM/structured-program results, and ablations inspected.
- [HoarePrompt](papers/hoareprompt.md), ICSE 2026: natural strongest
  postconditions, loop k-induction, CoCoClaNeL setup, MCC comparisons, ablations,
  and non-formal/fuzzy-classifier limitations inspected.
- [ARTEMIS](papers/artemis.md), ICSE 2026: structured-NL-to-LTL pipeline,
  candidate decomposition, balanced distinguishing traces, five safety-critical
  datasets, user-query reductions, failures, and simulated-expert assumptions
  inspected.
- [RFCAudit](papers/rfcaudit.md), ASE 2025: hierarchical semantic indexing,
  demand-driven query tools, self-review, six protocol implementations, real
  bugs, and indexing/retrieval/review ablations inspected.

### Serious challengers recorded

- [LogicLoc](papers/logicloc.md): LLM-synthesized Datalog programs plus parser
  and mutation feedback; retained as a preprint candidate behind NESA.
- [PAGENT](papers/pagent.md): program-analysis-guided PoC generation; retained
  as a narrow accepted-in-press security candidate.
- [ProbGuard](papers/probguard.md): predicate abstraction, learned DTMC, CTL
  prediction, and PAC analysis; strong candidate, not selected because the small
  study does not satisfy the practical formal sample conditions.
- [LemmaNet](papers/lemmanet.md): offline lemma discovery and online proof-state
  adaptation; strongest accepted-in-press verification challenger for the
  syllabus-freeze recheck.
- [Event-B Agent](papers/event-b-agent.md): formal model synthesis and repair;
  candidate, but insufficient inspected comparative evidence to displace the
  selected formal readings.
- [ACTaint](papers/actaint.md): multi-role access-control taint analysis;
  candidate behind the cleaner IRIS division of labor.
- [Semia](papers/semia.md): constraint-guided representation synthesis and
  Datalog auditing of agent skills; exact-fit preprint candidate.
- [Deductive Steering](papers/deductive-steering.md): each reasoning step carries
  an SMT encoding checked for logical consequence, with counterexample refinement
  and backtracking across fault localization, synthesis, and invariant tasks.
  Recorded as a candidate because only the official ISSTA abstract was available;
  no uninspected ablation or limitation was inferred.
- [AMA](papers/ama-adaptive-memory.md): inspected and rejected as primary because
  lifecycle roles do not define concurrent shared-state consistency.
- [H-MAS](papers/h-mas.md): inspected and rejected as primary because the
  hierarchical “agents” are serving-controller roles, not agent programs.

Screened but not added as serious candidates: VADAOrchestra (Datalog workflow
application outside SE), CacheSlide and SYMPHONY (model-serving rather than
agent-program scheduling), NL-to-schedule task planners, prompt-heavy
configuration/operations agents, generic query-optimization agents, and new
architecture-recovery prompts. They did not clear the mechanism/relevance bar.

### Metadata and evidence verification

Titles, author lists, venues, dates, and publication status were checked against
final publisher/proceedings records where available: ACM DOI/FSE for NESA,
USENIX for Agentix, ACL Anthology for LAS, ICSE proceedings/program and ACM DOI
for HoarePrompt and ARTEMIS, IEEE DOI/ASE program for RFCAudit, and the ISSTA
2026 research program plus current preprints for AutoCodeSherpa and Gordian.
The latter two remain `accepted_in_press` until final publisher records are
available. Preprint-only records are labeled as such rather than assigned a
venue by inference.

### Final comparisons and stop condition

The v5 set retains 11 v4 primaries and adds eight. CARD, Multi-Agent Resilience,
CodePlan, AutoCodeRover, CodaMOSA, MSG, Draft--Sketch--Prove, and Sagas leave
primary status for distinct reasons recorded in the audit; none was silently
deleted. Search stopped when each disputed slot had (a) a fully inspected
mechanism-distinct winner, (b) an explicit strong alternative, or (c) a
documented gap. Further results were mechanism duplicates, application-only
uses, weaker evidence, or preprints. The late Deductive Steering check brings
the canonical CSV to 101 records and exactly 19 `selected` entries.

## 2026-08-28 — Final adversarial seminar-worthiness review

### Scope and method

Re-read reading-list v5, its audit, v3/v4/v5 decisions, all selected notes,
coverage, topic maps, and the prior search record before opening any new source.
For every primary, recorded the concrete mechanism, oracle counterfactual,
unique lesson, strongest objection, and remove-one-paper consequence. The full
technical/evaluation/limitation sections received particular attention for
NESA, Gordian, AutoCodeSherpa, ARTEMIS, RFCAudit, Agentix, LAS, HoarePrompt,
SAGA, and Plan-Then-Execute.

Targeted search was limited to the weaknesses that review exposed: shallow
program-logic prompting, shallow workflow routing, and overstated delegation.
No broad new survey was run. Publication status and metadata were rechecked
against ACL Anthology, NDSS proceedings, conference research programs, and the
authors' released artifacts.

### Decision-changing inspection

- [HoarePrompt](papers/hoareprompt.md) is rejected as a primary. Its
  natural-language states, loop generalization, and final entailment are prompted
  model outputs without executable semantics or soundness; “k-induction” is
  three unrolls followed by generalization. Absolute MCC is 0.159--0.259 at
  roughly 39--64× the baseline token cost.
- [LLM-as-Scheduler](papers/llm-as-scheduler.md) is rejected as a primary. Its
  mechanism is a benchmark-specific schema/DistilBERT gate plus a prompted JSON
  router over a fixed workflow, with about 66% routing accuracy and no resource,
  dependency, concurrency, tool, or durable-state semantics.
- [SAGA](papers/saga.md) moves from selected to strong background. Its provider,
  one-time-key, and encrypted quota/expiry-token protocol establishes contact
  authentication and secrecy, but not attenuated task authority, delegation
  chains, policy correctness, or immediate revocation.
- [LemmaNet](papers/lemmanet.md) moves from strong candidate to selected after
  full-paper inspection. Offline semantics-aware VC generation and
  obligation-aligned proved lemmas feed an adaptive online lemma maintainer;
  every imported/refined lemma and the original Frama-C VC are checked in Rocq.
  On 941 VCs it proves 364 versus AutoRocq's 287, with offline, online, and
  semantic-analyzer ablations falling to 328, 302, and 301.

### Challengers and stop decisions

LemmaNet is the only challenger that clearly beats a v5 primary. ProbGuard's
practical sample is far below its useful PAC regime; only abstract-level
accepted evidence remains available for Deductive Steering; AutoCodeRover,
CodePlan, and CodaMOSA overlap retained repair/analysis mechanisms; Draft–Sketch–
Prove and Agentic Specification Generator overlap the now stronger exact-proof
sequence; Multi-Agent Resilience and CARD do not add shared-state or independent
recovery semantics. Murakkab remains a broader profile-guided deployment
optimizer but does not beat Agentix's non-clairvoyant dynamic-program scheduler.

Search stopped at 17 primaries: 16 v5 survivors plus LemmaNet. Further hits were
mechanism duplicates, abstract-only accepted work, or papers that did not beat a
specific retained assignment. The final state is recorded in
[reading-list-v5-final-review.md](reading-list-v5-final-review.md), the canonical
CSV, topic maps, coverage matrix, and syllabus outline.

## 2026-08-28 — Ingredient-level agent and multi-agent architecture audit

### Trigger and gap

The frozen list taught strong SE boundaries—agent-computer interface, executable
actions, runtime scheduling, communication topology, and checked coordination—
but did not directly answer how the usual internal agent modules or multi-agent
organizational ingredients compose. The search was therefore limited to recent
peer-reviewed architecture abstractions rather than reopened as a generic agent
framework search.

### Sources and papers inspected

- Fully inspected [AgentSquare](papers/agentsquare.md),
  [MaAS](papers/maas.md), [GPTSwarm](papers/gptswarm.md),
  [Evolving Orchestration](papers/evolving-orchestration.md), and
  [Flow](papers/flow.md), including their method, central experiments,
  ablations, and limitations.
- Rechecked ICLR, ICML/PMLR, and NeurIPS proceedings metadata. TapeAgents was
  screened but remains a 2024 technical report; ADAS was checked as an
  architecture-search alternative but does not supply a stable ingredient
  taxonomy. Neither was promoted into the decision set.
- Revisited the NeurIPS 2025 position
  [Large Language Models Miss the Multi-agent Mark](papers/llms-miss-multi-agent-mark.md)
  for classical-MAS ingredient vocabulary, not as an empirical primary.

### Decision

AgentSquare is the only challenger that changes the single-agent architecture
judgment. Its planning/reasoning/tool/memory tuple is the clearest current
ingredient map, although its evidence primarily validates architecture search.
It becomes a strong candidate; the selected 19 are not silently changed.

No single multi-agent paper dominates the existing pair. Evolving Orchestration
is the best inspected organization-level companion because it joins agent
heterogeneity, dynamic selection, and induced topology. Information Propagation
still gives the stronger causal communication lesson, while TraceFix alone
turns interleavings and deadlock into checked protocol obligations. MaAS and
GPTSwarm are useful search abstractions; Flow is rejected after full inspection.

### Reading-list v6 resolution

The course allocates two weeks—not three—to agent and multi-agent architecture.
AgentSquare replaces CodeAct in Week 1; Evolving Orchestration replaces
Agentless in Week 2. CodeAct remains the expressive-action comparison and
Agentless remains the repair/autonomy control. The resulting 19-paper list is
recorded in `syllabus/reading-list-v6.md`, and `syllabus/outline.md` now points
to v6.

## 2026-08-28 — Fall syllabus placement and instructor-review list

The actual Fall calendar contains 16 paper-discussion meetings, so assigning all
six v6 architecture and multi-agent papers would consume three weeks. The
date-level schedule now assigns AgentSquare, SWE-agent, Evolving Orchestration,
and TraceFix across Weeks 1--2. Agentix and Information Propagation remain
replacement candidates rather than extending the introductory sequence.

The remaining 12 meetings cover repair/testing, program analysis, requirements
and conformance, verification, security/runtime assurance, and human oversight.
`syllabus/paper-list-fall2026.md` records the 16 proposed assignments, six
replacement candidates, and one short framing reading with verified metadata
and decision-relevant discussion summaries. `reading-list-v6.md` is explicitly
labeled as the reviewed 19-paper research pool rather than the date-level
schedule.

## 2026-08-29 — Reading-list v7 technical-depth and evaluation audit

### Trigger and method

Re-read the canonical CSV, coverage matrix, relevant topic maps, v6 list,
date-level schedule, and the method/evidence/limitations notes for every
scheduled paper. Each primary had to expose a discussable algorithm,
abstraction, interface, language, protocol, runtime, verifier, or uniquely
illuminating negative result. Benchmark rank, recency, and author/venue prestige
were not treated as technical depth.

### Decisions

- Information Propagation replaces TraceFix in the multi-agent week. Evolving
  Orchestration now covers dynamic organization, while CAPE and EIB-Learner
  cover causal message flow and topology design.
- TraceFix remains selected but moves to coordination correctness/runtime
  assurance. Its PlusCal/TLA+/TLC loop and partial runtime conformance are the
  central technical objects.
- ACE replaces CaMeL in the scheduled security slot after full-paper review.
  ACE's trusted abstract plan, concrete app binding, static information-flow
  check, and isolated capability execution form an end-to-end architecture.
  CaMeL remains the closest strong alternate and was not demoted for lack of
  depth.
- Semantic Commit remains as the single mechanism-bearing SE/HCI primary.
  Plan-Then-Execute becomes a strong supporting empirical paper because its 2x2
  user study is the dominant contribution.
- Agentix and LeanDojo remain technically deep alternates. The 16-meeting list
  does not add a serving week or a second theorem-proving paper.
- ImpossibleBench is the only evaluation-first exception. Its impossible-task
  construction makes specification gaming logically observable and reveals
  access, feedback-loop, and monitor failures that the mechanism papers do not.

### New papers inspected

- [PSearch](papers/psearch.md), ASE 2026: the official program describes a
  structured intermediate-patch state and MCTS allocation over long-horizon
  repair. It remains unread/watch-list because the full method, ablations, and
  limitations were not publicly auditable.
- [CANDOR](papers/candor.md), ASE 2026 Journal First: the official abstract
  describes specialized prompt roles and panel consensus for JUnit generation.
  It is rejected because no independent oracle or protocol-level coordination
  mechanism is apparent; AutoCodeSherpa and ImpossibleBench remain stronger.

The resulting 16-paper decision and per-paper objections are recorded in
`syllabus/reading-list-v7.md`; the schedule, outline, canonical CSV, instructor
paper list, topic maps, and coverage matrix were synchronized.

## 2026-08-29 — Agent architecture overview survey audit

### Gap and search method

The existing architecture unit had strong mechanisms but no explicit overview
above them: AgentSquare maps planning/reasoning/tools/memory, SWE-agent isolates
the environment interface, and Agentix supplies runtime scheduling. Re-read the
canonical CSV, architecture and multi-agent topic maps, coverage matrix, and
prior architecture-search decisions before searching publisher/proceedings
records for surveys that jointly cover internal modules, control loops,
environment/tool boundaries, multi-agent organization, and oversight.

### Papers inspected

- [From Language Models to Agentic AI](papers/from-language-models-to-agentic-ai.md),
  Cognitive Computation 2026: the closest single engineering overview, with six
  modules and autonomy/tool/collaboration/governance axes. Candidate only as
  framing because the record appeared on 24 August and the architecture is a
  synthesis rather than a tested mechanism.
- [A Survey on Large Language Model Based Autonomous Agents](papers/survey-llm-autonomous-agents.md),
  FCS 2024: the cleanest established profile-memory-planning-action map.
- [Large Language Model Based Multi-agents](papers/llm-multiagents-survey.md),
  IJCAI Survey Track 2024: the strongest compact companion for environment,
  profiling, communication, and capability acquisition.
- [The Rise and Potential of LLM Based Agents](papers/rise-potential-llm-agents-survey.md),
  SCIS 2025: broad brain-perception-action reference covering single, multi,
  human-agent, and agent-society settings, but too long and conceptual.
- [Agentic AI Systems](papers/agentic-ai-systems-survey.md), Neurocomputing
  2026: broadest taxonomy across architecture, cognition, interaction, trust,
  and evaluation; less crisp as an operational reference architecture.
- [From Language to Action](papers/from-language-to-action-review.md),
  Artificial Intelligence Review 2026: current and useful for citation paths,
  but catalogue- and evaluation-heavy.
- [Agentic AI: A Comprehensive Survey](papers/agentic-ai-comprehensive-survey.md)
  and [the hybrid-architecture SLR](papers/hybrid-agent-architectures-slr.md)
  were rejected for this role: the first is a symbolic-versus-neural paradigm
  history, and the second is a 30-paper hybrid-systems position.
- [A Review of Prominent Paradigms](papers/prominent-agent-paradigms-review.md),
  COLING 2025, was retained as skimmed specialization: its tool/planning/feedback
  workflow taxonomy is technical but not comprehensive.
- A lifecycle-oriented Neurocomputing survey was screened from its publisher
  abstract, but the full record was inaccessible during this audit; it was not
  promoted or used to change a decision.

### Decision

Do not replace AgentSquare or SWE-agent with a survey. If one overview is
needed, assign selected sections of Bajoria et al. as instructor framing. If
stability and compactness matter more than one-paper convenience, use short
excerpts from Wang et al. and Guo et al. The architecture and multi-agent units
remain capped at two weeks; no syllabus file changes in this round.
