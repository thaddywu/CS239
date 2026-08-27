# Agentic Software Engineering Seminar Knowledge Base

This repository maps the intellectual structure and reading candidates for a
graduate seminar on **Agentic Software Engineering / Software Engineering for
AI Agents**. It is a maintained decision record, not a comprehensive paper
dump.

## Start here

- [`literature/papers.csv`](literature/papers.csv): canonical paper index and
  decisions.
- [`literature/coverage.md`](literature/coverage.md): how thoroughly each area
  has been explored and what remains missing.
- [`literature/search-log.md`](literature/search-log.md): search reasoning,
  including dead ends.
- [`topics/`](topics/): evolving maps of mechanisms, debates, and candidates.
- [`literature/papers/`](literature/papers/): decision-relevant paper notes.
- [`syllabus/outline.md`](syllabus/outline.md): tentative reading sequence.
- [`AGENTS.md`](AGENTS.md): mandatory protocol for future exploration.

The initial corpus deliberately distinguishes peer-reviewed work from
preprints and retains rejected papers so later searches do not repeat the same
work.

## Initial evidence snapshot (2026-08-26)

- 54 evaluated records in the canonical index.
- 24 candidates and 24 strong candidates, each with a
  method/evidence/limits note.
- 5 explicit rejections and 1 superseded foundational record retained.
- 10 topic maps, a coverage matrix, four logged search rounds, and a tentative
  ten-week syllabus.

The first build found mature clusters around interfaces, repository repair,
formal environments, multi-agent topology/faults, and security enforcement. It
also records three real gaps: transactional failure recovery, agentic
architecture recovery, and mechanism-rich hardware agents.

## Maintenance rule

Start every update from [`AGENTS.md`](AGENTS.md), the CSV, the relevant topic
map, and the coverage gap. New searches must add decisions back to the index;
rejected work is never silently removed.
