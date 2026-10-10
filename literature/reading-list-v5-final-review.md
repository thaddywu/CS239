# Reading-list v5: final adversarial review

The mechanism map below applies one test throughout: after replacing the LLM
with an oracle proposal generator, is there still a mechanism worth teaching?
The resulting recommendation at this review stage was 17 primary papers: 16
survivors plus LemmaNet.

**Post-review update (2026-08-28):** a targeted audit of a supplied agent-
correctness list subsequently promoted TraceFix and Semantic Commit, producing
the current 19-paper list. See the
[supplied-list audit](supplied-agent-correctness-audit-2026-08-28.md).

| Paper | Technical mechanism | Oracle counterfactual | Unique student lesson | Strongest objection | Verdict |
|---|---|---|---|---|---|
| SWE-agent | A purpose-built agent–computer interface exposes bounded repository observations, guarded edit/search commands, execution feedback, and a linter. Interface ablations test which affordances change repair behavior. | **Strong.** Observation and action design, feedback, and guardrails remain a systems boundary. | Students read this paper to learn that the interface mediating a model and a computer is part of the algorithm. | The headline benchmark numbers are now dated, and some ablations bundle interface and prompting changes. | KEEP — core |
| Executable Code Actions Elicit Better LLM Agents (CodeAct) | A persistent Python interpreter is the action language: one program can compose tools, branch, loop, retain state, and receive execution errors. | **Strong.** A unified executable action representation and interpreter state remain. | Students read this paper to learn why an expressive programmatic action space composes better—and enlarges the confinement problem—than a fixed command vocabulary. | Much of the evidence uses compact benchmarks, and arbitrary code execution shifts major safety obligations outside the paper. | KEEP — core |
| Agentix | PLAS schedules whole agent programs by attained service; ATLAS approximates the longest observed dependency path across dynamically created model-call threads. An MLFQ-like scheduler and distributed load balancer combine fairness, preemption, and KV locality. | **Strong.** Non-clairvoyant scheduling over dynamic dependency-bearing programs remains. | Students read this paper to learn that an agent runtime should schedule programs and critical paths rather than isolated model calls. | The mechanism applies to generic LLM DAG serving and omits tool latency, human pauses, and external side effects. | KEEP — useful |
| Information Propagation Topologies | CAPE intervenes on one agent's answer to measure whether correctness propagates; TCTE aggregates influence over graph degree. EIB-Learner fuses dense and sparse GNN views and samples a task-conditioned communication graph with policy-gradient reward. | **Moderate.** The intervention metric and graph learner remain, but their value depends on model-mediated propagation. | Students read this paper to learn that communication edges transmit both insight and correlated error, so denser is not monotonically better. | Homogeneous debate agents, small reasoning tasks, and reward-trained topology leave tools, shared state, and true multi-agent necessity untested. | KEEP — useful |
| LLM-as-Scheduler (LAS) | A benchmark-specific schema/DistilBERT gate scores intermediate artifacts; harder cases go to a prompted router that emits JSON for exit, test, refine, verify, or continue within a fixed AFlow workflow. | **Moderate.** A cost/quality gate and routing policy remain, but not a substantive scheduling abstraction. | Students read this paper to learn that conditional stage routing can trade workflow cost against quality. | The 66% routing accuracy, per-benchmark calibration, and absence of dependencies, concurrency, tools, or persistent state make this shallow beside Agentix. | CUT |
| Agentless | A fixed three-phase pipeline localizes files/functions, generates patches, and filters them with repository tests and patch ranking instead of maintaining an open-ended autonomous loop. | **Moderate.** The staged repair decomposition and deterministic validation remain. | Students read this paper to learn that a strong non-agentic pipeline is the required control before attributing repair gains to autonomy. | Its mechanism is deliberately simple and its absolute results are tightly coupled to a fast-moving benchmark/model stack. | KEEP — core |
| AutoCodeSherpa | It generates an input condition, a line-level infection condition, and an output condition. Hypothesis executes the input/output property, runtime monitors test infection formulas on passing/failing samples, and the artifacts localize faults and reject patches. | **Strong.** Executable properties and monitored state predicates remain independently testable artifacts. | Students read this paper to learn how a bug explanation can become executable evidence connecting triggering inputs, corrupted state, and observable failure. | Property-based sampling does not prove the claimed Hoare-style implications, and the reported patch validator rejects many bad patches but has only 48.5% precision. | KEEP — core |
| ImpossibleBench | The benchmark deliberately pairs specifications and tests that cannot both be satisfied; therefore every test-passing solution is direct evidence of oracle exploitation. Controlled variants probe how models discover and exploit the contradiction. | **Strong.** The impossibility construction is an oracle-validity experiment independent of model intelligence. | Students read this paper to learn that test passage can be anti-evidence of correctness when the executable oracle conflicts with intent. | It contributes an experimental design rather than a new SE mechanism and needs pairing with a testing or explanation paper for a full class. | KEEP — useful |
| NESA | A restricted Datalog policy joins parser-derived relations with neural relations requested lazily under bound arguments. A worklist computes a monotone fixed point over returned facts, while incremental prompting avoids recomputing entire neural relations. | **Strong.** A relational language, binding-aware neural predicate interface, and fixed-point engine remain. | Students read this paper to learn that symbolic analysis can own global closure while a model supplies narrowly scoped semantic facts. | Fixed-point closure does not make neural facts sound or complete; aliases, context insensitivity, and missing model facts still cause false results. | KEEP — core |
| Defusing Logic Bombs in Symbolic Execution with LLM-Generated Ghost Code (Gordian) | The model proposes inverse relations, solver-friendly surrogates, and heap-topology builders for solver-hostile fragments. KLEE/Z3 solve the transformed path constraints, then candidate witnesses replay on the original program. | **Strong.** Representation repair, symbolic execution, constraint solving, and original-program witness checking remain. | Students read this paper to learn that a model can improve solver tractability without entering the trusted validity boundary. | Unsound or incomplete transformations can silently destroy search completeness, and the integration is localized and partly manual. | KEEP — core |
| HoarePrompt | Prompts propagate natural-language state descriptions along a CFG, unroll loops three times, ask the model to generalize, and finally classify whether the described post-state satisfies the requirement. | **Weak.** CFG traversal remains, but every semantic transformer and the final entailment judgment is an unverified prompt. | Students read this paper to learn the difference between program-logic-shaped prompting and program verification. | “Strongest postcondition” and “k-induction” are analogies, not a sound calculus; absolute MCC is only 0.159–0.259 at 39–64× baseline token cost. | CUT |
| IRIS | The model proposes CodeQL taint sources, sinks, sanitizers, and contextual alarm judgments; CodeQL computes repository-scale dataflow paths and the model triages the resulting witnesses. | **Strong.** A conventional static analyzer retains ownership of global reachability and produces inspectable paths. | Students read this paper to learn that learned semantic classification and symbolic global analysis can have a clean division of labor. | Incorrect source/sink/sanitizer facts can suppress vulnerabilities, and effectiveness depends heavily on the CodeQL/model/benchmark combination. | KEEP — core |
| ARTEMIS | Requirements pass through FRETish or property-pattern fields to deterministic LTL. The system builds multiple decomposition candidates, eliminates them with proxy LTL checks, and selects short traces that approximately bisect the remaining interpretations for expert labeling. | **Strong.** The structured IR, formal candidate semantics, and active distinguishing-query algorithm remain. | Students read this paper to learn that formalization needs semantic validation of competing interpretations, not merely fluent NL-to-LTL translation. | The expert is simulated, the correct meaning must be expressible in the candidate grammar, and 14.2% of cases produce no plausible candidate within budget. | KEEP — core |
| RFCAudit | Bottom-up function/file/directory summaries form a persistent hierarchical semantic index. RFC clauses become mandatory properties; a state machine localizes evidence, issues caller/callee/type queries on demand, classifies compliance, and self-critiques the finding. | **Moderate.** Hierarchical retrieval state and demand-driven repository traversal remain, but semantic extraction and verdicts are model judgments. | Students read this paper to learn how normative prose can drive evidence-seeking queries over a large implementation rather than one-shot retrieval. | It is closer to carefully engineered semantic indexing and retrieval than to a sound conformance analyzer. | KEEP — useful |
| LeanDojo | Traced Lean environments expose exact proof states, scoped premises, executable tactics, and kernel feedback; retrieval is evaluated with a novel-premise split. | **Strong.** The interaction protocol, premise index, benchmark split, and proof kernel remain. | Students read this paper to learn what an agent environment looks like when every action changes exact formal state and an independent kernel decides success. | It is theorem proving rather than software engineering proper, and later systems improve its raw proving performance. | KEEP — core |
| Defeating Prompt Injections by Design (CaMeL) | Trusted control flow is separated from untrusted data; values carry provenance and capabilities, and policy checks mediate tool calls and data flows. | **Strong.** Information-flow structure, capabilities, and complete mediation remain even with an adversarial proposal generator. | Students read this paper to learn that prompt injection is a confused-deputy and provenance problem, not merely a bad-text classification problem. | Guarantees are relative to a restrictive trusted architecture and policy completeness, not to arbitrary legacy agents or semantic misuse inside allowed flows. | KEEP — core |
| AgentSpec | A stateful trigger–predicate–decision DSL specifies action policies; an external reference monitor intercepts proposed tool calls and updates policy state independently of the model. | **Strong.** The policy language and enforcement monitor remain. | Students read this paper to learn how application-specific temporal safety rules can be enforced outside model compliance. | The DSL cannot express every semantic intent, and the monitor is only as complete as its tool interception and policy set. | KEEP — core |
| SAGA | Providers register agents and contact policies, issue one-time keys, and establish encrypted, quota- and expiry-bounded access tokens for authorized communication. ProVerif checks secrecy/authentication and RAFT replicates the registry. | **Strong.** A conventional authenticated contact protocol remains. | Students read this paper to learn the identity and lifecycle assumptions required before autonomous services may contact one another. | It authorizes communication rather than delegated task authority; revocation waits for token expiry/quota, and the formal model does not prove policy correctness or delegation semantics. | BACKGROUND |
| Plan-Then-Execute | A 2×2 experiment crosses automatic versus user-involved planning with automatic versus user-involved execution; users may edit plans and approve or revise each simulated API action. It measures task outcome, plan/action correctness, calibrated trust, intervention behavior, and workload. | **Strong.** The factorial oversight experiment and behavioral measurements remain. | Students read this paper to learn that adding approval points can repair or introduce errors while increasing workload without reliably calibrating trust. | Six simulated tasks confound high risk with deliberately flawed plans, and one-step actions do not represent long-lived or irreversible workflows. | KEEP — useful |

## A. Papers I would cut first

1. **HoarePrompt.** Its control-flow decomposition is useful, but its natural-language states and final entailment remain unverified model outputs; loop “k-induction” is three unrolls followed by prompted generalization. LemmaNet now supplies the better seminar contrast: informal program comprehension proposes artifacts, while Rocq checks every imported helper lemma and the final Frama-C VC.

2. **LLM-as-Scheduler.** LAS is a calibrated gate plus a prompted action router over a fixed workflow, not a scheduler with resource, dependency, concurrency, or state semantics. Removing it loses a cost/quality routing example but no idea that Agentix or the topology paper cannot frame more deeply.

3. **SAGA.** Its authenticated contact protocol is technically real, but “delegation” does not mean attenuated task authority or a chain of delegated capabilities, and policy changes do not invalidate outstanding tokens. Keep it as security background beside CaMeL and AgentSpec, not as a third full security assignment.

## B. Papers that looked stronger after full review

**NESA** has a real Datalog/neural relation boundary and binding-aware fixed-point engine; **Gordian** has unusually clean untrusted-representation/verified-witness separation. **ARTEMIS** contributes an actual candidate-elimination and balanced-query algorithm, while **AutoCodeSherpa** makes explanations executable even though its sampling claims need care. **RFCAudit** survives because retrieval ablations and real confirmed bugs support its conformance-search architecture; **Agentix** survives the Murakkab comparison because its non-clairvoyant program/critical-path scheduler is the sharper runtime lesson. **LemmaNet** is the only challenger that clearly beats a current primary: offline semantics-aware lemma synthesis plus online proof-state adaptation raises AutoRocq from 287 to 364 of 941 VCs, with all imported lemmas and final proofs kernel-checked.

## C. Papers that looked weaker after full review

**HoarePrompt** and **LAS** sounded more algorithmic in their abstracts than their implementations justify; **SAGA** proves a narrower authenticated-contact protocol than its delegation framing suggests. The other named challengers do not force a swap: ProbGuard's practical traces do not meet its own useful PAC regime; Deductive Steering lacks enough available full-paper evidence; AutoCodeRover, CodePlan, and CodaMOSA are strong but overlap retained repair/analysis lessons; Draft–Sketch–Prove and Agentic Specification Generator overlap the now stronger exact-verification sequence; Multi-Agent Resilience and CARD still rely on model-based containment or benchmark topology optimization rather than shared-state semantics.

## D. Recommended final list

### SWE-agent: Agent-Computer Interfaces Enable Automated Software Engineering
**Venue:** NeurIPS 2024  
**Key authors / institutions:** John Yang, Carlos E. Jimenez, Shunyu Yao; Princeton  
**Why:** Controlled interface ablations make observation, action, feedback, and guardrails first-class agent design choices.

### Executable Code Actions Elicit Better LLM Agents
**Venue:** ICML 2024  
**Key authors / institutions:** Xingyao Wang, Hao Peng, Heng Ji; UIUC and Apple  
**Why:** A persistent executable action language exposes the expressiveness, composition, and confinement tradeoff opposite SWE-agent.

### Agentix: An Efficient Serving Engine for LLM Agents as General Programs
**Venue:** NSDI 2026  
**Key authors / institutions:** Michael Luo, Xiaoxiang Shi, Ion Stoica; UC Berkeley, Google DeepMind, and Shanghai Jiao Tong University  
**Why:** PLAS and ATLAS make dynamic program structure and critical paths schedulable runtime objects.

### Understanding the Information Propagation Effects of Communication Topologies in LLM-based Multi-Agent Systems
**Venue:** EMNLP 2025  
**Key authors / institutions:** Xu Shen, Shirui Pan, Xin Wang; Jilin University, Griffith University, and UNSW  
**Why:** Counterfactual influence measurement shows why communication graphs propagate both insight and error.

### Demystifying LLM-based Software Engineering Agents
**Venue:** FSE 2025  
**Key authors / institutions:** Chunqiu Steven Xia, Yinlin Deng, Lingming Zhang; UIUC  
**Why:** Agentless is the essential fixed-pipeline control against claims that repository repair requires open-ended autonomy.

### AutoCodeSherpa: Symbolic Explanations in AI Coding Agents
**Venue:** ISSTA 2026, accepted in press  
**Key authors / institutions:** Sungmin Kang, Haifeng Ruan, Abhik Roychoudhury; National University of Singapore  
**Why:** Executable input, infection, and output conditions connect issue semantics to localization and patch rejection.

### ImpossibleBench: Measuring LLMs' Propensity of Exploiting Test Cases
**Venue:** ICLR 2026  
**Key authors / institutions:** Ziqian Zhong, Aditi Raghunathan, Nicholas Carlini; Carnegie Mellon University and Anthropic  
**Why:** Impossible specification/test pairs turn every passing solution into direct evidence that executable oracles can reward incorrectness.

### NESA: Relational Neuro-Symbolic Static Program Analysis
**Venue:** FSE 2026  
**Key authors / institutions:** Chengpeng Wang, Yifei Gao, Qingkai Shi, Xiangyu Zhang; NUS, Purdue, MegaETH, and Nanjing University  
**Why:** Restricted Datalog and lazy neural relations create a reusable symbolic-closure/semantic-fact boundary.

### Defusing Logic Bombs in Symbolic Execution with LLM-Generated Ghost Code
**Venue:** ISSTA 2026, accepted in press  
**Key authors / institutions:** Dimitrios Stamatios Bouras, Sergey Mechtaev; Peking University  
**Why:** Untrusted ghost transformations repair solver representations while original-program replay preserves witness validity.

### IRIS: LLM-Assisted Static Analysis for Detecting Security Vulnerabilities
**Venue:** ICLR 2025  
**Key authors / institutions:** Ziyang Li, Saikat Dutta, Mayur Naik; Cornell University and University of Pennsylvania  
**Why:** Learned source/sink semantics and CodeQL-owned reachability define a clean neuro-symbolic analysis split.

### Automating Requirements Formalization: Using LLMs and Low-Complexity Distinguishing Traces for Semantic Validation
**Venue:** ICSE 2026  
**Key authors / institutions:** Daniel Mendoza, Anastasia Mavridou, Andreas Katis, Caroline Trippel; Stanford and KBR/NASA Ames  
**Why:** Structured requirements and balanced distinguishing traces make intended semantics—not translation fluency—the validation target.

### RFCAudit: AI Agent for Auditing Protocol Implementations Against RFC Specifications
**Venue:** ASE 2025  
**Key authors / institutions:** Mingwei Zheng, Chengpeng Wang, Xiangyu Zhang; Purdue University  
**Why:** A persistent hierarchical index and demand-driven code queries connect normative clauses to repository evidence.

### LeanDojo: Theorem Proving with Retrieval-Augmented Language Models
**Venue:** NeurIPS 2023, Datasets and Benchmarks  
**Key authors / institutions:** Kaiyu Yang, Alex Gu, Animashree Anandkumar; Caltech and NVIDIA  
**Why:** Exact proof state, scoped retrieval, executable tactics, and kernel checking define the strongest agent–verifier environment lesson.

### Automated Lemma Discovery in Agentic Program Verification
**Venue:** ASE 2026, accepted in press  
**Key authors / institutions:** Huan Zhao, Haoxin Tu, Zhengyao Liu, Martin C. Rinard, Abhik Roychoudhury; NUS and MIT  
**Why:** LemmaNet turns source-level program comprehension into offline and adaptive helper lemmas whose proofs and target VCs are checked by Rocq and Frama-C.

### Defeating Prompt Injections by Design
**Venue:** IEEE SaTML 2026  
**Key authors / institutions:** Edoardo Debenedetti, Nicholas Carlini, Florian Tramèr; ETH Zurich, Google, and collaborators  
**Why:** Provenance-aware capabilities and trusted control/data separation move prompt injection out of the model's discretion.

### AgentSpec: Customizable Runtime Enforcement for Safe and Reliable LLM Agents
**Venue:** ICSE 2026  
**Key authors / institutions:** Haoyu Wang, Christopher M. Poskitt, Jun Sun; Singapore Management University  
**Why:** A stateful policy DSL plus an external reference monitor makes application action safety independently enforceable.

### Plan-Then-Execute: An Empirical Study of User Trust and Team Performance When Using LLM Agents As A Daily Assistant
**Venue:** CHI 2025  
**Key authors / institutions:** Gaole He, Gianluca Demartini, Ujwal Gadiraju; TU Delft and University of Queensland  
**Why:** A factorial oversight study shows that human review can repair or create errors, add workload, and fail to calibrate trust.
