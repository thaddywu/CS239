# H-MAS: Hierarchical Multi-Agent Scheduling for Multi-Tenant LLM Serving

## Decision

**Rejected as a primary.** Primary source: [Findings of ACL 2026](https://aclanthology.org/2026.findings-acl.1946/).

H-MAS uses perception, feedback, long- and short-horizon control, and execution
roles to schedule multi-tenant inference, reporting 1.2--3x goodput over SGLang
and vLLM. The scheduling mechanism is real, but its “agents” are operational
controller roles rather than collaborating LLM programs. Agentix addresses the
course's agent-program runtime question more directly, so this is recorded as a
serving-system comparison and an agent-washing boundary case.
