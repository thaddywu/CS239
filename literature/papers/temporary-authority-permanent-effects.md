# Temporary Authority, Permanent Effects: Commit-Time Authorization for LLM Agents

## Decision

**Candidate, not a v4 primary while it remains a preprint.** Primary record:
[arXiv 2607.10487](https://arxiv.org/abs/2607.10487).

The paper separates endpoint success from authorized commit. An authorization
witness must remain fresh, causally prior, bound to the same effect, and
eligible at durability time. A controlled-invalidation suite spans browser,
tool/API, and multi-agent workflows; most invalidated runs still reach their
visible result while violating authorization. CommitGuard blocks protected
commit surfaces when the runtime supplies the required evidence.

The abstraction directly connects TOCTOU, delegation, provenance, and durable
effects. Its single-author preprint status and synthetic instrumented harness
keep it behind CaMeL, AgentSpec, and SAGA for assignment, but it is a high-value
frontier comparison.

