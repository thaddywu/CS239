# Reading-list v4 decisions

This note records only changes that materially affect the v3 structure.

- **Murakkab — remove from primary.** Its declarative workflow IR and
  cross-layer optimizer are technically strong, but they optimize model,
  accelerator, cost, and SLO choices rather than communication, shared state,
  synchronization, delegation, or fault containment. Keep it as systems
  background, not as the course's agent-architecture reading.
- **Multi-Agent Resilience — retain, but no longer alone.** Its controlled
  fault injection and Challenger/Inspector mitigations still earn a reading.
  Information Propagation Topologies and the new ICLR 2026 CARD paper now
  precede it, so the block teaches causal propagation and adaptive graph design
  before fault containment.
- **Software Reflexion Models — move to background.** The abstraction remains
  valuable, but a 1995 non-agent paper should not occupy a primary slot when
  architecture recovery is not itself a full course block. Recent work was
  either non-agent design understanding (ACE), benchmark/negative evidence
  (RepoProbe), prompt-and-self-reflection evaluation, or early-results work.
  This is recorded as a modern agentic-literature gap.
- **CodaMOSA — retain.** RippleGUItester and newer 2026 testing papers add
  valuable change-aware and evaluation ideas, but none provides a cleaner
  mechanism than measured search stagnation followed by targeted model seeding
  and a return to evolutionary search.
- **Sagas / Beldi — assign only one.** Sagas is the default primary because
  semantic compensation best exposes the open-world agent problem. Beldi is an
  alternative when the class should study exactly-once replay and isolation in
  an implementable mediated runtime. Exact-fit agent work such as Cordon,
  ACRFence, and Agentic Transaction remains preprint-only as of 2026-08-27.
- **Adjustable Autonomy — replace as primary.** CHI 2025's Plan-Then-Execute is
  a modern LLM-agent study that separates planning and execution approval. Its
  negative result—more human involvement neither reliably calibrates trust nor
  improves every task—is more useful for the current course. The 2002 paper
  remains the formal alternative for costed transfer-of-control policies.
- **SAGA — retain.** Its trusted provider and small evaluation constrain the
  claim, but cryptographic inter-agent identity and authorization remain unique
  among the selected papers. It should be challenged alongside CaMeL and
  AgentSpec, not treated as a complete governance solution.
- **New primary: CARD (ICLR 2026).** A conditional variational graph generator
  changes communication topology when models, tools, or information sources
  change, filling the multi-agent design gap more directly than Murakkab.
- **New alternative: RepoProbe (ASE 2026).** Its checklist-based evaluation and
  edit-bias result are strong negative evidence for repository understanding,
  but it does not yet recover or maintain an architecture model.

The resulting v4 has 19 primary papers. This is a structural working set, not
a target count: the final cut can remove one or more papers after the actual
class calendar and per-meeting reading load are fixed.
