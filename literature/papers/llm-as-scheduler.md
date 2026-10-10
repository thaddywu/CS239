# LLM-as-Scheduler: Agentic Workflow Dynamic Scheduling

## Decision

**Rejected as a primary reading after the final v5 adversarial review.** Primary
source: [ACL 2026 proceedings](https://aclanthology.org/2026.acl-long.581/).

## Mechanism and evidence

LAS dynamically routes execution through a fixed multi-stage workflow. A cheap
script or DistilBERT gate handles obvious decisions; a larger scheduler chooses
early exit, testing, refinement, or rerouting only for harder cases. On MBPP,
HumanEval, and GSM8K it reduces output tokens by 43--63% and latency by 36--42%
with at most a 1.4-point accuracy loss relative to AFLOW.

Ablations expose the division of labor: the gate alone is cheap but loses much
more accuracy; the LLM scheduler alone preserves accuracy but costs more; the
combination retains 93.7% accuracy in the reported aggregate while lowering
cost. Routing accuracy is only about 66%, but harmful errors are reported at
2.7%. Calibration is domain-specific and the evidence covers a small set of
workflows without tools or retrieval.

## Course role

The full mechanism is a benchmark-calibrated gate plus a prompted JSON router,
not a scheduler with resource, dependency, concurrency, tool, or persistent-state
semantics. Agentix supplies the deeper runtime abstraction, and Information
Propagation supplies the remaining multi-agent primary. Reconsider only if a
later version adds a general scheduling model or substantially broader evidence.
