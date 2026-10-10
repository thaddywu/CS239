# Cordon: Semantic Transactions for Tool-Using LLM Agents

## Decision

**Rejected as a primary reading in this round; reconsider after peer review.** Primary record: [arXiv 2606.17573](https://arxiv.org/abs/2606.17573).

## Problem and mechanism

Tool-using agents cross systems whose side effects, authority, and rollback rules are not captured by ordinary database transactions. Cordon introduces a task-scoped semantic transaction containing typed intents, result objects, provenance links, shadow state, a pre-commit effect outbox, delegated authority, and audit/recovery metadata. It states invariants for lineage, untrusted-data mutation, pre-commit irreversible effects, rollback, boundary completeness, least privilege, scoped approval, and audit completeness. The implementation mediates supported tools and can rollback or resume a task using recorded lineage and effect information.

## Evidence and limits

The prototype is evaluated on constructed adversarial and benign workflows and
reports reduced irreversible-effect failures with modest approval and latency
overhead. Effects outside mediated tools or opaque plugins remain out of scope,
and the record available in August 2026 is an arXiv preprint whose PDF carries a
future EuroSys '27 header rather than a final proceedings record. The current
arXiv record lists Zheng Chen, Hanqing Liu, Duling Xu, Dong Dong, Jialin Li,
Bangzheng Pu, and Jidong Zhai; earlier local metadata named a different author
group and has been corrected.

## Course role

This is the closest agent-native match to the correctness scenario, but publication status and independent evidence are below the seminar's primary-paper bar. Its ideas are recorded as a frontier comparison to Sagas, Beldi, SAGA, CaMeL, and AgentSpec rather than silently omitted.
