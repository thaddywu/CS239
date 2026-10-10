# A Survey on Large Language Model Based Autonomous Agents

## Decision

**Candidate as a short architecture framing reading, not as a student-led
technical primary.** Verified against the
[journal record](https://journal.hep.com.cn/fcs/EN/10.1007/s11704-024-40231-1).

## Architecture and evidence

Wang et al. organize agent construction into profile, memory, planning, and
action, then separately review capability acquisition, applications, and
evaluation. The architecture section is unusually teachable: memory is divided
by structure, representation, and operations; planning is divided by feedback
and search structure; action covers tool use and environment interaction.

The framework is an explanatory taxonomy, not an executable architecture or an
experiment establishing that the four modules are necessary. Its literature is
mostly from 2023, profiling is partly persona-oriented, and it does not treat
tool schemas, runtime isolation, policy monitors, observability, or durable
effects as first-class components.

## Course role

The cleanest established prerequisite for AgentSquare. Assign Section 2.1 or
use its architecture figure in lecture, then let AgentSquare, SWE-agent, and
security/runtime papers supply technical mechanisms and system boundaries.
