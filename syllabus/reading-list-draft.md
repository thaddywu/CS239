# CS239 Agentic Software Engineering — Final Reading List Draft

This draft contains exactly 20 primary-paper discussion days, two Document Review days, and one student paper/system presentation session. The instructor-led tutorial scaffold—MCP, A2A, Strands, ReAct, Toolformer, OpenHands, and benchmark/version caveats—is background rather than an additional paper day.

# Theme: Interfaces and Agent Runtimes

## Theme question

Where should an agent's capability live: in model behavior, in the action interface, or in an independently managed runtime?

## Why this theme matters

Before asking whether an agent can plan or code, the course needs a precise model of what the agent can observe and do. These papers turn the framework stack into inspectable design choices: constrained commands, executable action languages, declarative workflow graphs, optimizers, and runtime policy.

## Paper Day 1 — The agent-computer interface is part of the algorithm

### Paper

**SWE-agent: Agent-Computer Interfaces Enable Automated Software Engineering**

Venue: [NeurIPS 2024, Main Conference Track](https://proceedings.neurips.cc/paper_files/paper/2024/hash/5a7c947568c1b1328ccc5230172e1e7c-Abstract-Conference.html) — publication status: peer-reviewed conference paper.

Authors: John Yang; Carlos E. Jimenez; Alexander Wettig; Kilian Lieret; Shunyu Yao; Karthik Narasimhan; Ofir Press

Author institutions:

- Princeton Language and Intelligence, Princeton University

### What problem does this paper solve?

Repository repair agents are often evaluated as if the language model alone determines success, even though the model acts through an interface designed for humans or inherited from a shell. That interface can flood the context with irrelevant output, make navigation expensive, permit malformed edits, and hide useful failure information. The paper asks whether an agent-computer interface should instead be designed around the perceptual and action limitations of language models. It targets real issue resolution, where an agent must locate relevant code, inspect bounded portions of large files, edit safely, run tests, and retain enough interaction history to recover from mistakes. The deeper problem is causal attribution: if interface choices materially change behavior, benchmark scores cannot be read simply as measurements of model intelligence or autonomous planning.

### Technical core

SWE-agent exposes a small set of LM-oriented repository commands for search, bounded file viewing, line-based editing, and execution. Observations are deliberately compact, older history is compressed, and failed commands return targeted feedback. Editing includes syntax-oriented guardrails so malformed changes are rejected before they contaminate later steps. The paper makes these choices testable through interface ablations: search result presentation, viewing-window size, editor design, lint feedback, and history policy are varied while the task and model are held comparatively stable. On a 300-task study, these changes produce meaningful differences, including benefits from summarized search, a medium-sized view window, syntax checking, and compressed recent context. The contribution is therefore a recoverable interaction protocol, not merely a prompt or a collection of shell commands.

### Why it earns one course day

It gives the course a concrete systems object—the ACI—whose design can be analyzed and ablated. It also establishes a durable question for every later paper: which failures belong to the model, and which were induced or prevented by the runtime interface?

### Connection

Read directly against CodeAct's opposite bet on a maximally expressive action language.

## Paper Day 2 — Expressiveness versus confinement in the action space

### Paper

**Executable Code Actions Elicit Better LLM Agents**

Venue: [ICML 2024, PMLR 235](https://proceedings.mlr.press/v235/wang24h.html) — publication status: peer-reviewed conference paper.

Authors: Xingyao Wang; Yangyi Chen; Lifan Yuan; Yizhe Zhang; Yunzhu Li; Hao Peng; Heng Ji

Author institutions:

- University of Illinois Urbana-Champaign
- Apple

### What problem does this paper solve?

Most tool-using agents select from a collection of text or JSON call schemas. That arrangement works for atomic calls but becomes awkward when a task requires loops, branching, intermediate variables, composition across libraries, or revision after an exception. Each new tool enlarges a heterogeneous action vocabulary, while orchestration remains implicit in generated text. CodeAct asks whether a familiar programming language can serve as one compositional action space for many tools and environments. The target is not simply syntactic convenience: the system must preserve intermediate state, execute proposed operations, expose concrete errors, and let the model revise its next action from those observations. The paper therefore isolates an interface-design question that framework comparisons usually blur—whether agents benefit from a small guarded command set or from a powerful general-purpose language.

### Technical core

CodeAct lets the model emit executable Python interleaved with natural-language turns. A persistent interpreter retains variables and imported libraries, executes composed operations, and returns outputs or exceptions into the next turn. The paper evaluates this interface across seventeen models against common text and JSON action formats, reporting improvements of up to twenty percentage points on its tool-use settings. It then separates interface effects from training effects by constructing CodeActInstruct, roughly seven thousand multi-turn action trajectories, and fine-tuning open models to use the code-action protocol. The interpreter makes multi-step tool composition explicit and gives debugging a real environmental signal, but it also moves a large amount of authority behind a single action channel. Python expressiveness is thus both the mechanism that produces capability and the mechanism that expands the sandboxing, validation, and rollback burden.

### Why it earns one course day

The paper offers a non-obvious, empirically tested action-space abstraction rather than another tool-call prompt. Its productive conflict with SWE-agent lets a class debate expressiveness, inspectability, least privilege, and which complexity belongs in the model versus the interface.

### Connection

Murakkab moves the next layer of responsibility—from individual actions to whole-workflow execution—outside the model.

## Paper Day 3 — Treat the workflow graph as an optimizable program

### Paper

**Murakkab: Resource-Efficient Agentic Workflow Orchestration in Cloud Platforms**

Venue: [20th USENIX Symposium on Operating Systems Design and Implementation (OSDI 2026)](https://www.usenix.org/conference/osdi26/presentation/chaudhry) — publication status: peer-reviewed conference paper.

Authors: Gohar Irfan Chaudhry; Esha Choukse; Haoran Qiu; Íñigo Goiri; Rodrigo Fonseca; Adam Belay; Ricardo Bianchini

Author institutions:

- MIT Computer Science and Artificial Intelligence Laboratory
- Microsoft Azure Research

### What problem does this paper solve?

Agentic workflows combine several model calls, tools, branches, and aggregation stages, yet common serving stacks see only an opaque sequence of requests. When control logic is tightly coupled to a particular model and hardware assignment, a cloud system cannot jointly trade accuracy, latency, energy, and cost across the workflow. Static deployment choices also become stale as arrival rates and service-level objectives change. Murakkab addresses this systems problem by making the internal workflow available to an optimizer and runtime without requiring the model to decide resource policy. The paper asks what abstraction a cloud platform needs to treat an agent graph as a program rather than as unrelated inference calls. Its objective is not better prompting; it is predictable and adaptable execution of multi-component agent workloads under explicit service-level constraints.

### Technical core

Murakkab introduces a declarative workflow representation that separates logical control flow from concrete model, accelerator, batching, and execution choices. Offline profiling characterizes component alternatives, after which a cross-layer optimizer searches configurations that satisfy user-specified accuracy and systems objectives. At runtime, resource multiplexing and adaptive reconfiguration respond to load and changing SLOs while preserving the workflow specification. The evaluation covers several static workflows and a dynamic coding case, reporting reductions of up to 2.8 times in GPU use, 3.7 times in energy, and 4.3 times in cost while maintaining target SLOs. The crucial design move is that workflow structure becomes inspectable optimization input. The limitation is equally instructive: benchmark accuracy stands in for semantic task quality, and efficient re-execution is not equivalent to safe recovery from externally visible side effects.

### Why it earns one course day

This is the strongest existing systems-runtime paper in the corpus: it contributes an abstraction, optimizer, adaptive runtime, and measured resource trade-offs. It also prevents the opening unit from collapsing into interface prompts by showing that orchestration has a genuine systems layer.

### Connection

The next theme asks what happens when the workflow contains several communicating decision makers rather than a known graph of components.

# Theme: Multi-Agent Architecture without Role-Playing

## Theme question

How should communication structure control the spread of useful information and the containment of faulty agents?

## Why this theme matters

Multiple personas are not an architecture. These readings make the graph and the fault model explicit, then test interventions that distinguish useful coordination from extra sampling, correlated error, and unchecked message propagation.

## Paper Day 4 — Communication topology as a causal mechanism

### Paper

**Understanding the Information Propagation Effects of Communication Topologies in LLM-based Multi-Agent Systems**

Venue: [EMNLP 2025, Main Conference](https://aclanthology.org/2025.emnlp-main.623/) — publication status: peer-reviewed conference paper.

Authors: Xu Shen; Yixin Liu; Yiwei Dai; Yili Wang; Rui Miao; Yue Tan; Shirui Pan; Xin Wang

Author institutions:

- School of Artificial Intelligence, Jilin University
- School of Information and Communication Technology, Griffith University
- School of Computer Science and Engineering, University of New South Wales

### What problem does this paper solve?

Multi-agent systems are commonly compared using chain, tree, sparse, or fully connected communication graphs, but aggregate accuracy does not explain why a graph helps. Dense connectivity can spread a useful insight rapidly and also amplify one erroneous message; sparse connectivity can contain error and also prevent a decisive fact from reaching the final node. The paper seeks a causal account of this trade-off rather than another leaderboard of team configurations. It asks how an individual agent's output changes collective decisions under a fixed topology, when sparsity suppresses harmful propagation, and when it blocks beneficial information. That problem matters for software teams of agents because the same channel may carry code hypotheses, test interpretations, security claims, or corrupted state, and “more collaboration” has no monotonic relationship with correctness.

### Technical core

The paper introduces Counterfactual Agent Propagation Effect (CAPE), which intervenes on an agent output and measures the resulting change in the collective prediction. CAPE separates beneficial insight propagation from error propagation across topologies with different sparsity. The empirical analysis shows that moderately sparse graphs often strike the best balance: they retain paths for complementary information while reducing indiscriminate contamination. Guided by this result, EIB-Learner combines structural views derived from dense and sparse graphs and uses a graph-neural topology optimizer to construct task-sensitive communication patterns. Experiments across six datasets compare effectiveness, communication cost, and robustness. The mechanism is deeper than choosing a graph by intuition, although the causal claims remain episode-bound: agents frequently share base models, and the learned topology does not authenticate messages, constrain authority, or prevent correlated failures.

### Why it earns one course day

It turns topology into an explanatory and design variable, with both an intervention metric and a learned mechanism. The paper supports discussion about causal attribution, graph sparsity, error diffusion, and why a coordination graph is not itself a security boundary.

### Connection

The following paper makes the fault explicit and asks whether topology and model reviewers can actually contain it.

## Paper Day 5 — Fault injection and containment in multi-agent systems

### Paper

**On the Resilience of LLM-Based Multi-Agent Collaboration with Faulty Agents**

Venue: [ICML 2025, PMLR 267](https://proceedings.mlr.press/v267/huang25ay.html) — publication status: peer-reviewed conference paper.

Authors: Jen-Tse Huang; Jiaxu Zhou; Tailin Jin; Xuhui Zhou; Zixi Chen; Wenxuan Wang; Youliang Yuan; Michael Lyu; Maarten Sap

Author institutions:

- The Chinese University of Hong Kong
- Tsinghua University
- Carnegie Mellon University
- Peking University
- Renmin University of China
- The Chinese University of Hong Kong, Shenzhen

### What problem does this paper solve?

A multi-agent system can look effective when every component is cooperative and similarly capable, yet deployment must tolerate an agent that is incompetent, corrupted, or malicious. Existing demonstrations rarely specify a fault model or distinguish failure caused by one node from common model error. This paper asks how linear, flat, and hierarchical collaboration structures degrade when a controlled faulty response is introduced, and whether explicit review mechanisms recover the system. It spans code generation, mathematics, translation, and evaluation to test whether resilience depends on both task and topology. For the course, the important problem is architectural: when one component emits bad information, what paths allow the fault to dominate, who is allowed to challenge it, and can a model-based reviewer provide anything resembling independent containment?

### Technical core

AutoTransform and AutoInject generate controlled faulty agent responses, enabling the authors to compare six systems and three structural families under injected error. The hierarchical pattern `A -> (B <-> C)` shows a smaller reported performance drop than the linear and flat alternatives. Two mitigation designs then modify the protocol: Challenger lets agents contest another message, while Inspector adds a reviewing component that identifies and corrects suspect outputs. In selected configurations these mechanisms recover up to 96.4 percent of injected errors. The experiments therefore test both structure and remediation instead of merely assigning different occupational roles. However, the faults are synthetic, and Inspector is another language model that may share the same blind spots. Recovery from a bad message is also much easier than undoing a tool action, repairing poisoned shared memory, or containing colluding agents.

### Why it earns one course day

It provides the necessary counterfactual for claims of multi-agent robustness: introduce a fault, locate its propagation path, and measure recovery. Paired with the topology paper, it yields a full discussion day on whether review by another model is fault tolerance or only correlated redundancy.

### Connection

The course now returns to software engineering, where structure and validation can be grounded in repositories rather than conversational messages.

# Theme: Repository-Scale Coding and Analysis

## Theme question

Which representations and control structures let an agent change a repository without confusing navigation, planning, and validation?

## Why this theme matters

Repository work exposes the difference between an impressive trajectory and an engineered system. The four readings progressively replace generic browsing with program structure, fixed phases, explicit edit obligations, and whole-program analysis.

## Paper Day 6 — Program structure as the agent's search policy

### Paper

**AutoCodeRover: Autonomous Program Improvement**

Venue: [ISSTA 2024](https://2024.issta.org/details/issta-2024-papers/127/AutoCodeRover-Autonomous-Program-Improvement) — publication status: peer-reviewed conference paper.

Authors: Yuntong Zhang; Haifeng Ruan; Zhiyu Fan; Abhik Roychoudhury

Author institutions:

- National University of Singapore

### What problem does this paper solve?

Issue-resolution agents must find a small set of relevant program entities inside repositories too large to place in a prompt. Generic shell exploration and lexical retrieval can spend most of the budget on irrelevant files, while a one-shot patch has no opportunity to use execution evidence. AutoCodeRover addresses localization and repair as a program-improvement workflow grounded in code structure. Given a natural-language issue, it must infer likely classes, methods, and call relationships, gather just enough context, propose a patch, and respond to test results. The paper's challenge is not simply generating code that looks plausible; it is deciding where to look and how to refine that decision after a failed attempt. This makes it a useful representative of open-ended coding agents whose search is constrained by software-engineering artifacts rather than by a generic conversation loop.

### Technical core

AutoCodeRover exposes repository search operations over classes, methods, code snippets, and related definitions, using the model's evolving hypothesis to select program-structure-aware context. The agent iteratively localizes likely fault sites, constructs a patch, runs the available tests, and can revise its analysis from concrete failures. Its ISSTA evaluation reports 57 resolved GitHub issues at pass@1 with an average cost around $0.43 in the studied configuration, illustrating that structured navigation can avoid the very large contexts and budgets of more generic agents. The technical contribution lies mainly in analysis-guided retrieval and workflow design, not in a stronger correctness oracle: tests still decide acceptance. Results also depend on the language parser, benchmark infrastructure, and issue distribution. A passing patch may overfit tests or miss intent not encoded in executable artifacts.

### Why it earns one course day

It is a compact, technically grounded coding-agent architecture whose decisions can be traced to repository entities. It also creates the right baseline question for Agentless: does the model need open-ended control of this workflow at all?

### Connection

Agentless holds the task fixed while replacing the exploratory agent loop with a deterministic staged pipeline.

## Paper Day 7 — Is autonomy necessary for software repair?

### Paper

**Demystifying LLM-based Software Engineering Agents**

Venue: [FSE 2025](https://conf.researchr.org/details/fse-2025/fse-2025-research-papers/85/Demystifying-LLM-based-Software-Engineering-Agents) — publication status: peer-reviewed conference paper.

Authors: Chunqiu Steven Xia; Yinlin Deng; Soren Dunn; Lingming Zhang

Author institutions:

- University of Illinois Urbana-Champaign

### What problem does this paper solve?

Complex software agents bundle planning, navigation, repeated model calls, tool use, and validation, making it difficult to know whether open-ended autonomy caused the observed result. They can also consume large budgets while repeatedly exploring the same repository. This paper asks whether issue repair can instead be decomposed into a small, fixed pipeline whose phases are independently inspectable. The system must still localize files and edit sites, generate candidate patches, and determine which candidate is most credible, but it does not let a model invent the control flow. The problem is therefore methodological as well as practical: establish a strong low-cost control condition before crediting an autonomous loop. If a deterministic pipeline matches or beats elaborate agents, future papers must identify the specific adaptive decision that justifies extra agency.

### Technical core

Agentless fixes computation into three phases. Hierarchical localization narrows from files to class or function skeletons and then to edit locations, combining embedding retrieval with model judgments while aggressively compressing context. Repair samples small patch candidates around the selected locations. Validation generates reproduction tests, executes them on original and patched repositories, screens for regressions, and ranks survivors. In the main ablation setting, reproduction-test selection improves the result from 25.67 percent under majority voting to 32 percent, while combined file localization includes the ground-truth file in 81.67 percent of cases. The mechanism is deliberately un-agentic: repeated model inference is retained, but planning and phase transitions are program-defined. Generated tests can nevertheless share the patch's misunderstanding, and later benchmark revisions make raw score comparisons less informative than the controlled pipeline ablations.

### Why it earns one course day

This is the course's cleanest antidote to agent washing. It supports a rigorous discussion about which adaptive decisions truly require an agent, what a fair compute-matched baseline looks like, and when deterministic orchestration is preferable.

### Connection

CodePlan retains planning, but grounds every plan node in an explicit repository edit obligation and dependency relation.

## Paper Day 8 — Planning as a changing graph of edit obligations

### Paper

**CodePlan: Repository-level Coding using LLMs and Planning**

Venue: [FSE 2024, Proceedings of the ACM on Software Engineering](https://www.microsoft.com/en-us/research/publication/codeplan-repository-level-coding-using-llms-and-planning-2/) — publication status: peer-reviewed conference paper.

Authors: Ramakrishna Bairi; Atharv Sonwane; Aditya Kanade; Vageesh D. C.; Arun Iyer; Suresh Parthasarathy; Sriram Rajamani; B. Ashok; Shashank Shet

Author institutions:

- Microsoft Research India

### What problem does this paper solve?

Repository-scale changes such as API migration or type propagation are not collections of independent local edits. A seed change can alter callers, overrides, types, and build obligations across dozens of files, while a reactive fix for the latest compiler error may undo the intended change or chase symptoms downstream. CodePlan asks how a coding system can represent the causal structure of a change and update that representation as edits are applied. The plan must identify code locations, record why one edit depends on another, provide the right spatial and temporal context to each model call, and use build or analysis diagnostics without letting the latest error become the entire strategy. This is planning over software semantics, not free-form decomposition into textual subtasks.

### Technical core

CodePlan represents work as a directed acyclic graph whose nodes contain a code block, an edit instruction, and completion status; edges encode why another edit is required. Incremental dependency analysis and a change-may-impact relation expand the graph after each accepted edit. A model receives spatial context from repository dependencies and temporal context from predecessor changes, while the dependency representation itself is refreshed as the repository evolves. Build, type-check, test, or analysis failures can create new seed obligations. Evaluation covers C# package migration and Python temporal edits spanning two to ninety-seven files. The final FSE study reports five of seven repositories passing its validity checks, whereas same-context baselines without planning pass none. The analysis is intentionally incomplete and task-specific, so the plan is a structured hypothesis rather than a sound change-impact proof.

### Why it earns one course day

The edit-obligation DAG is a clever, inspectable mechanism that makes repository planning falsifiable. It also connects coding agents to classical change-impact analysis and sets up a broader question: when should an LLM propose semantics for an existing analyzer rather than control the analysis itself?

### Connection

Document Review I consolidates interface and planning choices before IRIS moves the semantic backbone into a static analyzer.

## Document Review Day 1 — Agent architecture and change-control design review

Teams review a proposed repository agent design that combines an MCP-style tool layer, a CodeAct-like interpreter, a multi-agent communication graph, and test-driven patch acceptance. The review must identify hidden authority, unsupported causal claims, missing baselines, and failure paths, then propose concrete interface, dependency, validation, and escalation changes. No new primary paper is assigned.

## Paper Day 9 — Let the model supply missing semantics, not reachability

### Paper

**IRIS: LLM-Assisted Static Analysis for Detecting Security Vulnerabilities**

Venue: [ICLR 2025](https://proceedings.iclr.cc/paper_files/paper/2025/hash/582d4e27fa24168f3af1f4582655034b-Abstract-Conference.html) — publication status: peer-reviewed conference paper.

Authors: Ziyang Li; Saikat Dutta; Mayur Naik

Author institutions:

- University of Pennsylvania
- Cornell University

### What problem does this paper solve?

Whole-program taint analysis can follow interprocedural data flow, but real repositories use libraries whose sources, sinks, propagators, and sanitizers have not been modeled. Missing specifications produce false negatives, while manually creating them is expensive. A language model can infer likely security roles from names and context, yet cannot reliably trace all paths through a repository or provide a sound reachability argument. IRIS addresses this complementary mismatch. It asks how probabilistic semantic judgment can extend a mature static analyzer without allowing the model to replace its program reasoning. The target is security vulnerability detection across large Java projects, where both recall and analyst workload matter. The broader course problem is responsibility allocation: use the model where specifications are missing, then use deterministic analysis where scale and consistency exceed contextual inference.

### Technical core

IRIS first extracts candidate external APIs and relevant internal parameters, then asks an LLM to assign CWE-specific taint roles. These labels are compiled into CodeQL specifications, allowing CodeQL to enumerate unsanitized interprocedural paths across the repository. A second contextual model stage receives a path and surrounding code to triage likely false positives and explain the report. On CWE-Bench-Java—120 manually validated vulnerabilities in large projects—base CodeQL detects 27, whereas IRIS with GPT-4 detects 55 and reduces average false-discovery rate by about five percentage points; the study also reports four previously unknown vulnerabilities. The symbolic engine owns reachability, but neither learned specification mining nor final triage is sound. If the model never identifies a needed semantic role, CodeQL cannot recover the missing path.

### Why it earns one course day

IRIS is one of the corpus's cleanest neuro-symbolic software-engineering systems: each component has a defensible responsibility and an observable failure mode. It enables a technical discussion of inferred specifications, sound versus unsound stages, false-positive triage, and what the “modulo” component actually guarantees.

### Connection

The validation block generalizes this pattern from program analysis to test search, oracle authority, and executable specifications.

# Theme: Validation, Specification, Formal Checking, and Recovery

## Theme question

What evidence should change an agent's behavior, and what must the surrounding system guarantee when tests, memories, or retries are unreliable?

## Why this theme matters

This is the course's dominant core. It moves from hybrid test generation to adversarial oracle analysis, durable properties, proof environments, autoformalization, persistent state, and finally an explicit recovery abstraction.

## Paper Day 10 — Invoke generation only when algorithmic search stalls

### Paper

**CodaMOSA: Escaping Coverage Plateaus in Test Generation with Pre-trained Large Language Models**

Venue: [ICSE 2023](https://conf.researchr.org/details/icse-2023/icse-2023-technical-track/132/CodaMOSA-Escaping-Coverage-Plateaus-in-Test-Generation-with-Pre-trained-Large-Langua) — publication status: peer-reviewed conference paper.

Authors: Caroline Lemieux; Jeevana Priya Inala; Shuvendu K. Lahiri; Siddhartha Sen

Author institutions:

- University of British Columbia
- Microsoft Research

### What problem does this paper solve?

Search-based software testing can mutate and optimize executable tests, but it reaches coverage plateaus when random construction is unlikely to produce semantically meaningful objects, strings, or call sequences. Language models can propose realistic tests, yet unconstrained generation lacks the fitness-guided exploration and systematic mutation of established testing algorithms. CodaMOSA asks how to combine the two without merely running both and taking the union. The system needs a measurable trigger for model intervention, a way to target under-covered functions, and a representation bridge that converts arbitrary generated Python into the restricted internal form used by search-based testing. The problem is an instance of disciplined hybridity: assign each technique the part of the search space where it has a comparative advantage.

### Technical core

CodaMOSA begins with MOSA-style search-based test generation and monitors coverage progress. When improvement stalls, it identifies low-coverage callables and queries Codex for example tests aimed at those regions. A deserialization procedure maps useful generated constructs into the search engine's internal test representation, after which ordinary mutation, execution, and coverage fitness resume. The LLM therefore injects seeds at a detected plateau rather than controlling the whole loop. Across 486 Python modules, CodaMOSA achieves statistically significant coverage increases on many more modules than it harms relative to both search-only and model-only baselines. The mechanism and ablations make invocation timing technically consequential. Still, branch or statement coverage is only a search signal: it says little about assertion quality, fault revelation, semantic intent, or whether an agent will exploit the tests.

### Why it earns one course day

The paper is a strong example of a clever hybrid algorithm whose control policy is explicit and measurable. It lets students distinguish “LLM plus a tool” from a genuine division of algorithmic labor.

### Connection

ImpossibleBench attacks the assumption that an executable test result is automatically trustworthy evidence of correctness.

## Paper Day 11 — When passing the tests proves the agent is wrong

### Paper

**ImpossibleBench: Measuring LLMs' Propensity of Exploiting Test Cases**

Venue: [ICLR 2026](https://proceedings.iclr.cc/paper_files/paper/2026/hash/ca688eb14e29701a11bdba6633186328-Abstract-Conference.html) — publication status: peer-reviewed conference paper.

Authors: Ziqian Zhong; Aditi Raghunathan; Nicholas Carlini

Author institutions:

- Carnegie Mellon University
- Anthropic

### What problem does this paper solve?

Coding benchmarks usually count a passing test suite as success, even when the patch violates the natural-language requirement, modifies the tests, special-cases inputs, or manipulates execution semantics. Manual inspection can find some exploitation, but it is expensive and lacks an unambiguous ground truth. ImpossibleBench constructs tasks in which tests deliberately contradict the stated specification, so every passing attempt necessarily demonstrates specification-violating behavior. The paper asks how often capable models exploit a proxy, which access and feedback conditions make exploitation easier, and whether monitors can recognize the resulting trajectories. This converts a vague concern about reward hacking into a controlled experiment. It also exposes a central software-engineering conflict: requirements, tests, code, and runtime policy are separate artifacts, and an agent needs a rule for what to do when they disagree.

### Technical core

The framework mutates LiveCodeBench and SWE-bench tasks using one-off expected-value changes or explicitly conflicting assertions. Candidate mutations are filtered by running original and empty patches so obviously invalid constructions are removed. Agents then operate under controlled variants of prompt wording, test visibility, read/write permission, scaffold complexity, feedback rounds, and access to a human-escalation action. Because a pass is definitionally illegitimate, the cheating rate has unusually clean semantics. The study catalogs strategies ranging from direct test edits to overloaded comparison operators, extra hidden state, and special casing. Read-only or hidden tests reduce some attacks, and an explicit abort path helps some models, but model-based monitors remain imperfect on repository tasks. The benchmark is synthetic by design, so it diagnoses propensity rather than estimating the natural frequency of contradictory artifacts.

### Why it earns one course day

It is an illuminating negative result with a technically sharp construction: success becomes evidence of failure. The paper can sustain discussion about Goodhart's law, access control on tests, escalation, evaluator independence, and why retry feedback may intensify exploitation.

### Connection

PropertyGPT responds by generating durable specifications that can be compiled, ranked, and checked independently of example tests.

## Paper Day 12 — Generate properties, then make them executable

### Paper

**PropertyGPT: LLM-driven Formal Verification of Smart Contracts through Retrieval-Augmented Property Generation**

Venue: [NDSS 2025](https://www.ndss-symposium.org/ndss-paper/propertygpt-llm-driven-formal-verification-of-smart-contracts-through-retrieval-augmented-property-generation/) — publication status: peer-reviewed conference paper.

Authors: Ye Liu; Yue Xue; Daoyuan Wu; Yuqiang Sun; Yi Li; Miaolei Shi; Yang Liu

Author institutions:

- Singapore Management University
- MetaTrust Labs
- The Hong Kong University of Science and Technology
- Nanyang Technological University

### What problem does this paper solve?

Formal smart-contract verification depends on invariants, preconditions, postconditions, and rules, but writing comprehensive properties requires scarce expertise. Existing provers can check a supplied property yet cannot decide which domain-specific obligations a new contract should satisfy. PropertyGPT asks whether an LLM can transfer expert-written specification patterns to unseen code while subjecting the generated artifacts to more than a plausibility judgment. It must retrieve relevant precedents, adapt them to new identifiers and behavior, repair properties that do not compile, prioritize appropriate candidates, and finally connect them to a verification engine. The underlying course problem is broader than contracts: can agents produce reusable semantic artifacts rather than ephemeral tests, and what evidence distinguishes a meaningful property from a syntactically valid or trivially true one?

### Technical core

PropertyGPT embeds properties from expert audit reports and retrieves a reference for in-context adaptation to a target contract. Generated candidates pass through compilation and static-analysis feedback, which drives iterative correction rather than verbal self-critique. A multi-dimensional ranking procedure scores semantic and structural similarity to select top candidates, and a dedicated prover attempts to verify them against the contract. On ninety ground-truth properties, the paper reports 80 percent recall and 64 percent precision; feedback raises compilability from 63 to 87 percent. The complete system detects 26 of 37 evaluated incidents and reports twelve previously unknown vulnerabilities. The stages provide concrete failure boundaries, although ranking is not a proof of property relevance and verification only guarantees the contract relative to the generated property. Domain transfer beyond Solidity and Certora-style specifications remains open.

### Why it earns one course day

It fills a genuine gap between test generation and formal checking: the agent creates a durable specification artifact and receives machine feedback at multiple stages. The class can debate property adequacy, vacuity, retrieval bias, and where human review remains indispensable.

### Connection

LeanDojo next shows the strongest version of a typed environment in which every accepted action and final artifact has formal semantics.

## Paper Day 13 — A proof assistant as an agent runtime

### Paper

**LeanDojo: Theorem Proving with Retrieval-Augmented Language Models**

Venue: [NeurIPS 2023, Datasets and Benchmarks Track](https://proceedings.neurips.cc/paper_files/paper/2023/hash/4441469427094f8873d0fecb0c4e1cee-Abstract-Datasets_and_Benchmarks.html) — publication status: peer-reviewed conference paper.

Authors: Kaiyu Yang; Aidan Swope; Alex Gu; Rahul Chalamala; Peiyang Song; Shixing Yu; Saad Godil; Ryan J. Prenger; Animashree Anandkumar

Author institutions:

- California Institute of Technology
- NVIDIA
- Massachusetts Institute of Technology
- University of California, Santa Barbara
- The University of Texas at Austin

### What problem does this paper solve?

Learning-based theorem provers need far more than a corpus of final proof text. They require exact proof states, legal tactics, dependency-constrained premises, reproducible interaction with a pinned proof environment, and evaluation splits that do not reward memorized library usage. Before LeanDojo, much relevant infrastructure and data were private, brittle, or difficult to connect to machine-learning systems. The paper addresses how to expose Lean as a programmatic environment for training and deploying proof agents while also tackling premise selection in a large mathematical library. This is highly relevant to agentic software engineering because it demonstrates what most coding runtimes lack: typed observable state, executable actions, precise failure feedback, scoped resources, and a validator the agent cannot persuade or rewrite.

### Technical core

LeanDojo instruments Lean repositories to extract abstract syntax, proof states, tactic traces, file dependencies, source locations, and fine-grained premise usage. It exposes an interactive API in which a prover submits tactics and receives kernel-grounded state transitions or errors. ReProver adds a trained retriever that selects only accessible premises and uses in-file hard negatives, then conditions tactic generation and best-first proof search on the retrieved library context. The benchmark contains 98,734 theorems and proofs, 217,776 tactics, and roughly 130,000 premises, with a novel-premises split designed to resist easy memorization. Retrieval improves proof success relative to non-retrieval baselines. Kernel acceptance certifies the formal proof, but not the faithfulness of the theorem statement to an informal requirement; environment and library versioning also remain part of the trusted setup.

### Why it earns one course day

LeanDojo is both a mechanism paper and a reference architecture for agent environments. It lets students ask which properties of proof assistants—typed state, scoped actions, immutable checks, reproducible versions—can be imported into software-agent runtimes.

### Connection

PAT-Agent moves the uncertainty upstream: the checker is exact, but the formal model itself must be inferred from natural language.

## Paper Day 14 — Counterexample-guided autoformalization

### Paper

**PAT-Agent: Autoformalization for Model Checking**

Venue: [ASE 2025](https://doi.org/10.1109/ASE63991.2025.00176) — publication status: peer-reviewed conference paper.

Authors: Xinyue Zuo; Yifan Zhang; Hongshu Wang; Yufan Cai; Zhe Hou; Jing Sun; Jin Song Dong

Author institutions:

- National University of Singapore
- Griffith University
- School of Computer Science, University of Auckland

### What problem does this paper solve?

Model checking can prove that a formal transition system satisfies stated assertions or return a concrete counterexample, but building that model from a natural-language system description is specialized and error-prone. Direct generation mixes architectural understanding, formal syntax, and property encoding in one fragile step. PAT-Agent asks how to decompose autoformalization so that a model can be compiled, checked, and repaired using machine evidence. The system must identify processes, state, synchronization, and desired properties; generate CSP#; distinguish syntax failures from assertion violations; and use counterexample traces to guide revision. The fundamental difficulty is that a verified formal model may still omit or distort the intended behavior, so internal consistency and translation faithfulness must be discussed as separate claims.

### Technical core

A planning model first structures the natural-language description into modeling elements and an explicit synthesis plan. A generation model converts that plan into CSP# accepted by the Process Analysis Toolkit. PAT then checks compilation and assertions, returning diagnostics or counterexample traces to a bounded repair loop. This makes the external verifier introduce genuinely new information at each revision. On forty systems, the complete pipeline reaches full compilation and full-pass within up to five rounds, while direct baselines achieve substantially lower full-pass rates; ablations show that removing either planning or repair reduces performance. The result demonstrates useful checker-guided synthesis, not semantic completeness. Repair is tailored to PAT and CSP#, the evaluation corpus is limited, and no kernel can establish that the generated model faithfully contains every behavior meant by an ambiguous prose description.

### Why it earns one course day

The paper joins planning, a formal intermediate artifact, counterexample-guided repair, and an exact checker in one analyzable pipeline. It supports a demanding discussion about what has actually been proved when the specification itself is model-generated.

### Connection

The next pair treats persistent memory as another generated artifact whose later reuse can improve or corrupt behavior.

## Paper Day 15 — Learn memory management as part of the policy

### Paper

**Agentic Memory: Learning Unified Long-Term and Short-Term Memory Management for Large Language Model Agents**

Venue: [ACL 2026, Long Papers](https://aclanthology.org/2026.acl-long.981/) — publication status: peer-reviewed conference paper.

Authors: Yi Yu; Liuyi Yao; Yuexiang Xie; Qingquan Tan; Jiaqi Feng; Yaliang Li; Libing Wu

Author institutions:

- School of Cyber Science and Engineering, Wuhan University
- Alibaba Group

### What problem does this paper solve?

Long-horizon agents typically manage long-term memory with fixed triggers or a separate controller while treating the active context as a passive sliding window. These independently designed policies can store irrelevant experiences, fail to retrieve useful facts, and retain distracting context without optimizing how both memory tiers interact. Agentic Memory asks whether storage, retrieval, update, deletion, summarization, and filtering can become first-class actions of the same policy that solves the task. The challenge is temporal credit assignment: a memory decision made early may affect an answer many steps later, producing sparse and discontinuous rewards. A useful solution must teach the model not only what content matters, but when to manipulate persistent and active state across multi-stage tasks.

### Technical core

AgeMem exposes structured tools for adding, updating, deleting, and retrieving long-term records and for summarizing or filtering short-term context. A three-stage rollout separates long-term memory construction, context-pressure management, and a later task that requires coordination across both stores. Progressive reinforcement learning first develops each capability and then integrates them. Step-wise Group Relative Policy Optimization propagates outcome credit back to individual memory actions, addressing the delay between state mutation and observed utility. Across five long-horizon benchmarks, the reported average rises from 28.05 to 41.96 on Qwen2.5-7B and from 43.97 to 54.31 on Qwen3-4B relative to no-memory settings, with component ablations supporting the separate mechanisms. The learned policy still depends on designed rewards and clean benchmark feedback that many deployments cannot supply.

### Why it earns one course day

This is not retrieval augmentation renamed as memory: memory mutation is explicit in the action space and learned through a staged credit-assignment method. It gives the class a constructive design to test against delayed contamination and evaluator dependence.

### Connection

The following empirical paper asks what happens when retrieved experiences are wrong, stale, or only superficially aligned.

## Paper Day 16 — Persistent memory as a delayed failure channel

### Paper

**How Memory Management Impacts LLM Agents: An Empirical Study of Experience-Following Behavior**

Venue: [ACL 2026, Long Papers](https://aclanthology.org/2026.acl-long.27/) — publication status: peer-reviewed conference paper.

Authors: Zidi Xiong; Yuping Lin; Wenya Xie; Pengfei He; Zirui Liu; Jiliang Tang; Himabindu Lakkaraju; Zhen Xiang

Author institutions:

- Harvard University
- University of Georgia
- Michigan State University
- University of Minnesota-Twin Cities

### What problem does this paper solve?

Agent memory is usually justified by average gains from retrieving past successes, but a growing memory bank is a dynamic stateful system populated by the agent's own imperfect trajectories. An error stored today can influence many later tasks, and even a successful experience can be misleading when superficial input similarity hides a different objective. This paper asks how addition and deletion policies change long-term behavior, whether agents copy retrieved experience in measurable ways, and when evaluators can prevent contamination. It focuses on the mechanism behind memory benefit and harm rather than proposing another vector-store architecture. The software-engineering analogy is direct: cached plans, patches, tool traces, and summaries require provenance, quality labels, invalidation, and distribution-shift handling, not just a larger retrieval index.

### Technical core

The study compares unfiltered, automatically evaluated, and strict memory addition with periodic, history-based, and combined deletion across four agent setups. Its central measurement, experience-following, relates similarity between a new task and a retrieved record to similarity of the resulting output. Controlled experiments show two distinct hazards: inaccurate memories propagate errors, while apparently successful but misaligned experiences are replayed in inappropriate contexts. Strict selection improves behavior, and future task outcomes can become delayed labels for stored records. History-based deletion can greatly shrink memory, but only when its utility evaluator is reliable; a coarse evaluator removes valuable experience and reduces performance. The operation set is intentionally narrow—addition and deletion—so merge semantics, provenance graphs, concurrency, schema evolution, and consistency across agents remain unresolved.

### Why it earns one course day

It provides the negative half of a unusually strong pairing: learned memory actions do not solve memory quality or invalidation. The experiments support discussion of state contamination, evaluator trust, delayed labels, and why persistent agents need database-like governance.

### Connection

Microreboot asks what a runtime can do after stateful execution has failed, rather than merely asking the model to try again.

## Paper Day 17 — Recovery requires a system boundary, not a retry prompt

### Paper

**Microreboot—A Technique for Cheap Recovery**

Venue: [6th USENIX Symposium on Operating Systems Design and Implementation (OSDI 2004)](https://www.usenix.org/conference/osdi-04/microreboot%E2%80%94-technique-cheap-recovery) — publication status: peer-reviewed conference paper.

Authors: George Candea; Shinichi Kawamoto; Yuichi Fujiki; Greg Friedman; Armando Fox

Author institutions:

- Computer Systems Lab, Stanford University

### What problem does this paper solve?

Rebooting often clears transient software failures even when the root cause is unknown, but restarting an entire process or machine creates long outages and discards unrelated work. Microreboot asks whether recovery can be made cheap enough to invoke speculatively by restarting only the smallest replaceable component. That requires a design in which component execution state is separable from durable user and session data, dependencies tolerate temporary unavailability, and requests can retry without duplicating harmful effects. Although the paper predates LLM agents, it earns current relevance because most agent frameworks call another model attempt “recovery” without defining a restart boundary, state restoration policy, or side-effect model. The paper supplies concrete abstractions for asking what can be reset after a failed plan and what must survive.

### Technical core

The system gives application components restartable lifecycles, externalizes durable state, and structures dependencies so a recovery manager can surgically microreboot a suspected component before escalating to larger restarts. Requests that encounter the restarting component fail quickly or retry transparently, reducing the user-visible recovery interval. Experiments on a J2EE auction application show that microreboots recover most failures addressed by full reboot while completing roughly an order of magnitude faster and losing much less work. The mechanism depends on crash-only component behavior and disciplined state separation. It does not repair corrupted durable data, prove that an external action is idempotent, or roll back a transaction already committed to another service. Those limitations make it especially valuable for agent design: retries are safe only after the runtime identifies which state and effects can be replayed.

### Why it earns one course day

This classic systems paper passes the modern reading-cost test because it contributes the missing recovery abstraction, not just historical context. It lets the class turn vague proposals for “reflection and retry” into designs with restart units, durable-state boundaries, escalation, and idempotence requirements.

### Connection

The application case now tests how far an unusually clean learned-proposer/symbolic-checker split can go under a domain-specific state model.

# Theme: Application Case and Student Frontier Scan

## Theme question

Which application domains make agent responsibilities precise enough to yield mechanisms rather than demos?

## Why this theme matters

An application earns course time only when its environment exposes a reusable division of labor. AlphaGeometry provides that mechanism; the student session then stress-tests whether newly found systems meet the same bar.

## Paper Day 18 — Neural proposals, symbolic closure

### Paper

**Solving olympiad geometry without human demonstrations**

Venue: [Nature 625 (2024), 476–482](https://www.nature.com/articles/s41586-023-06747-5) — publication status: peer-reviewed journal article.

Authors: Trieu H. Trinh; Yuhuai Wu; Quoc V. Le; He He; Thang Luong

Author institutions:

- Google DeepMind
- Computer Science Department, New York University

### What problem does this paper solve?

Symbolic geometry engines can derive consequences quickly and exactly from known objects, but hard olympiad proofs often require an auxiliary construction that introduces a new point or relation. Such exogenous terms create an effectively infinite branching factor that hand-written heuristics cover poorly. At the same time, human formal proofs are too scarce to train a large neural proposer directly. AlphaGeometry addresses both bottlenecks: generate a large synthetic proof corpus and restrict learned generation to the decisions that symbolic deduction cannot efficiently enumerate. The paper is not a general conversational agent, which is precisely why it is useful. It asks whether a narrow, explicit responsibility split between probabilistic proposal and exact closure can solve a difficult application more reliably than end-to-end text generation.

### Technical core

The system generates roughly one hundred million synthetic geometry theorems and proofs and identifies dependency differences that expose auxiliary-construction steps. A language model is trained to propose those exogenous terms, while a symbolic engine performs deductive closure and either completes the proof or returns the enlarged state for another proposal. Learned search is therefore confined to the infinite-branching portion; routine reasoning and final validity remain symbolic. AlphaGeometry solves 25 of 30 selected olympiad geometry problems, compared with ten for the prior symbolic baseline, and its formal proof traces can be checked and rendered for human review. The domain provides a clean language, a strong synthetic generator, and exact semantics. Diagram interpretation and informal-to-formal translation are mostly outside the evaluated problem, limiting direct transfer to messy software requirements.

### Why it earns one course day

AlphaGeometry is the application reading because its success rests on a clear technical contract between components, not on a broad autonomous-agent demonstration. Students can map auxiliary constructions to candidate invariants, specifications, edit obligations, or abstractions in software engineering and identify where the analogy fails.

### Connection

The student session applies the course's mechanism and counterfactual tests to frontier papers and systems found outside the selected twenty.

## Student Session — 5-minute: Here's an Interesting Agent Paper/System I Found

Each student presents one paper or system in five minutes: the claimed mechanism, the strongest counterfactual, the evidence that it is not prompt-only or agent washing, and one unresolved software-engineering failure mode. This is a discovery and critique session, not an additional primary-paper day.

# Theme: Correctness and Safety as Runtime Governance

## Theme question

How can an agent remain useful when model outputs and tool data are untrusted, policies are incomplete, and actions have real authority?

## Why this theme matters

The final pair moves safety out of the prompt and into enforceable software mechanisms. One constrains provenance-sensitive control and data flow by construction; the other supplies customizable policies and an external reference monitor over runtime actions.

## Paper Day 19 — Defeat prompt injection by separating control from data

### Paper

**Defeating Prompt Injections by Design**

Venue: [IEEE Conference on Secure and Trustworthy Machine Learning (SaTML 2026)](https://www.floriantramer.com/publications/camel25/) — publication status: peer-reviewed conference paper.

Authors: Edoardo Debenedetti; Ilia Shumailov; Tianqi Fan; Jamie Hayes; Nicholas Carlini; Daniel Fabian; Christoph Kern; Chongyang Shi; Andreas Terzis; Florian Tramèr

Author institutions:

- Google
- Google DeepMind
- ETH Zurich

### What problem does this paper solve?

Tool-using agents commonly place trusted user instructions and untrusted data returned by email, documents, or web tools into one model context. A prompt injection embedded in that data can then alter control flow or redirect privileged information because the same model interprets content and authorizes actions. Training or prompting the model to ignore attacks cannot establish a reliable boundary. CaMeL reframes the problem as information-flow control and confused-deputy prevention: untrusted text may inform a computation, but it must not gain authority to rewrite the plan or exfiltrate protected values. The system must preserve useful dynamic data handling while ensuring that provenance and capabilities, rather than model confidence, govern sensitive tool calls.

### Technical core

CaMeL uses a privileged model to derive a program from trusted user input and a quarantined model to interpret untrusted values without changing that program's control structure. A custom Python-like interpreter attaches provenance and fine-grained capability metadata to values as they flow through computation. Deterministic policies mediate tools, arguments, and allowed data flows before execution. On the current AgentDojo evaluation, the main configuration reports no successful benchmark attacks while retaining 66.7 percent aggregate utility under attack; normal and strict modes expose the security–utility trade-off. The guarantee is relative to program translation, annotations, policy correctness, and the trusted interpreter. Ambiguous intent, unsupported dynamic control, availability attacks, and misuse that remains inside an allowed flow can still require confirmation or refusal.

### Why it earns one course day

CaMeL clears the absolute technical bar: separation, provenance, capabilities, an interpreter, and enforceable policies replace a defensive prompt. It supports a deep discussion of trusted computing bases, noninterference-like claims, annotation burden, and whether useful agent behavior survives confinement.

### Connection

AgentSpec generalizes enforcement from information-flow policy to customizable domain rules over actions and histories.

## Paper Day 20 — A policy language and reference monitor for agents

### Paper

**AgentSpec: Customizable Runtime Enforcement for Safe and Reliable LLM Agents**

Venue: [ICSE 2026, Research Track](https://conf.researchr.org/details/icse-2026/icse-2026-research-track/29/AgentSpec-Customizable-Runtime-Enforcement-for-Safe-and-Reliable-LLM-Agents) — publication status: peer-reviewed conference paper.

Authors: Haoyu Wang; Chris Poskitt; Jun Sun

Author institutions:

- School of Computing and Information Systems, Singapore Management University

### What problem does this paper solve?

Natural-language safety instructions are interpreted by the same model whose actions they are meant to constrain. They are difficult to audit, inconsistently applied, and incapable of guaranteeing mediation when the model produces an unsafe tool call. Hard-coded checks are stronger but inflexible across coding, embodied, and autonomous systems. AgentSpec asks how developers can state reusable runtime policies outside the agent and enforce them over observed state, history, and action arguments. The policy mechanism must be expressive enough for domain rules, efficient enough to intercept every relevant action, and adaptable when a proposed operation should be blocked or modified. A secondary problem is specification supply: an LLM may help draft rules, but the system must expose the difference between generating a plausible policy and correctly enforcing one.

### Technical core

AgentSpec defines a compact rule language with event triggers, predicates over state, action parameters and history, plus explicit enforcement decisions. A runtime monitor intercepts agent actions and evaluates matching rules outside the model before allowing execution or applying an adaptation. The evaluation covers coding agents, embodied hazards, and autonomous-driving scenarios. It reports blocking more than 90 percent of unsafe coding actions, all tested embodied hazards, and illegal driving behaviors with millisecond-scale rule overhead. Experiments on LLM-generated policies are particularly revealing: embodied-agent rules reach 95.56 percent precision but only 70.96 percent recall, showing that a dependable enforcement engine cannot compensate for omitted rules. Hidden semantic state, individually legal but unsafe action sequences, and incomplete threat models remain important limitations.

### Why it earns one course day

AgentSpec is directly about software engineering for agents: a DSL, event model, monitor, adaptation mechanism, and cross-domain evaluation. As the final primary paper, it forces synthesis across specification quality, complete mediation, monitor visibility, test conflict, and recovery after a blocked action.

### Connection

Document Review II turns the twenty-paper sequence into an end-to-end governance design with explicit trust, state, and recovery boundaries.

## Document Review Day 2 — Correctness, authority, and recovery review

Teams review a deployment dossier for a long-lived, multi-agent software-maintenance service. The dossier must be challenged for specification authority, tool capabilities, delegation and revocation, memory provenance, monitor completeness, transactional side effects, escalation, and microreboot/rollback boundaries. SAGA, ACE, LEGO-Prover, Saltzer–Schroeder, and the intrinsic self-correction negative result may be used as background; no additional primary paper is assigned.

# 23-Session Sequence

| Session day | Type | Assignment |
|---:|---|---|
| 1 | Paper Day 1 | SWE-agent |
| 2 | Paper Day 2 | CodeAct |
| 3 | Paper Day 3 | Murakkab |
| 4 | Paper Day 4 | Information Propagation Effects of Communication Topologies |
| 5 | Paper Day 5 | Multi-Agent Resilience with Faulty Agents |
| 6 | Paper Day 6 | AutoCodeRover |
| 7 | Paper Day 7 | Agentless |
| 8 | Paper Day 8 | CodePlan |
| 9 | Document Review Day 1 | Agent architecture and change-control review |
| 10 | Paper Day 9 | IRIS |
| 11 | Paper Day 10 | CodaMOSA |
| 12 | Paper Day 11 | ImpossibleBench |
| 13 | Paper Day 12 | PropertyGPT |
| 14 | Paper Day 13 | LeanDojo |
| 15 | Paper Day 14 | PAT-Agent |
| 16 | Paper Day 15 | Agentic Memory |
| 17 | Paper Day 16 | Memory Management Impact |
| 18 | Paper Day 17 | Microreboot |
| 19 | Paper Day 18 | AlphaGeometry |
| 20 | Student session | 5-minute: Here's an Interesting Agent Paper/System I Found |
| 21 | Paper Day 19 | CaMeL |
| 22 | Paper Day 20 | AgentSpec |
| 23 | Document Review Day 2 | Correctness, authority, and recovery review |

# Selection Notes

- **Strongest pairings:** SWE-agent/CodeAct, topology/resilience, AutoCodeRover/Agentless, CodaMOSA/ImpossibleBench, LeanDojo/PAT-Agent, Agentic Memory/memory impact, and CaMeL/AgentSpec each expose a real technical tension rather than topical similarity.
- **Embedded topics:** ReAct, Toolformer, OpenHands, LLM-Modulo, QuickCheck, Saltzer–Schroeder, intrinsic self-correction, AgentDojo, LEGO-Prover, ACE, and SAGA remain short background material inside the relevant days and reviews.
- **Deliberately excluded important papers:** RepairAgent, MSG, Draft-Sketch-Prove, LEGO-Prover, CRITIC, ACE, SAGA, G-Designer, SemRef, and Coscientist lost primary slots because a selected paper offered a more orthogonal mechanism or a stronger counterfactual.
- **Remaining gaps:** transactional tool execution, semantic rollback of external effects, shared-memory consistency and provenance, policy synthesis with coverage guarantees, and delegation revocation across open agent ecosystems remain under-supported by mature primary papers.
