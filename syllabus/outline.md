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

**Short background:** ReAct. **Optional:** OpenHands.

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

**Short background:** QuickCheck. **Optional:** CoverUp.

**Debate:** Coverage and test passage are feedback signals, not semantic truth.
When should a system synthesize examples, properties, or metamorphic relations;
and what should it do when tests conflict with the stated requirement?

## Week 5 — Neuro-symbolic software engineering at repository scale

**Primary**

- [IRIS](../literature/papers/iris.md)
- [CodePlan](../literature/papers/codeplan.md)

**Short background:** [Software Reflexion Models](../literature/papers/software-reflexion-models.md).
**Optional:** [GPTScan](../literature/papers/gptscan.md); RepoGraph.

**Debate:** IRIS lets the model supply missing specifications while analysis
supplies reachability; CodePlan lets analysis create future edit obligations.
Contrast both with retrieval-only “repository understanding” and define what
would count as actual architecture recovery.

## Week 6 — Proof assistants as high-integrity agent environments

**Primary**

- [LeanDojo](../literature/papers/lean-dojo.md)
- [LEGO-Prover](../literature/papers/lego-prover.md)

**Optional:** [Draft, Sketch, and Prove](../literature/papers/draft-sketch-prove.md);
[AlphaGeometry](../literature/papers/alphageometry.md); *Don't Trust: Verify*.

**Debate:** Why do typed state, small executable actions, scoped libraries, and
kernel checking make theorem proving a better agent runtime than a shell? Is a
verified lemma library the right model for long-term agent memory?

## Week 7 — Multi-agent communication and fault containment

**Primary**

- [Information Propagation Effects of Communication Topologies](../literature/papers/information-propagation-topologies.md)
- [Resilience with Faulty Agents](../literature/papers/multi-agent-resilience.md)

**Optional:** Du et al. debate; sparse communication topology. Use MetaGPT and
ChatDev only as short rejected contrasts.

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
2026 proceedings/artifact review.

**Debate:** Compare information/control-flow separation and capabilities with a
general action-policy monitor. State each trusted computing base, policy gap,
utility cost, and claim that is actually guaranteed.

## Week 10 — Frontier case clinic and project design review

There is deliberately no mandatory “best paper” for systems/science/hardware:
the search found strong applications but insufficiently isolated mechanisms.
Student groups choose one case—Coscientist, ChemCrow, MLAgentBench, ChatEDA, or
OpenHands—and submit:

1. an architecture and authority diagram;
2. a failure/threat model;
3. an independent validation and recovery design;
4. a matched non-agent or simpler-pipeline baseline;
5. the experiment that could falsify the system's central claim.

The second half is project/document review using the same rubric.

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
