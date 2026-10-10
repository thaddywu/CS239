# ACTaint: Multi-Agent Taint Analysis for Access-Control Vulnerabilities

## Decision

**Candidate, not selected.** Primary source: [ASE 2025 publisher record](https://doi.org/10.1109/ASE63991.2025.00210).

ACTaint assigns source, sink, and taint-reasoning roles to analyze access-control
vulnerabilities in Solidity and reports precision and F1 gains of 8.3 and 9.7
points over ACheker. The program-analysis grounding is meaningful, but the role
decomposition is narrower and less cleanly separable than IRIS's CodeQL-owned
reachability. Retain for a smart-contract/security variant, not the core list.
