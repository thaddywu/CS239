# Theme: Interfaces, Runtimes, and Coordination

## Core question

Which responsibilities belong in the model, the action interface, the workflow runtime, and the collaboration protocol?

## Why this theme matters

An agent is not just a model with a prompt: its observable state, permitted actions, execution substrate, and communication graph shape both capability and failure. These papers establish those layers through competing abstractions rather than framework tutorials.

## Paper Day 1 — The agent-computer interface is part of the algorithm

### Paper

**SWE-agent: Agent-Computer Interfaces Enable Automated Software Engineering**

Venue: NeurIPS 2024, Main Conference Track (peer-reviewed conference paper)

Authors: John Yang; Carlos E. Jimenez; Alexander Wettig; Kilian Lieret; Shunyu Yao; Karthik Narasimhan; Ofir Press

Author institutions:

- Princeton Language and Intelligence, Princeton University

Notable / established authors or group:

The paper comes from Princeton Language and Intelligence, the group that also produced SWE-bench; the connection matters because the interface is evaluated against the repository-level task the group helped define.

### What problem does this paper solve?

Repository-repair agents are often evaluated as if the language model alone determines success, even though the model acts through an interface inherited from a shell and editor designed for people. That interface can flood context with irrelevant output, make navigation expensive, admit malformed edits, and conceal useful failure signals. SWE-agent asks whether an agent-computer interface should be deliberately designed around a model's perceptual and action limitations. The deeper problem is causal attribution: if command design and observation policy materially change outcomes, a benchmark score is not simply a measure of model intelligence.

### Technical core

SWE-agent exposes a compact repository action space for search, bounded file viewing, line-oriented editing, and command execution. Observations are kept small, recent interaction is retained while older context is compressed, and failed actions return targeted feedback. The editor applies syntax-oriented checks so malformed changes are rejected before they poison later steps. Crucially, the paper ablates interface choices—including search presentation, viewing-window size, editor behavior, lint feedback, and history policy—while holding the broader task comparatively stable. The clever idea is to treat the ACI as an independently testable software artifact that controls information bandwidth and recoverability, not as incidental scaffolding around the model.

### Why it earns one of 20 slots

It gives the course a precise first systems object and a durable evaluation question: which failures belong to the model, and which were induced or prevented by the interface? Its design claims are concrete enough to inspect and ablate.

### Intellectual connection

CodeAct makes the opposite interface bet: replace a small guarded command vocabulary with one highly expressive executable language.

## Paper Day 2 — Expressiveness versus confinement in the action space

### Paper

**Executable Code Actions Elicit Better LLM Agents**

Venue: ICML 2024 (peer-reviewed conference paper)

Authors: Xingyao Wang; Yangyi Chen; Lifan Yuan; Yizhe Zhang; Yunzhu Li; Hao Peng; Heng Ji

Author institutions:

- University of Illinois Urbana-Champaign
- Apple

Notable / established authors or group:

The work joins UIUC language-and-agent researchers with Apple; members of the UIUC team subsequently contributed to the OpenHands software-agent platform.

### What problem does this paper solve?

Text and JSON tool schemas work for atomic calls but become awkward when a task needs loops, branching, intermediate variables, library composition, or revision after an exception. Every added tool enlarges a heterogeneous action vocabulary while orchestration remains implicit in generated text. CodeAct asks whether a programming language can instead serve as a single compositional action space. The problem is not syntax convenience alone: an action representation must preserve intermediate state, execute proposed operations, reveal concrete failures, and let the model revise from environmental evidence.

### Technical core

CodeAct lets the model emit executable Python interleaved with natural-language reasoning. A persistent interpreter retains variables and imported libraries, executes composed operations, and returns outputs or exceptions into the following turn. The paper compares this interface across seventeen models against text and JSON action formats, then separates interface effects from training effects with CodeActInstruct, a collection of roughly seven thousand multi-turn action trajectories used to fine-tune open models. The central abstraction is a stateful interpreter as the tool-composition layer: control flow and data flow become executable rather than narrated. That expressiveness is also its risk—one Python channel can hide broad ambient authority behind an apparently uniform action.

### Why it earns one of 20 slots

It contributes and isolates a non-obvious action-space abstraction. The comparison with SWE-agent supports a serious discussion of expressiveness, debuggability, least privilege, and where orchestration complexity should live.

### Intellectual connection

SWE-agent constrains individual actions; CodeAct makes them compositional. Murakkab moves up one level and treats the entire multi-component workflow as a program to optimize.

## Paper Day 3 — Treat the workflow graph as an optimizable program

### Paper

**Murakkab: Resource-Efficient Agentic Workflow Orchestration in Cloud Platforms**

Venue: 20th USENIX Symposium on Operating Systems Design and Implementation (OSDI 2026; peer-reviewed conference paper)

Authors: Gohar Irfan Chaudhry; Esha Choukse; Haoran Qiu; Íñigo Goiri; Rodrigo Fonseca; Adam Belay; Ricardo Bianchini

Author institutions:

- MIT Computer Science and Artificial Intelligence Laboratory
- Microsoft Azure Research
- Microsoft Azure

Notable / established authors or group:

The author team spans the MIT CSAIL systems group and Microsoft Azure/Azure Research; Adam Belay, Íñigo Goiri, Ricardo Bianchini, and their coauthors have sustained systems and cloud-computing publication records.

### What problem does this paper solve?

Agentic workflows combine model calls, tools, branches, and aggregation stages, yet common serving stacks see an opaque stream of requests. When control logic is coupled to fixed model and hardware choices, the platform cannot jointly trade accuracy, latency, energy, and cost across the workflow. Static deployments also become stale as load and service-level objectives change. Murakkab asks what representation a cloud system needs to optimize a workflow globally without asking the model to make resource-policy decisions.

### Technical core

Murakkab introduces a declarative workflow representation that separates logical control flow from concrete model, accelerator, batching, and execution choices. Offline profiling characterizes component alternatives; a cross-layer optimizer searches configurations that satisfy accuracy and systems objectives; and the runtime multiplexes resources and adapts configurations as load and SLOs change. The evaluation spans static workflows and a dynamic coding case, reporting substantial reductions in GPU use, energy, and cost while preserving target SLOs. The clever move is making workflow structure inspectable optimization input. The runtime can optimize or re-execute components, but it does not by itself define safe rollback for externally visible side effects.

### Why it earns one of 20 slots

It is a genuine systems paper: abstraction, optimizer, adaptive runtime, and measured trade-offs all survive the counterfactual removal of the word “agent.” It prevents the opening unit from collapsing into prompt and tool-interface design.

### Intellectual connection

Murakkab assumes a declared component graph. The next paper asks what happens when graph nodes are decision-makers that can inject and propagate faulty information.

## Paper Day 4 — Fault injection before claims of collaboration resilience

### Paper

**On the Resilience of LLM-Based Multi-Agent Collaboration with Faulty Agents**

Venue: ICML 2025 (peer-reviewed conference paper)

Authors: Jen-Tse Huang; Jiaxu Zhou; Tailin Jin; Xuhui Zhou; Zixi Chen; Wenxuan Wang; Youliang Yuan; Michael Lyu; Maarten Sap

Author institutions:

- The Chinese University of Hong Kong
- Tsinghua University
- Carnegie Mellon University
- Peking University
- Renmin University of China
- The Chinese University of Hong Kong, Shenzhen

Notable / established authors or group:

The cross-institution team includes Michael R. Lyu's software-engineering group and Maarten Sap's language-and-social-reasoning group. It is retained for its fault-injection design, not institutional preference.

### What problem does this paper solve?

Multi-agent systems can look effective when every component is cooperative and similarly capable, but deployment must tolerate a node that is incompetent, corrupted, or malicious. Role-playing demonstrations rarely specify a fault model or distinguish a single-node failure from common model error. This paper asks how linear, flat, and hierarchical collaboration structures degrade under controlled faulty responses and whether explicit contest and inspection steps actually recover performance.

### Technical core

AutoTransform and AutoInject construct faulty agent responses, enabling controlled comparisons across six systems and three structural families on code generation, mathematics, translation, and evaluation. A hierarchical pattern, `A -> (B <-> C)`, shows a smaller reported degradation than linear and flat patterns. Challenger modifies the protocol so agents can contest a message; Inspector adds a reviewing node that identifies and corrects suspicious outputs. Selected configurations recover up to 96.4% of injected errors. The important contribution is experimental fault injection tied to communication structure and remediation, not the occupational labels assigned to agents. Synthetic faults and model-correlated reviewers remain important limitations.

### Why it earns one of 20 slots

It forces multi-agent architecture to make a falsifiable resilience claim. No comparably mature preferred-group alternative found in the targeted pass combines controlled fault generation, topology comparison, and measured mitigation.

### Intellectual connection

The opening theme ends by distinguishing message-level containment from the much harder problem encountered later: undoing committed tool actions and corrupted persistent state.

# Theme: Repository-Scale Reasoning and Software Structure

## Core question

Which software representations let a model find, plan, change, and validate repository-scale behavior without mistaking retrieval for understanding?

## Why this theme matters

Repository work exposes where generic agent loops stop being enough. The readings pit exploratory autonomy against staged pipelines, then introduce edit-dependency graphs, static dataflow, and explicit architecture hypotheses as stronger sources of structure.

## Paper Day 5 — Program structure as the search policy

### Paper

**AutoCodeRover: Autonomous Program Improvement**

Venue: ISSTA 2024 (peer-reviewed conference paper)

Authors: Yuntong Zhang; Haifeng Ruan; Zhiyu Fan; Abhik Roychoudhury

Author institutions:

- National University of Singapore

Notable / established authors or group:

The paper comes from Abhik Roychoudhury's software-engineering research group, with a sustained program-repair and program-analysis publication record.

### What problem does this paper solve?

Issue-resolution agents must locate a small fault-relevant slice inside repositories far too large for one context window. Generic shell exploration and lexical retrieval waste budget on unrelated files, while one-shot patching cannot use execution evidence. AutoCodeRover frames localization and repair as a program-improvement workflow grounded in software entities. It must infer likely classes and methods, expand context through relationships, propose a patch, and revise after tests fail.

### Technical core

AutoCodeRover exposes repository search operations over classes, methods, snippets, and related definitions, allowing a model's current hypothesis to drive structure-aware context acquisition. Its workflow combines AST-aware navigation, iterative context expansion, and—in the evaluated repair setting—spectrum-based fault-localization evidence, followed by patch construction and test-guided revision. The mechanism is a software-specific search policy rather than unrestricted browsing. The evaluation shows useful issue-resolution performance at low reported cost, but tests remain the acceptance oracle, so passing does not establish requirement fidelity or protect against overfitting.

### Why it earns one of 20 slots

It is a compact example of program analysis changing an agent's trajectory rather than serving only as post-hoc context. Its limitations also set up the next paper's challenge to open-ended autonomy.

### Intellectual connection

Agentless keeps the repository task but replaces the exploratory loop with fixed localization, repair, and validation phases.

## Paper Day 6 — Is open-ended autonomy necessary for repair?

### Paper

**Demystifying LLM-based Software Engineering Agents**

Venue: ACM FSE 2025 (peer-reviewed conference paper)

Authors: Chunqiu Steven Xia; Yinlin Deng; Soren Dunn; Lingming Zhang

Author institutions:

- University of Illinois Urbana-Champaign

Notable / established authors or group:

The paper comes from Lingming Zhang's UIUC software-engineering group, which has a sustained record in testing, debugging, and automated repair.

### What problem does this paper solve?

Complex coding agents bundle planning, navigation, repeated model calls, editing, and validation, making it difficult to tell whether open-ended autonomy causes the reported gains. The paper asks a strong control question: how far can a deliberately simple, non-agentic pipeline go when localization, repair, and validation are structured well? This matters because unnecessary autonomy increases cost, variance, debugging difficulty, and authority without proving that adaptive control is the useful ingredient.

### Technical core

Agentless divides repair into three deterministic phases. Localization narrows from files to classes/functions and then edit locations; repair produces several candidate patches within that context; validation normalizes, deduplicates, and ranks plausible patches using the available tests. The model supplies semantic proposals, but software fixes the phase order and constrains the information passed between them. The paper evaluates this pipeline on SWE-bench and reports competitive results at substantially lower cost than many agent systems. Its cleverness is methodological and architectural: it supplies a strong structured baseline that makes “the agent loop” an experimental variable rather than an assumption.

### Why it earns one of 20 slots

Graduate students need a credible negative control against autonomy claims. The paper teaches that workflow decomposition can be more important than giving a model broad control, while leaving room for tasks whose plans truly must change.

### Intellectual connection

CodePlan identifies such a case: multi-file edits reveal new obligations, so the plan must evolve from program dependencies after each change.

## Paper Day 7 — Planning as a changing graph of edit obligations

### Paper

**CodePlan: Repository-level Coding using LLMs and Planning**

Venue: ACM FSE 2024 (peer-reviewed conference paper)

Authors: Ramakrishna Bairi; Atharv Sonwane; Aditya Kanade; Vageesh D. C.; Arun Iyer; Suresh Parthasarathy; Sriram Rajamani; B. Ashok; Shashank Shet

Author institutions:

- Microsoft Research India

Notable / established authors or group:

The author team is from Microsoft Research India and includes researchers with established programming-languages, verification, and software-engineering work, including Sriram Rajamani and Aditya Kanade.

### What problem does this paper solve?

Repository-level tasks often require coordinated edits across callers, interfaces, configuration, and tests. A plan written once from the issue text misses dependencies revealed only after an edit changes a symbol or contract. Purely reactive browsing, however, can lose the global obligation structure. CodePlan asks how planning can remain explicit while being revised by facts derived from the changing program.

### Technical core

CodePlan represents work as a graph of edit obligations. It uses static dependency analysis and typed change-may-impact relations to identify entities potentially affected by a proposed change. After an edit, the planner expands or revises the graph rather than merely appending another language-model thought. Execution and validation proceed against this evolving plan until obligations are discharged. The technical insight is that planning state should be an explicit, inspectable artifact whose transitions are driven by program relations. The model proposes semantic changes; dependency analysis supplies reachability and impact that the model is poor at maintaining over many files.

### Why it earns one of 20 slots

This is the strongest repository-planning mechanism in the corpus and is intellectually distinct from both open-ended repair and a fixed pipeline. It also introduces explicit state that later correctness readings can ask to validate, persist, or invalidate.

### Intellectual connection

CodePlan uses structure to decide what else may need editing. IRIS uses structure to decide whether a security-relevant flow can actually exist across the repository.

## Paper Day 8 — Let the model propose semantics, not reachability

### Paper

**IRIS: LLM-Assisted Static Analysis for Detecting Security Vulnerabilities**

Venue: ICLR 2025 (peer-reviewed conference paper)

Authors: Ziyang Li; Saikat Dutta; Mayur Naik

Author institutions:

- University of Pennsylvania
- Cornell University

Notable / established authors or group:

The paper is associated with Mayur Naik's program-analysis group at Penn; the author block also lists Cornell for Saikat Dutta.

### What problem does this paper solve?

Static taint analysis can trace flows across huge programs but depends on manually maintained source, sink, and sanitizer specifications and often produces imprecise alerts. Language models can infer API meaning and read local context, but they are unreliable at exhaustive whole-program reachability. IRIS asks how to assign each component the part it can do well without asking either to solve the entire vulnerability-detection problem.

### Technical core

IRIS extracts candidate external APIs and internal parameters, asks an LLM to label vulnerability-specific sources and sinks, converts those labels into CodeQL specifications, and runs interprocedural static taint analysis. A second model stage receives the source, sink, intermediate path, and surrounding code to filter contextually implausible alerts. On CWE-Bench-Java's 120 vetted vulnerabilities, the reported best configuration detects 55 versus CodeQL's 27 while slightly lowering average false-discovery rate, and it finds four previously unknown vulnerabilities in current projects. The clever division is semantic proposal by the model and graph reachability by a static analyzer, although LLM-supplied specifications and filtering can still introduce false negatives.

### Why it earns one of 20 slots

It is a clear neuro-symbolic software-analysis architecture with a repository-scale evaluator and real discoveries. The technical contribution remains meaningful without the “agent” label.

### Intellectual connection

IRIS recovers one kind of implicit structure—dataflow—against a fixed formal model. Software Reflexion Models asks how an engineer can posit and falsify a higher-level architectural structure not directly present in code.

## Paper Day 9 — Architecture recovery as hypothesis testing

### Paper

**Software Reflexion Models: Bridging the Gap Between Source and High-Level Models**

Venue: Third ACM SIGSOFT Symposium on Foundations of Software Engineering, 1995 (peer-reviewed conference paper)

Authors: Gail C. Murphy; David Notkin; Kevin J. Sullivan

Author institutions:

- University of Washington
- University of Virginia

Notable / established authors or group:

This is foundational work from the University of Washington and University of Virginia software-architecture and program-understanding lineage. The publication affiliation lists Murphy and Notkin at Washington and Sullivan at Virginia.

### What problem does this paper solve?

Large systems do not contain a single authoritative diagram of their architecture, and code browsing or clustering alone cannot decide which structural relationships matter for a task. An engineer usually has a partial mental model that may be wrong. The paper asks how to turn that model into a falsifiable lens over source rather than either accepting it as documentation or replacing it with an opaque recovered clustering.

### Technical core

The engineer defines a high-level model and maps source entities onto its components. A source-model extractor derives relations such as calls or dependencies; the tool lifts those relations through the mapping and compares them with the hypothesized architecture. The resulting reflexion model classifies edges as convergence (expected and present), divergence (present but unexpected), or absence (expected but missing). The engineer iteratively changes the model or mapping in response. The paper formalizes this computation and reports applications including a 250-KLOC NetBSD subsystem and Microsoft Excel. Its cleverness is the explicit discrepancy artifact: architecture recovery becomes iterative hypothesis testing, not automatic summarization.

### Why it earns one of 20 slots

No modern agent paper inspected in this pass replaces this abstraction with equally strong evidence. Its age is a strength here: it states what repo graphs and LLM summaries still fail to do—compare intended structure with implementation evidence.

### Intellectual connection

The repository theme ends by distinguishing retrieved context from a checkable model. The next theme asks the analogous question for behavior: what makes a test or formal statement an adequate specification?

# Theme: Testing, Specifications, and Mechanized Proof

## Core question

How should probabilistic proposals interact with search, executable tests, formal contracts, proof states, and uncompromising checkers?

## Why this theme matters

Feedback is useful only if its authority and semantics are understood. These papers progress from hybrid test generation, through deliberate test/specification conflict, to generated contracts and proof-assistant environments where validation is exact but specification faithfulness remains open.

## Paper Day 10 — Invoke generation when algorithmic search stalls

### Paper

**CodaMOSA: Escaping Coverage Plateaus in Test Generation with Pre-trained Large Language Models**

Venue: ICSE 2023 (peer-reviewed conference paper)

Authors: Caroline Lemieux; Jeevana Priya Inala; Shuvendu K. Lahiri; Siddhartha Sen

Author institutions:

- University of British Columbia
- Microsoft Research

Notable / established authors or group:

The paper joins UBC software-engineering research with Microsoft Research's programming-languages, verification, and systems community.

### What problem does this paper solve?

Search-based unit-test generation exploits concrete coverage feedback but can plateau when useful inputs require semantic knowledge unavailable to mutation. Language models can propose plausible tests but waste calls, hallucinate APIs, and lack a disciplined stopping condition. CodaMOSA asks when a learned generator should intervene in an algorithmic search and how its proposals should return to that search rather than replacing it.

### Technical core

CodaMOSA extends MOSA, a many-objective search algorithm, with a stagnation detector. Evolutionary search runs normally until coverage stops improving; only then does a language model generate candidate tests for under-covered functions. Compilable proposals seed the population, after which ordinary mutation, selection, execution, and coverage measurement resume. This creates a closed hybrid loop: symbolic/executable feedback decides when the model is needed and whether its output is useful. The evaluation shows gains over both search-only and model-only alternatives. A targeted 2024–2026 testing search found richer GUI and iterative generators, but none isolated this division of labor as cleanly.

### Why it earns one of 20 slots

CodaMOSA re-earned its slot because recency did not reveal a deeper replacement. It teaches a reusable pattern: call a probabilistic proposer at a measurable search bottleneck, then return control to an algorithm with an external fitness signal.

### Intellectual connection

Its loop treats coverage and tests as reliable objectives. ImpossibleBench deliberately breaks that assumption and shows how the same feedback can reward specification violation.

## Paper Day 11 — When passing tests proves the agent is wrong

### Paper

**ImpossibleBench: Measuring LLMs' Propensity of Exploiting Test Cases**

Venue: ICLR 2026 (peer-reviewed conference paper)

Authors: Ziqian Zhong; Aditi Raghunathan; Nicholas Carlini

Author institutions:

- Carnegie Mellon University
- Anthropic

Notable / established authors or group:

The work comes from CMU and Anthropic; Aditi Raghunathan and Nicholas Carlini have established research records in robustness and security.

### What problem does this paper solve?

Coding systems optimize test pass rates even when tests are incomplete, stale, or inconsistent with natural-language intent. On an ordinary benchmark, a high score cannot distinguish a correct repair from deleting a test, special-casing inputs, or exploiting the harness. ImpossibleBench asks how to create unambiguous ground truth for this failure: can a benchmark make every successful run evidence that the system violated the stated specification?

### Technical core

The framework derives impossible variants of LiveCodeBench and SWE-bench by mutating or duplicating test expectations so they conflict directly with the task specification. It validates SWE-bench mutations against both original and empty patches, then defines the pass rate on impossible tasks as a cheating rate. Controlled variants alter prompt strictness, test visibility and writability, feedback rounds, and the availability of a human-escalation exit. The paper catalogs direct test edits, operator overloading, state recording, and special-casing; it also uses the resulting transcripts to evaluate monitors. The central idea is a counterfactual oracle in which proxy optimization and intended correctness point in opposite directions.

### Why it earns one of 20 slots

It changes how every earlier coding result should be interpreted and gives specification gaming a measurable experimental design. It is more than a benchmark leaderboard because it creates a diagnostic intervention over validator authority.

### Intellectual connection

ImpossibleBench shows that tests are fallible proxies. MSG raises the abstraction to preconditions, postconditions, modifies clauses, abort conditions, and invariants checked by a formal toolchain.

## Paper Day 12 — Divide specification generation by formal obligation

### Paper

**Agentic Specification Generator for Move Programs**

Venue: ASE 2025 (peer-reviewed conference paper)

Authors: Yu-Fu Fu; Meng Xu; Taesoo Kim

Author institutions:

- Georgia Institute of Technology
- University of Waterloo

Notable / established authors or group:

The paper comes from Georgia Tech's systems-security group led by Taesoo Kim and from the University of Waterloo; the official ASE record verifies these affiliations.

### What problem does this paper solve?

Formal verification of Move contracts depends on specifications that are expensive to write and whose clause types require different reasoning. A one-shot generator must simultaneously infer abort behavior, state modification, postconditions, and loop invariants while coping with facts hidden inside callees. MSG asks whether specification generation becomes more reliable when formal obligations are separated and program analysis exposes only the necessary interprocedural facts.

### Technical core

MSG assigns `aborts_if`, `modifies`, `ensures`, and loop-invariant clauses to specialized generators, ensembles their outputs, and repairs candidates using compiler and Move Prover diagnostics. Selective function inlining exposes relevant callee behavior without blindly expanding the whole call graph. On 357 Move functions, it reports verifiable specifications for 300 (84%) and loop invariants for 14 of 17 functions that need them. The specialized architecture reaches 84% function coverage versus 53.5% for an all-in-one design, while removing prover feedback lowers coverage to 70.9%. The reusable artifact is a checked contract, although verifier acceptance cannot prove that all intended requirements were included.

### Why it earns one of 20 slots

It combines specialization, selective static analysis, formal-language generation, and prover-guided repair in one inspectable architecture. It beats PropertyGPT for this slot by exposing clearer clause-specific roles and ablations while retaining reusable formal artifacts.

### Intellectual connection

MSG generates the specification consumed by a verifier. LeanDojo instead exposes the verifier's exact evolving proof state as the agent's execution environment.

## Paper Day 13 — A proof assistant as an agent runtime

### Paper

**LeanDojo: Theorem Proving with Retrieval-Augmented Language Models**

Venue: NeurIPS 2023, Datasets and Benchmarks Track (peer-reviewed conference paper)

Authors: Kaiyu Yang; Aidan Swope; Alex Gu; Rahul Chalamala; Peiyang Song; Shixing Yu; Saad Godil; Ryan J. Prenger; Animashree Anandkumar

Author institutions:

- California Institute of Technology
- NVIDIA
- Massachusetts Institute of Technology
- University of California, Santa Barbara
- The University of Texas at Austin

Notable / established authors or group:

The cross-institution team includes Animashree Anandkumar's Caltech/NVIDIA research group and collaborators from MIT, UCSB, and UT Austin.

### What problem does this paper solve?

Learning-based theorem provers need more than final proof text. They require exact proof states, legal actions, dependency-scoped premises, reproducible environments, and evaluation splits that do not reward memorized library usage. LeanDojo asks how to turn Lean into a programmatic environment for training and executing proof agents while making large-library premise selection an explicit technical problem.

### Technical core

LeanDojo instruments Lean repositories to extract syntax, proof states, tactic traces, dependencies, source locations, and fine-grained premise use. An interactive API accepts tactics and returns kernel-grounded successor states or errors. ReProver trains a retriever with accessible premises and in-file hard negatives, conditions tactic generation on those premises, and uses best-first search to assemble proofs. The benchmark contains 98,734 theorems, 217,776 tactics, and roughly 130,000 premises, including a novel-premises split. The cleverness lies in the environment contract: typed state, scoped resources, executable actions, and a checker that the model cannot persuade.

### Why it earns one of 20 slots

It is both a theorem-proving mechanism and a reference architecture for agent runtimes. Students can identify exactly which proof-assistant properties ordinary coding harnesses lack.

### Intellectual connection

LeanDojo searches directly in exact proof state. Draft, Sketch, and Prove inserts a structured, partially formal artifact between informal reasoning and local proof search.

## Paper Day 14 — Formal sketches as contracts between uncertain and exact reasoning

### Paper

**Draft, Sketch, and Prove: Guiding Formal Theorem Provers with Informal Proofs**

Venue: ICLR 2023 (peer-reviewed conference paper)

Authors: Albert Q. Jiang; Sean Welleck; Jin Peng Zhou; Wenda Li; Jiacheng Liu; Mateja Jamnik; Timothée Lacroix; Guillaume Lample; Yuhuai Wu

Author institutions:

- Meta AI
- University of Cambridge
- University of Washington
- Allen Institute for AI
- Google Research
- Cornell University
- Stanford University

Notable / established authors or group:

The paper combines established theorem-proving and language-model researchers across Meta AI, Cambridge, Washington, AI2, Google Research, Cornell, and Stanford.

### What problem does this paper solve?

Direct formal-proof generation forces one model output to contain both the mathematical idea and every proof-assistant detail. Search-only provers, in contrast, receive no global guidance from an available informal argument. DSP asks how an informal proof can constrain formal search without being mistaken for verified evidence. The true design problem is an interface between uncertain global reasoning and exact local discharge.

### Technical core

DSP takes a human-written or model-generated informal draft, translates its structure into a formal sketch with explicit holes, and delegates each hole to an off-the-shelf prover under the surrounding formal context. The proof assistant accepts only the fully discharged result. This decomposition turns one brittle generation problem into global outline production plus several smaller search obligations, and it localizes failures to the draft, sketch translation, or hole prover. On its main miniF2F setting the paper reports improvement from 20.9% to 39.3% and studies both human and generated drafts. A correct theorem statement is assumed; checking the proof does not establish that the theorem faithfully formalizes the original intent.

### Why it earns one of 20 slots

The formal sketch is a clean intermediate representation with a real semantic role, not a narrated chain of thought. It adds a distinct neural-symbolic composition to MSG's generated contracts and LeanDojo's state-space search.

### Intellectual connection

The formal block ends with exact checking and an unresolved intent boundary. The final theme asks what happens when decisions leave the checker and mutate an external world that may not be reversible.

# Theme: Correctness after Decisions Become Actions

## Core question

What does correctness require when a probabilistic planner interprets intent, acts on mutable state, holds authority, creates external effects, retries, and sometimes must transfer control to a person?

## Why this theme matters

Ordinary middleware assumes that programmers encode sequencing, transactions, authorization, and error handling. Agent-leveraged applications move some of those decisions into model behavior. The six readings supply distinct mechanisms for compensation, transactional replay, human escalation, information-flow control, delegated authority, and runtime enforcement.

## Paper Day 15 — Compensation is not rollback

### Paper

**Sagas**

Venue: ACM SIGMOD 1987 (peer-reviewed conference paper)

Authors: Hector Garcia-Molina; Kenneth Salem

Author institutions:

- Princeton University

Notable / established authors or group:

The publication affiliation is Princeton's database group. Hector Garcia-Molina and Kenneth Salem established the saga abstraction in this paper; the selection rests on that durable transaction model.

### What problem does this paper solve?

A long-lived transaction cannot hold locks for hours while waiting on people, services, or physical work, yet treating each step as unrelated can strand the system after partial completion. This is exactly the structure of many tool-using agent tasks: several actions commit before a later action fails. The paper asks which guarantees remain possible when global isolation and atomic rollback are deliberately relaxed.

### Technical core

A saga is an ordered sequence of independently committed, consistency-preserving transactions `T1 … Tn`. For each step, the application may define a semantic compensation `Ci`. If execution stops after `Tj`, backward recovery runs compensations in reverse order; if remaining work is guaranteed to finish, forward recovery continues the sequence. The system persistently records saga code, compensation metadata, savepoints, and progress, and the paper extends ordering rules to parallel sagas. A compensation need not restore an old physical state: it must semantically amend the action while respecting intervening work. Therefore other transactions may have observed results that are later compensated, and some effects—such as firing a missile—cannot be undone.

### Why it earns one of 20 slots

Modern agent papers frequently say “retry” or “rollback” without distinguishing forward recovery, semantic compensation, and impossible reversal. This paper supplies the missing abstraction more directly than Microreboot.

### Intellectual connection

Sagas permits visible intermediate commits and repairs them. Beldi explores the opposite design point: keep mediated stateful workflow execution inside an exactly-once transactional boundary.

## Paper Day 16 — Durable retry needs identifiers, logs, and isolation

### Paper

**Fault-tolerant and transactional stateful serverless workflows**

Venue: 14th USENIX Symposium on Operating Systems Design and Implementation (OSDI 2020; peer-reviewed conference paper)

Authors: Haoran Zhang; Adney Cardoza; Peter Baile Chen; Sebastian Angel; Vincent Liu

Author institutions:

- University of Pennsylvania
- Rutgers University–Camden

Notable / established authors or group:

The paper comes from systems and security researchers at Penn and Rutgers; the official USENIX record lists each publication affiliation.

### What problem does this paper solve?

Serverless platforms may retry a function whose earlier attempt already wrote data or invoked another function. Stateless retry advice is insufficient once workflows own durable state, and ordinary transaction managers do not fit a federated setting where each function controls its data. Beldi asks how to give such workflows exactly-once and transactional semantics while running on existing cloud providers.

### Technical core

Beldi wraps reads, writes, conditional writes, and function invocations with atomic intent logging and re-execution. An intent collector completes interrupted operations, while the linked DAAL structure co-locates application data and log history over a strongly consistent NoSQL substrate. Invocation identifiers and recorded outcomes prevent completed calls from being duplicated during replay. For multi-function transactions, Beldi provides opacity using two-phase locking, wait-die deadlock prevention, shadow records, and commit/abort propagation through the invocation graph. Three applications and experiments up to 1,000 AWS Lambdas demonstrate consistency and quantify overhead. Its boundary excludes arbitrary opaque external effects—the point where Sagas becomes necessary.

### Why it earns one of 20 slots

It makes state, retry, invocation, isolation, and crash recovery part of a concrete workflow runtime. Compared with Microreboot, it is closer to the partial-execution problem and more explicit about exactly-once effects.

### Intellectual connection

Beldi can guarantee behavior only for mediated operations. The next paper addresses a different uncertainty: whether control should remain autonomous or move to a person or another agent before an action is chosen.

## Paper Day 17 — Human oversight as a sequential control policy

### Paper

**Towards Adjustable Autonomy for the Real World**

Venue: Journal of Artificial Intelligence Research 17, 2002 (peer-reviewed journal article)

Authors: Paul Scerri; David V. Pynadath; Milind Tambe

Author institutions:

- Information Sciences Institute, University of Southern California
- Computer Science Department, University of Southern California

Notable / established authors or group:

The paper is from USC/ISI's TEAMCORE multi-agent research group led by Milind Tambe; the Electric Elves deployment provides the empirical setting.

### What problem does this paper solve?

“Ask a human when uncertain” ignores whether the person will respond, how long the team can wait, and what coordination failures the delay creates. Always acting autonomously can produce bad decisions; always transferring control can also be wrong. The paper asks how an agent should plan control transfer when decision quality, response probability, time, and team cost are all uncertain.

### Technical core

A transfer-of-control strategy is a conditional sequence of actions that give decision authority to agents or people, interleaved with `D` actions that change coordination constraints to buy time. A mathematical model computes expected utility from decision quality, response probability, wait cost, and miscoordination; a Markov decision process operationalizes the choice over strategies. User constraints can forbid or require actions in selected states. Electric Elves ran continuously for roughly seven months with ten users and monitored nearly 700 meetings; strategy and parameter-sweep experiments show that multi-step transfer is often optimal and that policies respond nontrivially to coordination costs. The approach still relies on estimated utilities and treats one isolated decision at a time.

### Why it earns one of 20 slots

It is a technically concrete HCI and multi-agent reading: escalation becomes a planned, costed action rather than a safety slogan. It also exposes privacy, security, and behavioral adaptation observed in deployment.

### Intellectual connection

Adjustable autonomy decides who should control a decision. CaMeL constrains which information may influence privileged control even when the model remains the decision-maker.

## Paper Day 18 — Separate trusted control from untrusted data

### Paper

**Defeating Prompt Injections by Design**

Venue: IEEE Conference on Secure and Trustworthy Machine Learning (SaTML) 2026 (peer-reviewed conference paper)

Authors: Edoardo Debenedetti; Ilia Shumailov; Tianqi Fan; Jamie Hayes; Nicholas Carlini; Daniel Fabian; Christoph Kern; Chongyang Shi; Andreas Terzis; Florian Tramèr

Author institutions:

- Google
- Google DeepMind
- ETH Zurich

Notable / established authors or group:

The author team spans Google, Google DeepMind, and ETH Zurich security researchers, including Nicholas Carlini and Florian Tramèr.

### What problem does this paper solve?

Tool outputs and retrieved documents are simultaneously useful data and adversarial instruction channels. Prompt filtering asks a probabilistic model to distinguish the two after they have already been mixed. CaMeL asks whether the application can instead prevent untrusted observations from gaining control authority by construction, while still allowing their values to flow into legitimate tool arguments.

### Technical core

CaMeL separates a privileged control plane from a quarantined data plane. A trusted model produces a plan over typed capabilities without reading untrusted content; a less-trusted model may transform data within that plan but cannot change control structure or independently acquire capabilities. The runtime tracks provenance and capability labels through values, applies security policies when privileged actions are requested, and mediates tool execution. Evaluation on AgentDojo measures both attack resistance and benign task utility. The design changes prompt injection from “recognize malicious words” into an information-flow and authority problem, though policy completeness, covert channels, and unsupported tool behavior remain in the trusted computing base.

### Why it earns one of 20 slots

It is the strongest construction-based security mechanism in the corpus and is clearly more than another detector or adversarial benchmark. Its abstractions connect programming languages, capability security, and agent architecture.

### Intellectual connection

CaMeL controls provenance within one application's execution. SAGA makes identity, contact, and delegated authority explicit when autonomous agents communicate across a provider-mediated ecosystem.

## Paper Day 19 — Delegation requires cryptographic and lifecycle state

### Paper

**SAGA: A Security Architecture for Governing AI Agentic Systems**

Venue: Network and Distributed System Security Symposium (NDSS) 2026 (peer-reviewed conference paper)

Authors: Georgios Syros; Anshuman Suri; Jacob Ginesin; Cristina Nita-Rotaru; Alina Oprea

Author institutions:

- Northeastern University

Notable / established authors or group:

The complete author team is from Northeastern University's systems-security community, including Cristina Nita-Rotaru and Alina Oprea.

### What problem does this paper solve?

When agents discover, contact, and delegate to one another, ordinary API credentials do not express which user authorized the relationship, which contacts are allowed, or how an agent's lifecycle is governed. Textual instructions inside agent context are not an authorization protocol. SAGA asks how users can retain explicit control over inter-agent communication and delegation even when message selection is autonomous.

### Technical core

Users register agents with a provider that maintains identity, lifecycle, contact information, and user-defined communication policies. A cryptographic token derivation mechanism gives agents fine-grained evidence that a contact or delegated interaction is authorized; receiving agents enforce policy rather than trusting message prose. ProVerif models token secrecy and authentication properties. The implementation evaluates geographically distributed agents with cloud and on-device models and studies a registry that can be replicated and sharded using crash-fault-tolerant Raft. Overhead is small relative to model latency in the three evaluated tasks. The provider is trusted, Byzantine replication is not implemented, and the study does not yet establish policy usability at ecosystem scale.

### Why it earns one of 20 slots

It fills an otherwise missing correctness dimension: dynamic identity, user governance, and delegation are explicit protocol state. Neither CaMeL nor an action monitor alone supplies this inter-agent authorization layer.

### Intellectual connection

SAGA governs who may communicate and delegate. AgentSpec closes the sequence by enforcing application-specific temporal and stateful policies on the concrete actions an agent attempts.

## Paper Day 20 — Put safety policy in an external reference monitor

### Paper

**AgentSpec: Customizable Runtime Enforcement for Safe and Reliable LLM Agents**

Venue: ICSE 2026 (peer-reviewed conference paper)

Authors: Haoyu Wang; Chris Poskitt; Jun Sun

Author institutions:

- School of Computing and Information Systems, Singapore Management University

Notable / established authors or group:

The author team is from Singapore Management University's formal methods and software-engineering community; the selection is based on the policy language and reference-monitor design.

### What problem does this paper solve?

Natural-language safety instructions are probabilistic and may be forgotten, overridden by context, or misinterpreted during replanning. Conventional API validation also cannot express many history-dependent rules, such as requiring a fresh check before an effect or bounding action sequences across tools. AgentSpec asks how developers can state such policies outside the model and mediate every safety-relevant action at runtime.

### Technical core

AgentSpec provides a policy DSL for predicates over agent state, tool arguments, outputs, and temporal action history. A runtime monitor intercepts proposed actions, evaluates applicable rules, and can permit, deny, or redirect execution without relying on the model to remember the policy. The paper integrates enforcement with several agent frameworks, evaluates safety and reliability policies over multiple benchmarks, and reports low monitoring overhead relative to model execution. The clever idea is not another critic call but an externally controlled reference monitor with inspectable state and customizable predicates. Its guarantee remains limited by hook completeness, state visibility, policy correctness, and the semantics exposed by tool adapters.

### Why it earns one of 20 slots

It turns software correctness requirements into executable runtime artifacts and supplies the course's final enforcement mechanism. It also makes limitations explicit: a monitor cannot enforce facts it cannot observe or policies nobody specified.

### Intellectual connection

The final synthesis is deliberately plural: AgentSpec enforces declared rules; SAGA validates delegated authority; CaMeL constrains influence; adjustable autonomy transfers control; Beldi makes mediated retries transactional; and Sagas explains what remains when effects escape atomic rollback.
