# Coverage Matrix

“Explored level” measures this repository's search coverage, not the field's
maturity. **Audit confidence** asks a different question: after adversarially
searching likely omissions and publication changes, how likely is the current
syllabus judgment to survive another focused check? Counts include cross-listed
selected papers and strong candidates and therefore are not additive.

| Topic | Explored level | Selected/strong | Literature maturity | Audit confidence | Judgment | Last audited | Decision-relevant evidence / remaining gap |
|---|---|---:|---|---|---|---|---|
| Agent architecture / harness | high | 3 | high | high | standalone/core | 2026-08-27 | SWE-agent and CodeAct isolate opposite interface choices; Murakkab adds a systems-runtime layer; transactional state remains missing |
| Tools and tool use | high | 3 | high | high | standalone/core | 2026-08-27 | Toolformer learns calls, CodeAct composes them, SWE-agent constrains them; protocol versioning/capability discovery remain thin |
| Planning and execution | high | 2 | medium/high | medium | embed/core | 2026-08-27 | LLM-Modulo and CodePlan give verifier- and dependency-driven alternatives; planning papers still confound model/value quality |
| Memory / context management | high | 3 | high for policy; low for transactions | high | **standalone now viable** | 2026-08-27 | AgeMem plus the experience-following study supply constructive and negative primaries; LEGO-Prover adds verified memory; cross-session security remains open |
| Multi-agent systems | high | 3 | medium/high | high | standalone/core | 2026-08-27 | Causal propagation, fault injection, learned topology, and SAGA authorization cover distinct mechanisms; shared-state consistency remains missing |
| Testing | high | 3 | high | high | standalone/core | 2026-08-27 | CodaMOSA, ImpossibleBench, and formal-property generation separate search, feedback, and oracle quality |
| Program repair | high | 3 | high | high | mature/core | 2026-08-27 | AutoCodeRover, RepairAgent, and Agentless retain the best autonomy spectrum; no new generic SWE-bench agent changed it |
| Runtime validation / verification | high | 2 | medium/high, fast-moving | medium | standalone with security/formal | 2026-08-27 | AgentSpec policies and PAT counterexample repair provide different monitors; RefineAct remains accepted/in press |
| Property-based testing | high | 2 | medium for properties; low for full PBT | high | embed, not standalone | 2026-08-27 | PropertyGPT and MSG generate reusable checked properties/invariants, but generator synthesis, shrinking, and long-term maintenance are not mature |
| Program analysis | medium | 3 | medium | medium | merge with repository/formal | 2026-08-27 | IRIS/GPTScan remain strongest direct hybrids; MSG and SemRef broaden analysis roles without defining general soundness contracts |
| Formal methods | high | 5 | high | high | standalone/core | 2026-08-27 | Proof environments, verified artifacts, model checking, property generation, and symbolic closure now give real mechanism diversity |
| Autoformalization | high | 3 | medium/high | medium | standalone within formal week | 2026-08-27 | PAT-Agent, PropertyGPT, and MSG add checker-guided synthesis; fidelity to informal intent remains the central unresolved threat |
| Theorem proving | high | 4 | high | high | standalone/core | 2026-08-27 | LeanDojo, Draft–Sketch–Prove, LEGO-Prover, and AlphaGeometry remain technically deep and complementary |
| Software/system architecture recovery | high | 1 | low/medium | medium | merge; standalone premature | 2026-08-27 | SemRef is a direct modern counterexample, but one refinement mechanism plus a missing final proceedings record does not form a mature cluster |
| Failure recovery / self-healing | high | 2 | medium for answer retry; low for side effects | medium | cross-cutting, gap-driven | 2026-08-27 | Targeted systems/workflow search found no agent checkpoint/replay, idempotency, saga compensation, or exactly-once semantics |
| Agent security | high | 5 | high for injection/evaluation; medium for systems | high | standalone/core | 2026-08-27 | AgentDojo, CaMeL, AgentSpec, ACE, and SAGA span benchmark, dataflow, monitor, trusted-plan, and authorization designs |
| Authorization / information flow / policy enforcement | high | 4 | medium/high | high | standalone within security | 2026-08-27 | CaMeL/ACE capabilities and dataflow, AgentSpec policy monitoring, and SAGA tokens are distinct; OS sandbox enforcement remains undercovered |
| Agent-based software development | high | 4 | high but benchmark-concentrated | high | cross-course thread | 2026-08-27 | SWE-agent, AutoCodeRover, Agentless, and CodePlan retain their roles; human oversight, CI/deployment, and rollback remain weak |
| Agents for systems / science / hardware | medium | 1 | high for workflow serving; application-rich elsewhere | medium | mixed; no combined core week | 2026-08-27 | Murakkab fixes the systems-runtime omission; science/hardware still offer domain cases more than isolated general mechanisms |

## Coverage interpretation

- **Best-supported required weeks:** interfaces/runtime; testing, repair, and
  oracle quality; formal environments; multi-agent topology/faults; security
  enforcement.
- **Newly viable focused session:** memory/state, using AgeMem as the constructive
  mechanism and the ACL experience-following study as the failure analysis.
- **Best merged topics:** program analysis + repository planning + architecture-
  recovery critique; strict property-based testing + formal specification
  generation rather than pretending they are the same subfield.
- **Judgments that survived an adversarial search:** repair's current primary
  pair, multi-agent's topology/fault pair, and the absence of transactional
  agent failure recovery.
- **Most fragile areas:** architecture recovery (one direct 2026 candidate with
  unresolved proceedings metadata), new runtime-enforcement work, and science/
  hardware follow-ups that may migrate into systems venues.
- **Cross-cutting missing abstraction:** specification authority—what happens
  when instructions, tests, generated properties, static analyses, policies,
  stored experience, and observed behavior disagree.

Last substantive update: 2026-08-27.
