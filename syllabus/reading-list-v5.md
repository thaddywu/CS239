# CS239 Reading List v5 — Final

The final list contains 19 primary papers. LAS and HoarePrompt are cut; SAGA
becomes instructor background; LemmaNet enters as the checked program-
verification replacement. A later supplied-list audit adds TraceFix for
coordination correctness and Semantic Commit for evolving intent. Detailed
reasons are in [the final review](../literature/reading-list-v5-final-review.md)
and [the supplied-list audit](../literature/supplied-agent-correctness-audit-2026-08-28.md).

| Block | Primary papers |
|---|---:|
| Interfaces and agent-program runtimes | 3 |
| Communication, coordination correctness, and autonomy controls | 3 |
| Repair, explanation, and oracle quality | 2 |
| Relational and symbolic program analysis | 3 |
| Requirements and conformance | 2 |
| Exact interactive verification | 2 |
| Authority and runtime enforcement | 2 |
| Human oversight and evolving intent | 2 |

## Interfaces and Agent-Program Runtimes

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

## Communication, Coordination Correctness, and Autonomy Controls

### Understanding the Information Propagation Effects of Communication Topologies in LLM-based Multi-Agent Systems
**Venue:** EMNLP 2025  
**Key authors / institutions:** Xu Shen, Shirui Pan, Xin Wang; Jilin University, Griffith University, and UNSW  
**Why:** Counterfactual influence measurement shows why communication graphs propagate both insight and error.

### TraceFix: Repairing Agent Coordination Protocols with TLA+ Counterexamples
**Venue:** ACM CAIS 2026  
**Key authors / institutions:** Shuren Xia, Qiwei Li, Taqiya Ehsan, Jorge Ortiz; Rutgers University  
**Why:** A topology IR, PlusCal/TLA+ model checking, counterexample-guided repair, and runtime monitoring make races, deadlocks, and protocol deviation explicit agent-engineering problems.

### Demystifying LLM-based Software Engineering Agents
**Venue:** FSE 2025  
**Key authors / institutions:** Chunqiu Steven Xia, Yinlin Deng, Lingming Zhang; UIUC  
**Why:** Agentless is the essential fixed-pipeline control against claims that repository repair requires open-ended autonomy.

## Repair, Executable Explanation, and Oracle Quality

### AutoCodeSherpa: Symbolic Explanations in AI Coding Agents
**Venue:** ISSTA 2026, accepted in press  
**Key authors / institutions:** Sungmin Kang, Haifeng Ruan, Abhik Roychoudhury; National University of Singapore  
**Why:** Executable input, infection, and output conditions connect issue semantics to localization and patch rejection.

### ImpossibleBench: Measuring LLMs' Propensity of Exploiting Test Cases
**Venue:** ICLR 2026  
**Key authors / institutions:** Ziqian Zhong, Aditi Raghunathan, Nicholas Carlini; Carnegie Mellon University and Anthropic  
**Why:** Impossible specification/test pairs turn every passing solution into direct evidence that executable oracles can reward incorrectness.

## Relational and Symbolic Program Analysis

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

## Requirements and Implementation Conformance

### Automating Requirements Formalization: Using LLMs and Low-Complexity Distinguishing Traces for Semantic Validation
**Venue:** ICSE 2026  
**Key authors / institutions:** Daniel Mendoza, Anastasia Mavridou, Andreas Katis, Caroline Trippel; Stanford and KBR/NASA Ames  
**Why:** Structured requirements and balanced distinguishing traces make intended semantics—not translation fluency—the validation target.

### RFCAudit: AI Agent for Auditing Protocol Implementations Against RFC Specifications
**Venue:** ASE 2025  
**Key authors / institutions:** Mingwei Zheng, Chengpeng Wang, Xiangyu Zhang; Purdue University  
**Why:** A persistent hierarchical index and demand-driven code queries connect normative clauses to repository evidence.

## Exact Interactive Verification

### LeanDojo: Theorem Proving with Retrieval-Augmented Language Models
**Venue:** NeurIPS 2023, Datasets and Benchmarks  
**Key authors / institutions:** Kaiyu Yang, Alex Gu, Animashree Anandkumar; Caltech and NVIDIA  
**Why:** Exact proof state, scoped retrieval, executable tactics, and kernel checking define the strongest agent–verifier environment lesson.

### Automated Lemma Discovery in Agentic Program Verification
**Venue:** ASE 2026, accepted in press  
**Key authors / institutions:** Huan Zhao, Haoxin Tu, Zhengyao Liu, Martin C. Rinard, Abhik Roychoudhury; NUS and MIT  
**Why:** LemmaNet turns source-level program comprehension into offline and adaptive helper lemmas whose proofs and target VCs are checked by Rocq and Frama-C.

## Authority, Information Flow, and Runtime Enforcement

### Defeating Prompt Injections by Design
**Venue:** IEEE SaTML 2026  
**Key authors / institutions:** Edoardo Debenedetti, Nicholas Carlini, Florian Tramèr; ETH Zurich, Google, and collaborators  
**Why:** Provenance-aware capabilities and trusted control/data separation move prompt injection out of the model's discretion.

### AgentSpec: Customizable Runtime Enforcement for Safe and Reliable LLM Agents
**Venue:** ICSE 2026  
**Key authors / institutions:** Haoyu Wang, Christopher M. Poskitt, Jun Sun; Singapore Management University  
**Why:** A stateful policy DSL plus an external reference monitor makes application action safety independently enforceable.

## Human Oversight and Evolving Intent

### Semantic Commit: Helping Users Update Intent Specifications for AI Memory at Scale
**Venue:** UIST 2025  
**Key authors / institutions:** Priyan Vaithilingam, Munyeong Kim, Frida-Cecilia Acosta-Parenteau, Daniel Lee, Amine Mhedhbi, Elena L. Glassman, Ian Arawjo; Harvard, Université de Montréal, Adobe, and Polytechnique Montréal  
**Why:** Semantic impact analysis and mixed-initiative conflict review treat persistent natural-language memory and rules as evolving specifications rather than one-shot prompts.

### Plan-Then-Execute: An Empirical Study of User Trust and Team Performance When Using LLM Agents As A Daily Assistant
**Venue:** CHI 2025  
**Key authors / institutions:** Gaole He, Gianluca Demartini, Ujwal Gadiraju; TU Delft and University of Queensland  
**Why:** A factorial oversight study shows that human review can repair or create errors, add workload, and fail to calibrate trust.

## Instructor Background and Explicit Gaps

- **SAGA** supplies authenticated inter-agent contact, provider-registry, and
  token-lifecycle vocabulary, but does not provide general attenuated task
  delegation or immediate revocation.
- **Sagas**, **Beldi**, and **Towards Adjustable Autonomy for the Real World**
  supply effect-recovery and control-transfer foundations without adding primary
  assignments.
- **Atomix** is the strongest current preprint on transactional settlement of
  tool effects; it remains frontier context rather than a primary assignment.
- No peer-reviewed 2023--2026 paper cleared the bar for transactional semantics
  over irreversible agent effects, approval-to-commit binding, or general
  concurrent shared-state consistency. These remain design exercises; TraceFix
  covers coordination protocols rather than arbitrary shared-state semantics.
