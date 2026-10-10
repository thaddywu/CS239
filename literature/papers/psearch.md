# PSearch: Search-Based Patch Generation in the Era of LLM-Based Automated Program Repair

## Decision

**Unread watch-list paper; not promoted to v7.** Primary source: [ASE 2026
program record](https://conf.researchr.org/details/ase-2026/ase-2026-research-track/92/PSearch-Search-Based-Patch-Generation-in-the-Era-of-LLM-Based-Automated-Program-Repa).

## Why it is promising

PSearch represents intermediate patches as a structured search state, scores the
promise of search directions, and uses Monte Carlo tree search to allocate a
long-horizon repair budget. That is a real repair algorithm rather than repeated
independent patch sampling.

## Why it is not yet selected

The official record exposes the abstract and artifact summary but not a full
paper. The search state, reward/evaluation signal, duplicate handling, failure
modes, and ablations therefore could not be inspected to the standard required
for a strong candidate. Recheck when the proceedings or author manuscript is
available.
