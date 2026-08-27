# IRIS: LLM-Assisted Static Analysis for Detecting Security Vulnerabilities

## Decision

**Strong candidate and preferred program-analysis anchor.** Primary source: [ICLR 2025 proceedings](https://proceedings.iclr.cc/paper_files/paper/2025/hash/582d4e27fa24168f3af1f4582655034b-Abstract-Conference.html).

## Problem and mechanism

Whole-repository taint analysis can trace flows but misses vulnerabilities when source, sink, propagation, or sanitizer specifications for libraries are absent. Pure LLM analysis has the opposite weakness: contextual intuition without dependable interprocedural reach.

IRIS first extracts candidate external APIs and public internal parameters. An LLM labels CWE-specific taint roles, which are compiled into CodeQL specifications. CodeQL then enumerates unsanitized repository-scale paths. A second contextual model stage sees path and surrounding code to triage false positives and explain the result. The symbolic engine therefore determines reachability; the model supplies missing semantic labels and final contextual judgment.

## Evidence

- CWE-Bench-Java contains 120 manually validated vulnerabilities in large real projects, averaging over 300K lines, across four CWE classes.
- Base CodeQL detects 27; IRIS with GPT-4 detects 55 while lowering average false-discovery rate by about five percentage points.
- On current versions of 30 projects the system reports four previously unknown vulnerabilities.

## Limits

The remaining false-discovery rate is still high, and final triage is not sound. Inferred specifications can create both missed flows and spurious paths. Results focus on Java taint vulnerabilities and depend on CodeQL's models and buildability.

## Course role

This is a clean LLM-Modulo system. Compare with GPTScan's smart-contract-specific property matching and with AutoCodeRover, where analysis only ranks context rather than defining the semantic backbone.
