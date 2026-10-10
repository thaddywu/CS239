# LogicLoc: Neurosymbolic Repository-Level Code Localization

## Decision

**Candidate, not selected.** Current source: [arXiv 2604.16021](https://arxiv.org/abs/2604.16021); publication status unverified.

LogicLoc extracts repository facts, asks an LLM to synthesize Datalog programs,
checks their syntax, and uses mutation feedback before executing them for code
localization. A keyword-agnostic benchmark makes the evaluation more
interesting than ordinary retrieval. NESA is preferred because its restricted
policy language and fixed-point division of symbolic/neural relations are more
general and its FSE publication is final; LogicLoc remains a direct challenger
if its publication status or evidence strengthens.
