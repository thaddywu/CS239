# Tentative Seminar Outline

This is an evidence-driven first syllabus, not a locked schedule. The normal
load is two primary papers plus a short background or optional reading. Papers
remain `strong_candidate` in the canonical CSV until the instructor freezes the
schedule.

## Course through-line

Every week asks the same responsibility question:

> What should a probabilistic model decide, what state and authority should the
> runtime expose, and what independent evidence is allowed to validate or stop
> an action?

Agent-based software development runs through the course rather than occupying
one framework-survey week.

## Week 1 — Agents as runtime/interface systems

**Primary**

- [SWE-agent](../literature/papers/swe-agent.md)
- [CodeAct](../literature/papers/codeact.md)

**Short background:** ReAct. **Optional:** OpenHands;
[Murakkab](../literature/papers/murakkab.md) for the deployment/runtime layer.

**Debate:** Should an agent receive a narrow LM-specific interface with concise
feedback and guardrails, or a maximally compositional programming language? Map
the trusted computing base and failure-recovery behavior of both designs.

## Week 2 — Learning tools, planning, and programmable orchestration

**Primary**

- [Toolformer](../literature/papers/toolformer.md)
- [LLM-Modulo planning](../literature/papers/llm-modulo-planning.md)

**Optional:** DSPy; LATS; MemGPT.

**Debate:** Which decisions belong in learned weights, a compiler/runtime, a
search procedure, or an external planner/verifier? Students redraw each paper as
the same proposer–executor–validator architecture and identify missing state.

## Week 3 — Repository repair: agent or engineered pipeline?

**Primary**

- [AutoCodeRover](../literature/papers/autocoderover.md)
- [Agentless](../literature/papers/agentless.md)

**Optional:** [RepairAgent](../literature/papers/repairagent.md); SWE-bench for
evaluation history.

**Debate:** Hold the model constant conceptually. Which gains come from program
structure, fault localization, hierarchy, sampling, interaction, or test access?
Why is “agentless” not the same as “non-agentic computation”?

## Week 4 — Testing, properties, and specification gaming

**Primary**

- [CodaMOSA](../literature/papers/codamosa.md)
- [ImpossibleBench](../literature/papers/impossiblebench.md)

**Short background:** QuickCheck. **Optional:** CoverUp;
[PropertyGPT](../literature/papers/propertygpt.md);
[Agentic Specification Generator](../literature/papers/agentic-specification-generator.md).

**Debate:** Coverage and test passage are feedback signals, not semantic truth.
When should a system synthesize examples, properties, or metamorphic relations;
and what should it do when tests conflict with the stated requirement?

## Week 5 — Neuro-symbolic software engineering at repository scale

**Primary**

- [IRIS](../literature/papers/iris.md)
- [CodePlan](../literature/papers/codeplan.md)

**Short background:** [Software Reflexion Models](../literature/papers/software-reflexion-models.md).
**Optional:** [GPTScan](../literature/papers/gptscan.md); RepoGraph;
[SemRef](../literature/papers/semref.md), with its proceedings-record caveat.

**Debate:** IRIS lets the model supply missing specifications while analysis
supplies reachability; CodePlan lets analysis create future edit obligations.
Contrast both with retrieval-only “repository understanding” and define what
would count as actual architecture recovery.

## Week 6 — Proof assistants as high-integrity agent environments

**Primary**

- [LeanDojo](../literature/papers/lean-dojo.md)
- [PAT-Agent](../literature/papers/pat-agent.md)

**Optional:** [Draft, Sketch, and Prove](../literature/papers/draft-sketch-prove.md);
[LEGO-Prover](../literature/papers/lego-prover.md);
[AlphaGeometry](../literature/papers/alphageometry.md); *Don't Trust: Verify*;
PropertyGPT or Agentic Specification Generator for software contracts.

**Debate:** Why do typed state, small executable actions, scoped libraries, and
independent checking make formal tools better agent runtimes than a shell? A
checker proves a generated model internally consistent; what evidence shows the
model faithfully represents the informal system?

## Week 7 — Multi-agent communication and fault containment

**Primary**

- [Information Propagation Effects of Communication Topologies](../literature/papers/information-propagation-topologies.md)
- [Resilience with Faulty Agents](../literature/papers/multi-agent-resilience.md)

**Optional:** Du et al. debate; sparse communication topology;
[G-Designer](../literature/papers/g-designer.md) for learned graph design;
[SAGA](../literature/papers/saga.md) for authorization. Use MetaGPT and ChatDev
only as short rejected contrasts.

**Debate:** When does another agent add information rather than another sample
from the same error distribution? Compare graph sparsity, hierarchy, Challenger,
and Inspector under correlated and malicious faults.

## Week 8 — Self-correction, external evidence, and recovery

**Primary**

- [Large Language Models Cannot Self-Correct Reasoning Yet](../literature/papers/self-correction-limitations.md)
- [CRITIC](../literature/papers/critic.md)

**Short systems bridge:** Microreboot. **Optional:** Reflexion.

**Debate:** Name the new information introduced by every correction loop. Then
extend answer revision into systems recovery: what checkpoint, idempotency,
rollback, or compensating action would be required after a real tool side effect?

## Week 9 — Security by construction and runtime enforcement

**Primary**

- [CaMeL](../literature/papers/camel.md)
- [AgentSpec](../literature/papers/agentspec.md)

**Required background excerpt:** Saltzer and Schroeder. **Evaluation context:**
[AgentDojo](../literature/papers/agentdojo.md). **Watch:** RefineAct after final ASE
2026 proceedings/artifact review. **Optional architectures:**
[ACE](../literature/papers/ace.md); [SAGA](../literature/papers/saga.md).

**Debate:** Compare information/control-flow separation and capabilities with a
general action-policy monitor. State each trusted computing base, policy gap,
utility cost, and claim that is actually guaranteed.

## Week 10 — Memory, persistent state, and frontier synthesis

**Primary**

- [Agentic Memory](../literature/papers/agentic-memory.md)
- [How Memory Management Impacts LLM Agents](../literature/papers/memory-management-impact.md)

**Short background:** MemGPT. **Cross-list:** LEGO-Prover as verified memory.

**Debate:** Is learned store/retrieve/update/delete behavior enough to call
memory a subsystem? Specify entry invariants, provenance, invalidation,
confidentiality, and rollback for a memory whose retrieved errors change future
actions. Distinguish answer-task rewards from deployable quality signals.

The second half retains the frontier clinic. Groups choose Coscientist, ChemCrow,
MLAgentBench, ChatEDA, OpenHands, or Murakkab and submit an authority diagram,
failure model, independent validation/recovery design, matched simpler baseline,
and a falsifying experiment.

## Changes from the initial hypothesis

- Split testing/repair from **oracle and specification quality** because
  ImpossibleBench and manual patch audits show that test passage can reward the
  wrong behavior.
- Merged modern repository understanding with classical architecture recovery;
  current retrieval/graph papers do not justify a standalone recovery week.
- Made software-development agents cross-cutting and rejected a framework tour.
- Downgraded systems/science/hardware to a frontier clinic until stronger
  mechanism-comparison literature appears.
- Elevated runtime enforcement/security to a full week because 2026 work now
  supplies architectural mechanisms, not only attack benchmarks.
- Added a focused memory week after ACL 2026 supplied complementary constructive
  policy learning and controlled failure evidence; MemGPT is now background.
- Replaced LEGO-Prover with PAT-Agent as Week 6's second primary to diversify
  theorem-proving and model-checking/autoformalization mechanisms; LEGO-Prover
  remains the verified-memory cross-reading.
- Kept property-based testing embedded: formal property/specification generation
  is now real, but full generator–property–shrinker maintenance is not mature.
- Kept architecture recovery merged despite SemRef, and kept failure recovery as
  a gap-driven week because no transactional agent-runtime counterexample was
  found.
