# MemGPT: Towards LLMs as Operating Systems

## Metadata

arXiv preprint, 2023. [Primary record](https://arxiv.org/abs/2310.08560).

## One-line idea

Treat the context window as limited fast memory and let the agent move data
between explicit memory tiers through function calls and interrupts.

## Technical core and architecture

A fixed-context model interacts with main context, archival storage, and recall
storage. System messages and interrupts pressure it to page information, search
older content, and revise stored state. The OS analogy makes memory management
an explicit runtime protocol.

## Evaluation and limits

Long-document and persistent-conversation demonstrations show advantages over
naive context truncation. Evidence is preprint-level, memory writes are largely
model-governed and unverified, and provenance/invalidation/consistency are weak.

## Course placement and decision

**Candidate / Week 2 optional.** Valuable architectural provocation; LEGO-Prover
is stronger evidence for reusable, verified memory.
