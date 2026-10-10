# ProbGuard: Proactive Runtime Monitoring for LLM Agent Safety via Probabilistic Prediction

## Decision

**Strong candidate, not selected; accepted in press at ASE 2026.** Primary
source: [ASE 2026 research program](https://conf.researchr.org/details/ase-2026/ase-2026-research-track/117/ProbGuard-Proactive-Runtime-Monitoring-for-LLM-Agent-Safety-via-Probabilistic-Predic).

ProbGuard abstracts traces into symbolic predicates, learns a DTMC, and uses CTL
safety probabilities to intervene before an unsafe action. It reports up to
15.84 seconds of warning in driving and large reductions in unsafe embodied
actions, with a visible halt-versus-completion tradeoff. The formal framing is
valuable, but the practical evaluation uses only 30 traces, below its stated
PAC sample requirements; the Markov abstraction and expert-written unsafe
predicates also limit the guarantee. Keep beside AgentSpec rather than replacing
its direct reference-monitor lesson.
