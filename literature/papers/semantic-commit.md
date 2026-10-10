# Semantic Commit: Helping Users Update Intent Specifications for AI Memory at Scale

## Decision

**Selected in v7 as the sole scheduled SE+HCI/intent paper.** UIST 2025,
DOI 10.1145/3746059.3747778. It supplies the SE+HCI correctness view of
maintaining persistent, informal intent specifications.

## Mechanism

SemanticCommit treats updates to natural-language memory, requirements, and
Cursor Rules as a semantic impact-analysis problem. A knowledge-graph retrieval
pipeline finds potentially conflicting prior facts; an interface separates
conflict detection, local resolution, global revision, and human verification.

## Evidence

Four small labeled datasets test retrieval/classification; SemanticCommit
reports 1.6x and 2.2x higher recall than two simpler baselines at similar
accuracy. A counterbalanced within-subjects study with 12 participants finds
distinct impact-analysis workflows, more granular intervention, and a greater
sense of control than a Canvas baseline without increased self-reported load.

## Limits

The datasets are small and curated, the user study is small and subject to
demand/familiarity effects, and Canvas differs in more than the focal feature.
Memory is modeled as an unweighted fact list without temporal scope,
provenance, confidence, or concurrent writers.

## Course role

This is the primary SE+HCI reading on evolving intent: agent specifications are
persistent, informal, and revised over time, so maintaining them is closer to
change-impact analysis than editing one prompt.
