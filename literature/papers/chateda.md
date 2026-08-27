# ChatEDA: A Large Language Model Powered Autonomous Agent for EDA

## Metadata

IEEE TCAD 2024. [DOI](https://doi.org/10.1109/TCAD.2024.3383347).

## One-line idea

Translate natural-language hardware-design goals into scripts that orchestrate
an RTL-to-GDSII electronic-design-automation flow.

## Technical core

The system decomposes a design request, generates executable EDA scripts, runs
tools, and uses outputs/errors to continue the flow. A domain-adapted model and
tool documentation support commands across synthesis and physical design.

## Evaluation and limits

Case studies demonstrate end-to-end tool use and compare generated scripts and
flows. The paper contributes a domain integration more than a new general agent
abstraction; proprietary/complex toolchains constrain reproducibility, and
formal equivalence/PPA validation are not a general recovery policy.

## Course placement and decision

**Candidate / Week 10 hardware case.** Currently the closest hardware loop, but
not strong enough to justify a required hardware-agent week.
