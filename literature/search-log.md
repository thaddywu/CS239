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
- Corrected the FSE 1995 title to *Software Reflexion Models* and replaced the
  DBLP URL with ACM DOI `10.1145/222124.222136`; the former subtitle did not
  belong to that proceedings title.
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
