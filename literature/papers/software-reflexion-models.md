# Software Reflexion Models: Bridging the Gap Between Source and High-Level Models

## Decision

**Background in v4; no longer primary.** Its abstraction remains valuable, but
the compact course should not spend a primary slot on a non-agent 1995 paper
merely to force architecture-recovery coverage. Primary metadata:
[ACM FSE 1995 DOI](https://doi.org/10.1145/222124.222136).

## Problem and mechanism

Architecture recovery is not simply summarization. A developer supplies a high-level model and a mapping from source entities to that model. The tool derives source dependencies, lifts them through the mapping, and classifies relations as convergences (expected and present), divergences (present but unexpected), or absences (expected but missing). The user iteratively revises the hypothesis and mapping.

The central artifact is therefore a falsifiable correspondence between an intended model and implementation evidence.

## Evidence and limits

The original work and follow-on implementation studies demonstrate interactive use on nontrivial systems. Its technical insight has aged well, but the mapping and high-level model require human effort and the recovered views depend on the chosen source relation extractor. It does not infer intent from natural language or act autonomously.

## Course role

Use as an excerpt or instructor background to discipline current claims.
RepoGraph and RepoCoder expose structure and context; they do not recover
architecture unless they posit a model and check it. A promising agentic
research direction is to propose hypotheses or mappings while a reflexion
engine computes explicit discrepancies.
