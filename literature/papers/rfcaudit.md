# RFCAudit: AI Agent for Auditing Protocol Implementations Against RFC Specifications

## Decision

**Selected for reading-list v5.** Primary source: [ASE 2025 research program](https://conf.researchr.org/details/ase-2025/ase-2025-papers/165/RFCAudit-AI-Agent-for-Auditing-Protocol-Implementations-Against-RFC-Specifications).

## Mechanism and evidence

An indexing agent builds a bottom-up semantic hierarchy over functions, files,
and directories. A detection agent checks individual RFC properties and uses
demand-driven queries for callers, callees, types, macros, and code context;
self-review filters findings. Across six C/C++ protocol implementations,
RFCAudit reports 47 bugs at 81.9% precision, with 20 confirmed or fixed.

Removing semantic indexing drops precision from 81.9% to 51.4%; disabling
retrieval tools lowers it to roughly 47--50%, and removing review substantially
raises false positives. The hierarchy and retrieval protocol are real
mechanisms, but all semantic judgments remain model-based; coverage is not
sound, context can be missed, and the evaluation requires manual labeling.

## Course role

RFCAudit broadens Agentic SE beyond repair into long-document/software
conformance while providing a concrete ablation-based lesson about hierarchical
state and demand-driven semantic queries.
