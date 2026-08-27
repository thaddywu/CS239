# Due-Diligence / Omission Audit — 2026-08-27

## Scope and bottom line

This was an adversarial audit of the existing map, not a new broad survey. It
started from the canonical CSV, notes, topic maps, prior rejection rationales,
coverage matrix, and syllabus; it then targeted papers capable of overturning a
judgment, replacing a weak publication, adding a missing mechanism, or changing
a reading slot. Ten papers met that threshold: eight `strong_candidate` and two
`candidate`.

Three conclusions changed materially:

1. **Memory is now viable as a focused week**: ACL 2026 supplies complementary
   constructive policy learning and controlled failure evidence.
2. **Property generation is no longer missing**, but strict property-based
   testing remains an embedded module rather than a standalone agent subfield.
3. **Systems runtime is no longer mechanism-thin**, because OSDI 2026 contributes
   a real declarative workflow/optimization system; science and hardware remain
   case-rich but mechanism-thin.

The most important negative conclusion survived: no mature peer-reviewed work
found in this audit gives LLM agents transactional rollback, checkpoint/replay,
idempotent tool effects, compensation, or exactly-once execution.

## Can each topic support a classroom discussion?

“Full week” means at least two complementary mechanisms or a mechanism plus a
strong negative/control paper. “Embedded” means technically useful material
exists but not enough independent mechanism diversity for a dedicated week.

| Topic | Support | Recommended papers and one-sentence mechanism | Technical depth | Classroom use |
|---|---|---|---|---|
| Agent architecture / harness | **Full week** | [SWE-agent](papers/swe-agent.md) makes the agent-computer interface an ablated design object; [CodeAct](papers/codeact.md) replaces narrow commands with one executable action language; [Murakkab](papers/murakkab.md) makes the workflow an optimizable declarative program | high to very high | Strong interface-versus-expressiveness-versus-runtime debate |
| Tools and tool use | **Full week or core block** | [Toolformer](papers/toolformer.md) learns when/how to call tools from filtered self-labels; CodeAct studies action composition; SWE-agent studies constrained affordances and feedback | high | Yes—three distinct responsibility allocations, not three tool demos |
| Planning and execution | **Core block** | [LLM-Modulo](papers/llm-modulo-planning.md) confines the model to proposing knowledge while an external planner/verifier owns correctness; [CodePlan](papers/codeplan.md) grows a dependency-driven edit-obligation DAG | high to very high | Yes, especially as proposer–executor–validator comparison |
| Memory / context management | **Full week, newly viable** | [Agentic Memory](papers/agentic-memory.md) learns store/retrieve/update/summarize/discard actions jointly for LTM and STM; [Memory Management Impacts](papers/memory-management-impact.md) shows retrieved experience can propagate errors and that deletion depends on evaluator quality | high | Yes—constructive mechanism plus adversarial empirical control |
| Multi-agent systems | **Full week** | [Information Propagation](papers/information-propagation-topologies.md) measures causal diffusion of insight/error; [Multi-Agent Resilience](papers/multi-agent-resilience.md) injects faults and tests containment; [G-Designer](papers/g-designer.md) learns sparse task-specific graphs | high | Yes—topology, causality, cost, and faults; avoid persona frameworks |
| Testing | **Full week** | [CodaMOSA](papers/codamosa.md) invokes an LM only after evolutionary coverage search stalls; [ImpossibleBench](papers/impossiblebench.md) makes test exploitation observable; [PropertyGPT](papers/propertygpt.md) generates reusable checked formal properties | high to very high | Yes—coverage, oracle authority, and specification gaming conflict directly |
| Program repair | **Full week** | [AutoCodeRover](papers/autocoderover.md) uses structure-aware search and fault localization; [Agentless](papers/agentless.md) fixes localization/sampling/validation into a deterministic pipeline; [RepairAgent](papers/repairagent.md) adds a repair-specific FSM/toolset | high | Yes—best agent-versus-engineered-pipeline discussion in the corpus |
| Runtime validation / verification | **Full week when paired with security/formal methods** | [AgentSpec](papers/agentspec.md) enforces a policy DSL outside the model; [PAT-Agent](papers/pat-agent.md) checks generated CSP# and repairs from model-checker counterexamples; RefineAct checks Prolog pre/postconditions but is still in press | very high | Yes—policy completeness, monitor observability, and intent fidelity |
| Property-based testing | **Embedded, not standalone** | [QuickCheck](papers/quickcheck.md) supplies properties/generators/shrinking; PropertyGPT and [Agentic Specification Generator](papers/agentic-specification-generator.md) generate prover-checked properties/contracts but not a full generator–shrinker lifecycle | foundational/very high, cluster depth medium | Supports a substantial segment, not a full agent-PBT week |
| Program analysis | **Merged week** | [IRIS](papers/iris.md) lets the model infer taint specifications while CodeQL owns reachability; [GPTScan](papers/gptscan.md) proposes vulnerability scenarios and statically validates necessary relations | high to very high | Yes within neuro-symbolic SE; too security-centered as a broad standalone survey |
| Formal methods | **Full week** | [LeanDojo](papers/lean-dojo.md) exposes traced proof state/premises as an agent environment; PAT-Agent adds model checking and counterexample repair; specification papers add code contracts | very high | Yes—now has genuine mechanism diversity across proof/model/specification |
| Autoformalization | **Full block inside formal week** | PAT-Agent turns natural-language systems into checked CSP# models; PropertyGPT and MSG turn code/examples into checked formal clauses | very high | Yes—the key debate is formal consistency versus faithful translation |
| Theorem proving | **Full week** | LeanDojo studies environment/retrieval; [Draft, Sketch, and Prove](papers/draft-sketch-prove.md) inserts a formal sketch between informal reasoning and proof search; [LEGO-Prover](papers/lego-prover.md) grows a verified lemma library | very high | Yes, though two primaries are enough for one week |
| Architecture recovery / repository understanding | **Merged; direct recovery alone still premature** | [SemRef](papers/semref.md) refines explicit recovered architectures using semantics plus dependencies; [Software Reflexion Models](papers/software-reflexion-models.md) computes discrepancies against a hypothesis; CodePlan uses repository dependencies for change planning | high to very high | Yes as a merged module; one modern direct recovery system is not a mature cluster |
| Failure recovery / self-healing | **Gap-driven week** | [Self-correction limitations](papers/self-correction-limitations.md) shows retries without new evidence can hurt; [CRITIC](papers/critic.md) adds falsifying tools; [Microreboot](papers/microreboot.md) supplies the state-preserving recovery baseline agents lack | high, but direct agent recovery depth low | Yes precisely because students must design the missing transactional layer |
| Agent security | **Full week** | [CaMeL](papers/camel.md) separates trusted control from untrusted data; AgentSpec monitors actions; [ACE](papers/ace.md) protects abstract/concrete plans with information-flow checks and execution barriers | very high | Yes—several distinct enforcement philosophies and trusted computing bases |
| Authorization / information flow / policy | **Full block inside security** | CaMeL and ACE enforce dataflow/capability boundaries; [SAGA](papers/saga.md) uses cryptographic tokens and a provider registry for inter-agent authorization; AgentSpec expresses event policies | very high | Yes—capability, dataflow, reference-monitor, and protocol tradeoffs |
| Agent-based software development | **Cross-course thread** | SWE-agent isolates the interface; AutoCodeRover injects SE analysis; Agentless supplies the structured control; CodePlan supplies dependency-driven multi-file planning | high to very high | Strong throughout the course; a separate framework-tour week would duplicate mechanisms |
| Systems / science / hardware | **Mixed: systems yes; combined week no** | Murakkab is a deep workflow-serving runtime; [Coscientist](papers/coscientist.md), [ChemCrow](papers/chemcrow.md), [MLAgentBench](papers/mlagentbench.md), and [ChatEDA](papers/chateda.md) expose consequential domain loops but less reusable architecture | very high for Murakkab; medium/high for cases | Best as runtime cross-listing plus frontier case clinic, not one coherent core week |

## 1. Major omissions found

| Addition | Why it mattered enough to add | Decision |
|---|---|---|
| [Agentic Memory](papers/agentic-memory.md), ACL 2026 | First formally published constructive primary here that makes both LTM and STM operations learned agent actions and provides component ablations | strong candidate; Week 10 primary |
| [How Memory Management Impacts LLM Agents](papers/memory-management-impact.md), ACL 2026 | Supplies controlled evidence for error propagation, misaligned replay, and evaluator-dependent deletion | strong candidate; Week 10 primary |
| [PropertyGPT](papers/propertygpt.md), NDSS 2025 | Directly falsifies the claim that LLM SE still produces only example tests by generating reusable prover-checked invariants/contracts | strong candidate; Week 4/6 optional |
| [Agentic Specification Generator](papers/agentic-specification-generator.md), ASE 2025 | Adds clause-specialized generation, static inlining, and prover feedback with a strong all-in-one ablation | strong candidate; Week 4/6 optional |
| [PAT-Agent](papers/pat-agent.md), ASE 2025 | Adds natural-language system modeling, model checking, and counterexample-guided repair—a missing formal-method mechanism | strong candidate; Week 6 primary |
| [SemRef](papers/semref.md), ICSE 2026 program | A real modern architecture-recovery system, not repository retrieval; it weakens the earlier categorical claim | candidate pending final proceedings/DOI resolution |
| [Murakkab](papers/murakkab.md), OSDI 2026 | Adds the strongest true systems contribution: declarative workflow abstraction, profile-guided optimization, and adaptive execution | strong candidate; Week 1 optional/system primary |
| [ACE](papers/ace.md), NDSS 2026 | Adds a trusted abstract-plan/dataflow/capability architecture distinct from CaMeL and AgentSpec | strong candidate; Week 9 optional/alternate |
| [SAGA](papers/saga.md), NDSS 2026 | Fills the delegation/authorization gap with a concrete cryptographic inter-agent protocol and formal analysis | strong candidate; Week 7/9 optional |
| [G-Designer](papers/g-designer.md), ICML 2025 | Adds learned topology optimization and communication cost, though it explains propagation less well than the current primary | candidate; Week 7 optional |

## 2. Stronger replacements

- **Memory:** AgeMem replaces MemGPT as the constructive primary; MemGPT remains
  short architectural history, and LEGO-Prover remains the verified-memory case.
- **Formal-week diversity:** PAT-Agent replaces LEGO-Prover as Week 6's second
  primary because LeanDojo + PAT-Agent spans proof environments and
  autoformalization/model checking. This is a syllabus-role replacement, not a
  downgrade of LEGO-Prover's technical quality.
- **Direct architecture recovery:** SemRef replaces RepoGraph/RepoCoder when the
  question is specifically architecture recovery; it does not replace CodePlan
  for change-impact planning or Software Reflexion Models for discrepancy
  semantics.
- **No replacements:** the repair pair, multi-agent primary pair, IRIS/GPTScan,
  SWE-agent/CodeAct, CaMeL, and AgentSpec survived focused comparison. ACE and
  SAGA add design points rather than make those papers obsolete.

## 3. Publication corrections

- Corrected the title to **“RepairAgent: An Autonomous, LLM-Based Agent for
  Program Repair”** (comma after “Autonomous”).
- Corrected the FSE 1995 title to **“Software Reflexion Models”** and replaced a
  DBLP link with ACM DOI `10.1145/222124.222136`; the former subtitle was not the
  exact proceedings title.
- Confirmed MemGPT still has no peer-reviewed conference version and remains
  `preprint`.
- Confirmed CaMeL as SaTML 2026 and AgentSpec as an ICSE 2026 research paper.
- Kept RefineAct as `accepted_in_press`; an accepted/program page is not a final
  proceedings record.
- Recorded SemRef as `peer_reviewed_program_no_proceedings_record`: the ICSE
  2026 research-track record is authoritative, but no final DOI/proceedings
  record was located.
- For PAT-Agent, the official ASE program and paper contain seven authors; a
  conflicting personal profile that inserted another author was not used.

## 4. Syllabus judgments changed

- Week 10 is now a required **memory and persistent-state** discussion using the
  two ACL papers, while retaining a shorter frontier project clinic.
- Week 6 now pairs LeanDojo with PAT-Agent to avoid spending both primary slots
  on theorem proving; LEGO-Prover moves to optional/verified-memory cross-list.
- Week 4 now explicitly distinguishes strict PBT from formal property and
  specification generation; PropertyGPT and MSG are optional readings.
- Week 1 gains Murakkab as the systems/runtime extension; the combined
  systems/science/hardware topic still does not replace a core week.
- Week 5 gains SemRef as the direct modern architecture-recovery contrast but
  remains a merged repository/program-analysis module.
- Weeks 7 and 9 gain G-Designer/SAGA and ACE/SAGA respectively without replacing
  their current primary pairs.

## 5. Judgments that survived audit

- **Program repair:** no checked 2025–2026 paper displaced AutoCodeRover and
  Agentless as the most instructive agent-versus-structured-pipeline pair.
- **Multi-agent:** information propagation and fault injection remain better
  primary readings than role workflows or learned topology alone.
- **Failure recovery:** no mature direct adaptation of rollback, compensation,
  durable execution, or exactly-once effects was found; answer revision is not
  systems recovery.
- **Program analysis:** IRIS/GPTScan remain the clearest direct responsibility
  splits; newer papers broaden validator uses rather than replace them.
- **Security:** the standalone-week judgment is stronger after adding trusted
  plans and cryptographic authorization; the old primaries remain valid.
- **Agent-based software development:** it should remain cross-cutting rather
  than become a product/framework survey.

## 6. Remaining uncertainty

- **Architecture recovery:** SemRef's final proceedings metadata needs a recheck,
  and terminology around design understanding may hide work outside “agent”
  labels. Audit confidence remains medium.
- **Runtime enforcement:** 2026 work is moving quickly and lacks common threat
  models/evaluations; RefineAct needs a final paper/artifact review.
- **Failure recovery:** absence claims are intrinsically fragile across workflow,
  serverless, robotics, and long-running-task terminology, despite the targeted
  systems search.
- **Memory:** the new week is strong on policy and empirical failure but weak on
  transactions, provenance, consistency, confidentiality, and deployment-scale
  quality signals.
- **Science/hardware:** important mechanisms may appear as laboratory automation,
  EDA, or control papers rather than agent papers; current evidence still favors
  case studies over a unified week.
- **2026 publication records:** accepted/program pages can precede DOI indexing;
  SemRef and RefineAct should be rechecked before syllabus freeze.
