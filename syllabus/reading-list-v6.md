# CS239 Reading List v6 — Reviewed 19-Paper Pool

The v6 research pool contains 19 selected papers organized into eight conceptual
units. The date-level Fall 2026 syllabus has only 16 paper-discussion meetings;
its proposed assignments and replacement candidates are recorded in
[paper-list-fall2026.md](paper-list-fall2026.md). A paper may therefore remain
selected in the reviewed research pool without appearing in the provisional
schedule.

Relative to v5, AgentSquare replaces CodeAct and Evolving Orchestration replaces
Agentless in this pool. CodeAct and Agentless remain strong comparison papers.

| Unit | Primary papers |
|---|---:|
| Agent architecture: modules, interface, runtime | 3 |
| Multi-agent organization, communication, coordination | 3 |
| Repair evidence and oracle correctness | 2 |
| Relational and symbolic program analysis | 3 |
| Requirements and implementation conformance | 2 |
| Exact interactive verification | 2 |
| Authority and runtime enforcement | 2 |
| Human oversight and evolving intent | 2 |

## 1. Agent Architecture: Modules, Interface, and Runtime

- **AgentSquare: Automatic LLM Agent Search in Modular Design Space** — ICLR
  2025. Planning, reasoning, tool use, and memory become uniform composable
  modules; architecture search exposes both useful combinations and the limits
  of treating those four modules as a complete agent.
- **SWE-agent: Agent-Computer Interfaces Enable Automated Software
  Engineering** — NeurIPS 2024. Controlled interface ablations make commands,
  observations, feedback, and guardrails explicit design choices.
- **Agentix: An Efficient Serving Engine for LLM Agents as General Programs** —
  NSDI 2026. PLAS and ATLAS schedule dynamic agent programs using attained
  service, dependencies, and distributed critical paths.

**Instructor comparison:** CodeAct supplies the expressive executable-action
alternative to SWE-agent's constrained ACI.

## 2. Multi-Agent Organization, Communication, and Coordination

- **Multi-Agent Collaboration via Evolving Orchestration** — NeurIPS 2025. A
  learned central orchestrator dynamically selects heterogeneous agents defined
  by model, reasoning pattern, and tools, inducing task-specific organizational
  topologies.
- **Understanding the Information Propagation Effects of Communication
  Topologies in LLM-based Multi-Agent Systems** — EMNLP 2025. Counterfactual
  influence analysis separates useful insight propagation from error diffusion
  and connects the result to sparse graph design.
- **TraceFix: Repairing Agent Coordination Protocols with TLA+
  Counterexamples** — ACM CAIS 2026. A topology IR, PlusCal/TLA+ model checking,
  and counterexample-guided repair expose races, deadlocks, and invalid protocol
  interleavings.

**Short framing:** *Large Language Models Miss the Multi-agent Mark* supplies
the classical-MAS checklist—social agency, structured environments,
coordination protocols, and emergence—without counting as a primary paper.

## 3. Repair Evidence and Oracle Correctness

- **AutoCodeSherpa: Symbolic Explanations in AI Coding Agents** — ISSTA 2026,
  accepted in press. Issue-derived input, infection, and output conditions become
  executable properties for localization and independent patch rejection.
- **ImpossibleBench: Measuring LLMs' Propensity of Exploiting Test Cases** —
  ICLR 2026. Conflicting specifications and tests make reward hacking and oracle
  exploitation directly observable.

**Instructor comparison:** Agentless is the fixed localization–repair–validation
control for asking when an open-ended agent loop is actually necessary.

## 4. Relational and Symbolic Program Analysis

- **NESA: Relational Neuro-Symbolic Static Program Analysis** — FSE 2026. A
  restricted Datalog policy joins parser facts with lazily generated neural
  relations under deterministic fixed-point evaluation.
- **IRIS: LLM-Assisted Static Analysis for Detecting Security
  Vulnerabilities** — ICLR 2025. The model proposes source/sink semantics while
  CodeQL owns repository-scale dataflow reachability.
- **Defusing Logic Bombs in Symbolic Execution with LLM-Generated Ghost Code**
  — ISSTA 2026, accepted in press. Untrusted ghost transformations improve the
  solver representation while original-program replay validates each witness.

## 5. Requirements and Implementation Conformance

- **Automating Requirements Formalization: Using LLMs and Low-Complexity
  Distinguishing Traces for Semantic Validation** — ICSE 2026. ARTEMIS uses
  balanced distinguishing traces to make intended semantics the human
  validation target.
- **RFCAudit: AI Agent for Auditing Protocol Implementations Against RFC
  Specifications** — ASE 2025. A hierarchical semantic index and demand-driven
  code queries connect normative clauses to repository evidence.

## 6. Exact Interactive Verification

- **LeanDojo: Theorem Proving with Retrieval-Augmented Language Models** —
  NeurIPS 2023 Datasets and Benchmarks. Exact proof state, scoped retrieval,
  executable tactics, and kernel checking define a rigorous agent–verifier
  environment.
- **Automated Lemma Discovery in Agentic Program Verification** — ASE 2026,
  accepted in press. LemmaNet uses source semantics and proof state to propose
  helper lemmas whose proofs and target VCs are checked by Rocq and Frama-C.

## 7. Authority, Information Flow, and Runtime Enforcement

- **Defeating Prompt Injections by Design** — IEEE SaTML 2026. CaMeL separates
  trusted control from untrusted data and applies provenance-aware capabilities
  to tool execution.
- **AgentSpec: Customizable Runtime Enforcement for Safe and Reliable LLM
  Agents** — ICSE 2026. A stateful policy DSL and external reference monitor
  independently constrain agent actions.

**Instructor context:** SAGA provides authenticated inter-agent contact but not
general attenuated delegation; Atomix remains preprint context for transactional
tool effects.

## 8. Human Oversight and Evolving Intent

- **Semantic Commit: Helping Users Update Intent Specifications for AI Memory at
  Scale** — UIST 2025. Semantic impact analysis and mixed-initiative review
  treat persistent natural-language memory as an evolving specification.
- **Plan-Then-Execute: An Empirical Study of User Trust and Team Performance
  When Using LLM Agents As A Daily Assistant** — CHI 2025. A factorial study
  shows when planning review and execution approval repair errors, create errors,
  or add unproductive workload.

**Instructor context:** Sagas, Beldi, and adjustable autonomy support the final
exercise on approval freshness, authority, idempotency, compensation, and
recovery.

## Deliberate omissions and open gaps

- CodeAct and Agentless remain strong comparisons rather than primary readings;
  their central questions are preserved in Weeks 1 and 3.
- No selected paper provides general concurrent shared-memory consistency,
  transactional semantics for irreversible agent effects, or commit-time
  binding among intent, approval, authority, and world-state version.
- The course therefore ends with one cross-cutting correctness trace rather than
  treating current agent frameworks as complete software architectures.
