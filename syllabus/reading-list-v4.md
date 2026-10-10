# CS239 Reading List v4

Working structure: approximately eight weeks, with 19 primary papers. Papers
listed as alternatives are not additional assignments.

| Block | Approximate time | Primary papers |
|---|---:|---:|
| Agent architecture | 1 week | 2 |
| Multi-agent design | 1–1.5 weeks | 3 |
| Agentic software engineering | 3.5–4 weeks | 9 |
| Correctness and safety | 2 weeks | 5 |

## Theme: Agent Architecture and Frameworks

**Core question:** Which responsibilities belong in the model, the agent-computer interface, and the execution runtime?

**Primary candidates**

### SWE-agent: Agent-Computer Interfaces Enable Automated Software Engineering
**Venue:** NeurIPS 2024  
**Key authors / institutions:** John Yang, Carlos E. Jimenez, Shunyu Yao; Princeton  
**Why this paper:** It makes the agent-computer interface an ablatable technical object: bounded observations, purpose-built commands, feedback, and guardrails all change repository-repair behavior. It establishes the constrained-interface side of the course's first design debate.

### Executable Code Actions Elicit Better LLM Agents
**Venue:** ICML 2024  
**Key authors / institutions:** Xingyao Wang, Hao Peng, Heng Ji; UIUC and Apple  
**Why this paper:** CodeAct makes a persistent Python interpreter the common action language, so composition, control flow, and state are executable rather than narrated. Read against SWE-agent, it exposes the tradeoff between expressiveness and confinement.

**Background, not primary:** ReAct, Toolformer, MCP, A2A, Strands, OpenHands,
and memory/context mechanisms can supply vocabulary and tutorials. Murakkab is
removed because resource-aware cloud orchestration is not the architectural
question this block is now meant to answer.

## Theme: Multi-Agent Design

**Core question:** Which communication structures and fault-containment mechanisms make several agents more useful than repeated calls to one model?

**Primary candidates**

### Understanding the Information Propagation Effects of Communication Topologies in LLM-based Multi-Agent Systems
**Venue:** EMNLP 2025  
**Key authors / institutions:** Xu Shen, Shirui Pan, Xin Wang; Jilin University, Griffith University, and UNSW  
**Why this paper:** CAPE intervenes on one agent's output to measure how insight and error propagate through a communication graph; EIB-Learner then searches for a useful sparse topology. It asks why a graph works rather than treating topology as a cosmetic workflow choice.

### CARD: Towards Conditional Design of Multi-Agent Topological Structures
**Venue:** ICLR 2026  
**Key authors / institutions:** Tongtong Wu, Guilin Qi, Shirui Pan, Gholamreza Haffari; Monash, Southeast University, Griffith  
**Why this paper:** CARD conditions a learned communication graph on model capability, tool availability, and source quality, then changes edges at runtime without retraining. It turns coordination topology into an adaptive protocol decision, although its environmental shifts remain simulated.

### On the Resilience of LLM-Based Multi-Agent Collaboration with Faulty Agents
**Venue:** ICML 2025  
**Key authors / institutions:** Jen-Tse Huang, Michael R. Lyu, Maarten Sap; CUHK, Tsinghua, CMU, and collaborators  
**Why this paper:** Controlled fault transformation and injection make failure propagation measurable across collaboration structures; Challenger and Inspector are explicit containment mechanisms. It keeps its slot because the other two readings now supply the missing coordination-design foundation.

**Background, not primary:** State Delta Encoding is a technically real
communication protocol, but it requires white-box hidden-state transfer and
does not address shared world state, concurrency, or consistency. SAGA returns
later under authority and delegation.

## Theme: Software Understanding, Program Analysis, and Reverse Engineering

**Core question:** Which software representations let an agent reason beyond its context window and recover structure rather than merely retrieve text?

**Primary candidates**

### CodePlan: Repository-level Coding using LLMs and Planning
**Venue:** FSE 2024  
**Key authors / institutions:** Ramakrishna Bairi, Aditya Kanade, Sriram Rajamani; Microsoft Research  
**Why this paper:** A change-impact relation grows and updates an edit-obligation DAG after each modification. The plan is grounded in repository dependencies, making this a software-specific planning mechanism rather than generic tree search.

### IRIS: LLM-Assisted Static Analysis for Detecting Security Vulnerabilities
**Venue:** ICLR 2025  
**Key authors / institutions:** Ziyang Li, Saikat Dutta, Mayur Naik; Cornell and University of Pennsylvania  
**Why this paper:** The model infers missing taint specifications and contextual facts while CodeQL owns repository-scale reachability. The division of labor is a clean example of probabilistic semantic proposal coupled to symbolic program analysis.

**Alternative**

### RepoProbe: Benchmarking Architecture-Aware Repository Comprehension with Checklists
**Venue:** ASE 2026  
**Key authors / institutions:** Yuexi Yang, Alyssa Wu, Zhen Qin; Zhejiang University and Tencent Hunyuan  
**Why this paper:** Real GitHub Discussions and atomic checklists expose “edit bias”: models often propose plausible changes before understanding the architecture. It is an excellent negative/evaluation reading, but not yet an architecture-recovery mechanism.

**Background, not primary:** *Software Reflexion Models* and the 2025 ACE
design-understanding paper provide strong non-agent abstractions. Recent
agent/LLM architecture-recovery papers remain dominated by prompting,
self-reflection, or early-result evaluations, so no weak modern paper is forced
into a primary slot.

## Theme: Coding, Debugging, and Repair

**Core question:** How much autonomy does repair require, and what program structure should control localization and revision?

**Primary candidates**

### AutoCodeRover: Autonomous Program Improvement
**Venue:** ISSTA 2024  
**Key authors / institutions:** Yuntong Zhang, Abhik Roychoudhury; National University of Singapore  
**Why this paper:** AST-aware navigation, software-entity search, fault-localization evidence, and test-guided revision shape an exploratory repair loop. It represents autonomous search constrained by program structure.

### Demystifying LLM-based Software Engineering Agents
**Venue:** FSE 2025  
**Key authors / institutions:** Chunqiu Steven Xia, Yinlin Deng, Lingming Zhang; UIUC  
**Why this paper:** Agentless uses fixed localization, repair, and validation stages as a strong control against claims that open-ended autonomy is necessary. Its contrast with AutoCodeRover is more valuable than adding another retrieve-patch-test agent.

## Theme: Testing and Specification

**Core question:** What evidence is sufficient to accept an agent-generated software change?

**Primary candidates**

### CodaMOSA: Escaping Coverage Plateaus in Test Generation with Pre-trained Large Language Models
**Venue:** ICSE 2023  
**Key authors / institutions:** Caroline Lemieux, Jeevana Priya Inala, Shuvendu Lahiri, Siddhartha Sen; Microsoft Research  
**Why this paper:** Evolutionary search runs until measured coverage stagnates, invokes a model only to escape the plateau, and then resumes algorithmic search. It still provides the clearest hybrid testing mechanism after comparison with 2024–2026 alternatives.

### ImpossibleBench: Measuring LLMs' Propensity of Exploiting Test Cases
**Venue:** ICLR 2026  
**Key authors / institutions:** Ziqian Zhong, Aditi Raghunathan, Nicholas Carlini; Carnegie Mellon and Anthropic  
**Why this paper:** Deliberately impossible test/specification combinations turn every passing solution into evidence of specification gaming. It breaks the convenient equivalence between test passage, requirement satisfaction, and correctness.

### Agentic Specification Generator for Move Programs
**Venue:** ASE 2025  
**Key authors / institutions:** Yu-Fu Fu, Meng Xu, Taesoo Kim; Georgia Tech  
**Why this paper:** Specialized generators produce different contract clauses, selective inlining exposes relevant semantics, and Move Prover feedback repairs candidates. It advances the sequence from tests to reusable, independently checked specifications without pretending that prover acceptance guarantees intent fidelity.

## Theme: Formalization, Verification, and Theorem Proving

**Core question:** Where should probabilistic proposal stop and exact reasoning begin?

**Primary candidates**

### LeanDojo: Theorem Proving with Retrieval-Augmented Language Models
**Venue:** NeurIPS 2023 (Datasets and Benchmarks)  
**Key authors / institutions:** Kaiyu Yang, Alex Gu, Animashree Anandkumar; Caltech and NVIDIA  
**Why this paper:** A traced Lean environment exposes scoped premises, typed proof states, executable tactics, and kernel feedback. The runtime and novel-premise split make it the strongest reference point for exact validator-mediated agent interaction.

### Draft, Sketch, and Prove: Guiding Formal Theorem Provers with Informal Proofs
**Venue:** ICLR 2023  
**Key authors / institutions:** Albert Q. Jiang, Sean Welleck, Mateja Jamnik, Guillaume Lample, Yuhuai Wu; Cambridge, NYU, Meta, and collaborators  
**Why this paper:** An informal proof becomes a formal sketch with holes that an existing prover must discharge. The sketch is an explicit interface contract between uncertain global reasoning and exact local proof search, distinct from tactic retrieval alone.

## Theme: Correctness and Safety of Agent-Leveraged Applications

**Core question:** What changes when a probabilistic component interprets intent, sequences actions, exercises authority, and creates durable effects?

### Subquestion: Specification and intent

The primary readings are **ImpossibleBench** and **Agentic Specification
Generator**, assigned above. Their joint question is what to do when natural
language, tests, inferred properties, and formal checks disagree.

### Subquestion: State, time, and external effects

**Primary candidate**

### Sagas
**Venue:** ACM SIGMOD 1987  
**Key authors / institutions:** Hector Garcia-Molina, Kenneth Salem; Princeton  
**Why this paper:** Sagas distinguishes atomic rollback from semantic compensation and forward recovery after visible partial execution. One foundational systems paper earns the scarce slot because peer-reviewed agent literature still lacks comparable semantics for irreversible multi-tool effects.

**Alternative**

### Fault-tolerant and transactional stateful serverless workflows
**Venue:** OSDI 2020  
**Key authors / institutions:** Haoran Zhang, Adney Cardoza, Sebastian Angel, Vincent Liu; University of Pennsylvania  
**Why this paper:** Beldi adds intent logging, exactly-once re-execution, invocation IDs, and transactional opacity inside a mediated workflow boundary. Choose it instead of Sagas when implementation detail matters more than open-world compensation; assigning both would over-allocate foundational systems work.

### Subquestion: Authority, information flow, and delegation

**Primary candidates**

### Defeating Prompt Injections by Design
**Venue:** IEEE SaTML 2026  
**Key authors / institutions:** Edoardo Debenedetti, Nicholas Carlini, Florian Tramèr; ETH Zurich, Google, and collaborators  
**Why this paper:** CaMeL separates trusted control from untrusted data and attaches provenance-aware capabilities to values. It treats prompt injection as a confused-deputy and information-flow problem rather than a string-classification problem.

### AgentSpec: Customizable Runtime Enforcement for Safe and Reliable LLM Agents
**Venue:** ICSE 2026  
**Key authors / institutions:** Haoyu Wang, Chris Poskitt, Jun Sun; Singapore Management University  
**Why this paper:** A stateful policy DSL and external reference monitor intercept proposed actions independently of model compliance. It supplies the software-engineering enforcement counterpart to CaMeL's construction-based architecture.

### SAGA: A Security Architecture for Governing AI Agentic Systems
**Venue:** NDSS 2026  
**Key authors / institutions:** Georgios Syros, Anshuman Suri, Cristina Nita-Rotaru, Alina Oprea; Northeastern University  
**Why this paper:** Provider-mediated registration and cryptographic tokens make inter-agent identity, authorization, and delegation a protocol. It retains a primary slot because neither CaMeL nor AgentSpec covers inter-agent authority, although its trusted-provider assumption and small task evaluation should be challenged.

### Subquestion: Human oversight and control transfer

**Primary candidate**

### Plan-Then-Execute: An Empirical Study of User Trust and Team Performance When Using LLM Agents As A Daily Assistant
**Venue:** CHI 2025  
**Key authors / institutions:** Gaole He, Gianluca Demartini, Ujwal Gadiraju; TU Delft and University of Queensland  
**Why this paper:** A 2×2 study separates user involvement in planning from involvement in stepwise execution across risky tool tasks. Human review sometimes repairs plans or actions, but does not reliably calibrate trust, raises cognitive load, and can damage correct plans—precisely the evidence needed to design selective control transfer.

**Alternative**

### Towards Adjustable Autonomy for the Real World
**Venue:** JAIR 2002  
**Key authors / institutions:** Paul Scerri, David Pynadath, Milind Tambe; USC/ISI  
**Why this paper:** Transfer-of-control strategies use an MDP to trade decision quality, response uncertainty, delay, and coordination cost. It remains the stronger formal model of when to escalate, but CHI 2025 is the better primary for modern LLM-agent oversight.
