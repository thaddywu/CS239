# Final 20-Paper-Day Selection Audit

This audit records the re-ranking used for `syllabus/reading-list-draft.md`. It is a selection decision over the existing corpus, not a new literature-search round. The decisive test was whether removing the paper would remove a non-obvious mechanism or an important counterfactual from the course.

## Selection constraints

- Exactly 20 primary paper days, with one primary paper per day.
- The center of gravity is coding, validation, verification, memory reliability, and recovery.
- Multi-agent work must study topology, propagation, or fault containment rather than simulated job roles.
- Prompt-only orchestration, benchmark-only contributions, and retry loops without a stronger oracle do not qualify.
- Papers that share a task are retained together only when they expose a real architectural tension.
- MCP, A2A, Strands, ReAct, Toolformer, OpenHands, and selected classical principles remain tutorial/background material without consuming primary-paper days.

## Selected 20

| Paper | Mechanism that earns the day | Counterfactual or tension | Final role |
|---|---|---|---|
| SWE-agent | Agent-computer interface with bounded views, guarded editing, concise feedback, and history compression | Rich human shell versus an LM-specific constrained interface | Interface anchor |
| CodeAct | Executable Python as a compositional action language with interpreter state and error feedback | Expressive universal action language versus narrow guarded commands | Interface counterpoint |
| Murakkab | Declarative workflow graph, profile-guided cross-layer optimizer, and adaptive serving runtime | Workflow policy inside prompts versus execution policy outside the model | Runtime/systems anchor |
| Understanding the Information Propagation Effects of Communication Topologies | CAPE interventions plus EIB-Learner for balancing insight and error diffusion | Dense access to information versus fault amplification | Multi-agent topology anchor |
| On the Resilience of LLM-Based Multi-Agent Collaboration with Faulty Agents | Controlled fault injection plus Challenger and Inspector mechanisms | Topology alone versus explicit fault containment | Multi-agent reliability anchor |
| AutoCodeRover | Program-structure-guided context search and iterative patch/test loop | Repository analysis versus generic file browsing | Repair architecture |
| Demystifying LLM-based Software Engineering Agents | Fixed localization, repair, and validation phases | Open-ended autonomy versus a cheap deterministic pipeline | Essential control condition |
| CodePlan | Incrementally updated edit-obligation DAG grounded in dependency and impact analysis | Planning as text versus planning over code semantics | Repository-scale planning |
| IRIS | LLM-mined taint specifications compiled into whole-program CodeQL analysis | Semantic flexibility versus sound reachability machinery | Program-analysis anchor |
| CodaMOSA | Search-based testing with LLM intervention only at coverage plateaus | Model-only generation versus algorithmically governed hybrid search | Testing anchor |
| ImpossibleBench | Deliberately conflicting specifications and tests that make every pass evidence of exploitation | Tests as oracle versus tests as a hackable proxy | Oracle critique |
| PropertyGPT | Retrieval, compiler/static feedback, property ranking, and a dedicated prover | Example tests versus durable executable properties | Specification generation |
| LeanDojo | Instrumented proof environment, scoped-premise retrieval, tactic execution, and kernel checking | Fluent proof text versus typed state and unforgeable validation | Formal-runtime anchor |
| PAT-Agent | Planned autoformalization with model-checker counterexamples driving bounded repair | Checker-certified consistency versus faithfulness to informal intent | Model-checking anchor |
| Agentic Memory | Memory operations as first-class actions learned with staged RL and step-wise GRPO | Fixed memory heuristics versus an end-to-end learned state policy | Constructive memory reading |
| How Memory Management Impacts LLM Agents | Controlled addition/deletion experiments exposing experience-following and delayed error propagation | More remembered experience versus higher-quality governed state | Memory negative result |
| Microreboot | Fine-grained restart enabled by component boundaries and separation of transient from durable state | Retry as a behavior versus recovery as a system abstraction | Classical recovery bridge |
| Solving olympiad geometry without human demonstrations | Learned exogenous-term proposals coupled to symbolic deductive closure | End-to-end generation versus a narrow neural-symbolic responsibility split | Application case |
| Defeating Prompt Injections by Design | Trusted planning, quarantined data interpretation, provenance/capability tracking, and policy enforcement | Prompt compliance versus security by construction | Information-flow security |
| AgentSpec | External policy DSL and runtime monitor over agent actions and traces | Generated safety advice versus independently enforced rules | Runtime-governance synthesis |

## Near misses and deliberate exclusions

| Paper | Why it is good | Why it did not receive one of the 20 days |
|---|---|---|
| Toolformer | Its loss-based self-labeling of useful API call sites is technically real. | The selected interface/runtime sequence is more directly about software-engineering control boundaries; Toolformer remains tutorial background. |
| LLMs Can't Plan, But Can Help Planning in LLM-Modulo Frameworks | It supplies the course's clearest responsibility-allocation thesis. | It is a position paper rather than a standalone evaluated mechanism; the selected systems instantiate and test its thesis. |
| RepairAgent | Its finite-state repair protocol is more structured than a generic shell loop. | AutoCodeRover and Agentless form the sharper analysis-guided versus fixed-pipeline comparison, and a third repair system would be incremental. |
| Agentic Specification Generator for Move Programs | It has a strong compiler/prover-feedback pipeline and a useful all-in-one ablation. | PropertyGPT and PAT-Agent cover specification generation and autoformalization with broader conceptual separation; this would be the first replacement if a domain-specific day is needed. |
| LEGO-Prover | A verified, growing skill library is a powerful form of typed agent memory. | It overlaps the formal-verification block, while Agentic Memory plus the memory-impact paper provides the cleaner constructive/negative state-management pair. Use LEGO-Prover as background in both blocks. |
| Draft, Sketch, and Prove | The formal sketch is an excellent intermediate contract between informal reasoning and automation. | LeanDojo and PAT-Agent already consume the formal-methods slots and cover environment design plus counterexample-guided repair. |
| Large Language Models Cannot Self-Correct Reasoning Yet | It is the strongest warning against intrinsic verbal self-correction. | The point is embedded across ImpossibleBench, memory failure, and the document review; a full day would displace a mechanism paper. |
| CRITIC | It correctly introduces external evidence into revision. | External-evidence loops are implemented with stronger software/formal machinery by IRIS, LeanDojo, PAT-Agent, and AgentSpec. |
| ACE | Its planner/executor separation and information-flow analysis are technically strong. | It is most redundant with CaMeL; CaMeL provides the sharper capability/provenance design for the single information-flow day. |
| SAGA | It fills the important identity, discovery, delegation, and cryptographic authorization gap. | The final safety pair prioritizes information-flow confinement and general runtime policy; SAGA is required background for the Document Review II design exercise. |
| G-Designer | It learns sparse task-dependent communication graphs. | The information-propagation paper explains why graph structure matters and provides the stronger causal object; selecting both would over-cluster topology optimization. |
| AgentDojo | It provides concrete dynamic attacks and a useful security environment. | It is primarily an evaluation environment; CaMeL supplies the defense mechanism and can use AgentDojo results as evidence. |
| SemRef | It is a genuine semantic-plus-structural architecture-recovery system. | One current system does not yet support a mature standalone topic, and its final proceedings/DOI status was still less settled during the audit. |
| Software Reflexion Models | It defines a falsifiable mapping between intended architecture and source dependencies. | It remains a short conceptual background reading for CodePlan rather than displacing an agent-centered primary day. |
| QuickCheck | It is the cleanest foundation for executable properties and generators. | PropertyGPT addresses the current agent-SE question directly; QuickCheck should frame discussion, not replace it. |
| OpenHands | It is important infrastructure with a broad sandbox/runtime artifact. | Its breadth makes mechanism attribution weaker than SWE-agent and Murakkab. |
| Coscientist | Physical execution makes authority and safety concrete. | The integrated demonstration does not isolate a broadly reusable agent mechanism as cleanly as AlphaGeometry. |
| MLAgentBench | It offers reproducible long-horizon ML experimentation tasks. | It is a benchmark rather than a new architecture or verification mechanism. |
| ReAct, Reflexion, MetaGPT, ChatDev, CAMEL | They are historically influential vocabulary and framework examples. | The central mechanisms are prompt-level, retry-centric, or role-centric, and fail the final technical bar as primary readings. |

## Redundancy audit

- **Interfaces:** SWE-agent and CodeAct remain together because they make opposite, testable choices about action-space expressiveness.
- **Multi-agent:** the topology paper studies causal propagation; the resilience paper injects faults and tests containment. Neither is a role-playing framework.
- **Repair:** AutoCodeRover contributes program-structure-guided search; Agentless is the matched autonomy counterfactual; CodePlan handles propagating multi-file edit obligations.
- **Validation:** CodaMOSA governs input search, ImpossibleBench attacks oracle authority, and PropertyGPT creates durable specifications. They are not three benchmark-score variants.
- **Formal methods:** LeanDojo designs a typed interaction environment; PAT-Agent studies natural-language-to-model translation and counterexample-guided repair.
- **Memory/recovery:** Agentic Memory learns state actions, the empirical memory paper diagnoses delayed contamination, and Microreboot supplies an explicit recovery abstraction absent from both.
- **Safety:** CaMeL enforces provenance-sensitive information flow by construction; AgentSpec enforces domain policies over runtime events.

## Remaining gaps after selection

No selected primary paper fully solves transactional tool execution, semantic rollback of external side effects, provenance-aware invalidation across shared multi-agent memory, or revocation across open agent ecosystems. Those gaps are intentional prompts for the two Document Review sessions rather than justification for adding weaker papers.
