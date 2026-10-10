# AMA: Adaptive Memory via Multi-Agent Collaboration

## Decision

**Rejected as a primary.** Primary source: [Findings of ACL 2026](https://aclanthology.org/2026.findings-acl.152/).

AMA divides memory construction, retrieval, judging, and refresh among roles
and supports targeted update and deletion, with roughly 80% token reduction in
the reported experiments. The useful lifecycle operations do not amount to a
defined shared-state protocol: consistency is model-judged, and concurrency,
versioning, isolation, and conflict resolution are absent. It therefore does
not close the multi-agent shared-state gap.
