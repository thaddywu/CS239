# Coverage Matrix

“Explored level” measures this repository's search coverage, not the field's
maturity. **Audit confidence** asks how likely the current syllabus judgment is
to survive another focused search. Counts include selected and strong candidates
and are not additive across topics.

| Topic | Explored level | Selected/strong | Literature maturity | Audit confidence | Judgment | Last audited | Decision-relevant evidence / remaining gap |
|---|---|---:|---|---|---|---|---|
| Agent interfaces / harness | high | 5 | high | high | standalone/core | 2026-08-29 | A focused survey audit adds a framing layer: Bajoria et al. supplies the broadest current engineering map, while Wang plus Guo is the more established single-/multi-agent pair; AgentSquare, SWE-agent, CodeAct, and Agentix remain the mechanism-bearing readings |
| Agent serving / performance | high | 2 | medium/high | high | embed/core | 2026-08-29 | Agentix's PLAS/ATLAS scheduling remains a very deep alternate, but v7 spends its two architecture weeks on ingredients, interfaces, orchestration, and communication rather than adding a serving meeting |
| Tools and tool use | high | 3 | high | high | embed/core | 2026-08-27 | CodeAct composes actions and SWE-agent constrains them; protocol versioning, capability discovery, and transactional tool semantics remain thin |
| Planning / workflow scheduling | high | 2 | medium | high | embed/background | 2026-08-28 | LAS was cut after full review because its calibrated gate and prompted router lack scheduling semantics; CodePlan and LLM-Modulo remain mechanism-bearing alternatives |
| Multi-agent communication | high | 6 | medium/high | high | embed/core | 2026-08-29 | V7 pairs Evolving Orchestration's heterogeneous dynamic allocation with Information Propagation's causal communication analysis; TraceFix moves to correctness/runtime assurance, and general shared-state consistency remains absent |
| Memory / context management | high | 3 | high for policies; low for consistency | high | background | 2026-08-27 | AgeMem and lifecycle studies are strong, but AMA does not supply versioning, isolation, or conflict semantics; no standalone block |
| Program repair | high | 4 | high | high | standalone/core | 2026-08-29 | AutoCodeSherpa supplies executable issue evidence; Agentless, AutoCodeRover, and CodaMOSA remain strong alternatives; PSearch is an exact-fit MCTS watch item whose full paper was unavailable |
| Testing / oracle quality | high | 4 | high | high | standalone/core | 2026-08-29 | AutoCodeSherpa and ImpossibleBench contrast executable properties with gameable tests; ImpossibleBench is v7's sole evaluation-first exception, while CANDOR's model-panel consensus lacks an independent oracle |
| Relational / static program analysis | high | 5 | medium/high, fast-moving | high | standalone/core | 2026-08-27 | NESA restricted Datalog and IRIS CodeQL taint analysis are selected; LogicLoc, ACTaint, and Semia define direct challengers |
| Symbolic execution / constraints | high | 2 | medium/high | high | standalone/core | 2026-08-27 | Gordian's ghost code assists KLEE/Z3 while original-program rechecking preserves witness validity; synthesis completeness remains open |
| Agentic program synthesis / invariants | medium/high | 1 | emerging | medium | future targeted search | 2026-08-27 | Deductive Steering is an exact-fit SMT-guided candidate, but only abstract-level accepted-in-press evidence was auditable; no primary selected |
| Structured correctness reasoning | high | 2 | medium/high | high | embed/core | 2026-08-28 | HoarePrompt was cut as program-logic-shaped prompting; LemmaNet now supplies checked source-aware helper lemmas while Gordian preserves original-program witness validity |
| Requirements formalization | high | 4 | medium/high | high | standalone/core | 2026-08-27 | ARTEMIS's structured language and balanced distinguishing traces replace MSG; intent fidelity outside the supported language is unresolved |
| Implementation/spec conformance | high | 2 | medium | medium/high | embed/core | 2026-08-27 | RFCAudit adds hierarchical semantic indexing and demand-driven RFC checks; semantic coverage remains model-dependent |
| Formal methods / theorem proving | high | 7 | high | high | standalone/core | 2026-08-29 | V7 schedules newer LemmaNet's checked adaptive program-verification lemmas; LeanDojo remains the technically deep exact-environment alternate rather than a second proof meeting |
| Software architecture recovery | high | 2 | medium | high | background/gap | 2026-08-27 | RepoProbe is strong negative evidence, but recent recovery mechanisms remain prompting/self-reflection-heavy; no primary forced into v5 |
| Failure recovery / external effects | high | 5 | high for workflows; emerging for agents | high | background plus design exercise | 2026-08-28 | Atomix is an exact-fit strong preprint with progress-aware settlement and effect classes; SagaLLM is published but lacks convincing durable transaction guarantees; no modern published primary selected |
| Agent security | high | 12 | high for injection; medium/high for systems | high | standalone/core | 2026-08-29 | V7 selects ACE's trusted-plan/static-IFC/isolated-execution architecture and AgentSpec's stateful runtime policies; CaMeL is the closest strong alternate, while Agent-C and LBAC remain preprint challengers |
| Authorization / information flow | high | 7 | medium/high | high | standalone/core | 2026-08-29 | ACE makes plan integrity, information flow, and capability barriers end-to-end; AgentSpec adds trace policies, while CaMeL and LBAC preserve alternative IFC/capability designs; attenuation, freshness, and revocation remain thin |
| Human oversight / control transfer | high | 3 | medium | high | standalone within correctness | 2026-08-29 | Semantic Commit is the v7 mechanism-bearing primary on evolving intent and impact analysis; Plan-Then-Execute becomes supporting empirical evidence because its 2x2 user study dominates its contribution |
| Configuration / deployment / operations | medium | 0 | application-rich; mechanism-thin | medium | future targeted search | 2026-08-27 | Screened diagnosis and cloud-API agents did not clear the oracle-counterfactual bar; distributed configuration and dependency repair remain promising routes |
| Database / query reasoning | medium | 0 | emerging | low/medium | future targeted search | 2026-08-27 | No inspected agent paper joined relational algebra, provenance, constraints, or transaction semantics strongly enough for a primary slot |

## Coverage interpretation

- **Best-supported required units:** interfaces/runtime; repair and executable
  validation; relational/symbolic analysis; formal environments; security
  enforcement.
- **Newly strong in final v5:** Datalog-style program analysis, solver-aiding
  symbolic execution, requirements semantic validation, RFC conformance,
  whole-agent scheduling, and source-aware checked lemma discovery.
- **Topics deliberately compressed:** generic repository understanding,
  architecture recovery, memory, and multiple topology papers. Strong
  mechanisms remain background rather than creating checklist weeks.
- **Judgments overturned:** CodaMOSA, AutoCodeRover, CodePlan, MSG, DSP, CARD,
  Multi-Agent Resilience, Sagas, LAS, and HoarePrompt leave primary status;
  SAGA moves to background. LemmaNet is the only final-review replacement.
- **Most fragile selected slots:** RFCAudit has strong component evidence but a
  model-owned conformance judgment; accepted-in-press AutoCodeSherpa, Gordian,
  and LemmaNet require proceedings rechecks.
- **Cross-cutting missing abstractions:** transactionality over external effects,
  commit-time binding of approval and authority, concurrent shared-state
  consistency, and soundness/completeness of model-derived semantic facts.

Last substantive update: 2026-08-29 (reading-list v7 technical-depth audit).

The 2026-08-29 architecture-survey audit found no survey that should displace a
technical primary. The closest single entry point is Bajoria et al.'s six-module
reference architecture plus four system axes, but its version of record was
only five days old. Wang et al. plus Guo et al. is the more established compact
pair for single-agent modules and multi-agent organization. Xi et al., Khapre et
al., and Chowa et al. remain broad reference/bibliography sources.

Reading-list v6 resolves the post-freeze audit: AgentSquare replaces CodeAct as
the primary ingredient map, and Evolving Orchestration replaces Agentless as the
multi-agent organization paper. CodeAct and Agentless remain strong instructor
comparisons. Agent plus multi-agent architecture is capped at two weeks; Flow,
MaAS, and GPTSwarm omit distributed-state or effect semantics in different ways.

Reading-list v7 turns the 16-meeting schedule into the canonical teaching set.
Information Propagation replaces TraceFix in the multi-agent week; TraceFix
moves to coordination correctness. ACE replaces CaMeL in the scheduled security
slot while CaMeL remains the nearest strong alternate. Semantic Commit remains
the single mechanism-bearing HCI paper and Plan-Then-Execute becomes supporting
empirical evidence. ImpossibleBench is the only evaluation-first primary.
