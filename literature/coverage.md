# Coverage Matrix

“Explored level” measures this repository's search coverage, not the field's
maturity. **High** requires expanded terminology, multiple venue families,
backward/forward citation paths, full-method inspection of leading papers, and
comparison against competing mechanisms. Counts include cross-listed papers.

| Topic | Explored level | Strong candidates | Literature maturity | Evidence covered | Major gap / next action |
|---|---|---:|---|---|---|
| Agent architecture and runtime | high | 4 | high for interfaces; medium for state | ReAct/Toolformer lineage; ICML/ICLR/NeurIPS runtime and ACI papers; action-space and verifier comparison | Search peer-reviewed protocol semantics, transactions, provenance, and durable state |
| Multi-agent systems | high | 2 | medium | Debate baseline/negative control; sparse and learned topology; causal propagation; ICML fault injection; role-workflow rejections | Correlated/shared-model faults, blackboard consistency, equal-compute controls, Byzantine tool users |
| Testing and program repair | high | 5 | high | ICSE/ISSTA/FSE repair; SWE-bench lineage; search/coverage hybrids; property-testing foundation; oracle exploitation | Durable property/invariant generation, independent patch validation, non-Python repositories |
| Program analysis | medium | 3 | medium | ICLR/ICSE/ISSTA; taint specification mining, property matching, dynamic partial execution; links into repair/planning | Broaden beyond security and state explicit soundness/false-negative contracts |
| Formal methods and theorem proving | high | 4 | high | ICLR/NeurIPS/Nature; Lean interaction, premise retrieval, sketches, growing libraries, symbolic closure, autoformalization | Faithful statement formalization and repository-scale software contracts |
| Architecture and repository understanding | medium | 2 | high for retrieval; low for agentic recovery | Repo retrieval/graphs, FSE change planning, classic reflexion-model citation path | Find systems that propose and independently check architectural hypotheses/mappings |
| Failure recovery and reliability | medium | 4 | medium for critique; low for side effects | Reflexion/CRITIC/negative self-correction; multi-agent fault injection; OSDI/HotOS recovery lineage | Checkpoint/replay, idempotency, compensating actions, verifier failure, durable external state |
| Security and policy enforcement | high | 5 | medium/high and rapidly moving | ACL/ICLR/NeurIPS attacks and testbeds; SaTML information flow/capabilities; ICSE/ASE runtime policies; classic protection principles | Delegation/revocation, policy composition, memory security, availability, common evaluations |
| Systems, science, and hardware | medium | 0 | application-rich; mechanism-thin | Nature chemistry loops; ICML experiment benchmark; TCAD EDA; workshop/preprint dead ends | Citation-chain follow-up for transactional labs and formally validated EDA; no standalone week yet |
| Agent-based software development | high | 4 | high but benchmark-concentrated | ACI, open runtime, SE-guided repair/planning, deterministic pipeline controls, multi-agent workflow rejections | Human oversight, ambiguous requirements, CI/deployment/rollback, cross-language evaluation |

## Coverage interpretation

- **Best-supported required weeks:** interfaces/runtime; testing and repair;
  formal environments; multi-agent topology/faults; security enforcement.
- **Best merged topic:** program analysis + repository change planning + the
  distinction between retrieval and architecture recovery.
- **Underdeveloped despite search:** transactional failure recovery; true
  agentic architecture recovery; hardware agents with formal feedback.
- **Cross-cutting missing abstraction:** specification authority—what happens
  when instructions, tests, static analyses, policies, and observed behavior
  disagree.

Last substantive update: 2026-08-26.
