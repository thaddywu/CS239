# Literature-Knowledge-Base Protocol

This repository is a persistent research asset for a graduate seminar on
Agentic Software Engineering / Software Engineering for AI Agents.

## Non-negotiable workflow

Never start literature search from scratch.

Before any search:

1. Read `literature/papers.csv`.
2. Read the relevant `topics/*.md` map.
3. Read `literature/coverage.md`.
4. Check existing candidate, rejected, and superseded papers.
5. Understand earlier rejection and comparison rationales.
6. Identify a genuinely underexplored gap.
7. Only then search the web, proceedings, and citation graph.

After a search round:

1. Add every seriously inspected paper to `literature/papers.csv`, including
   rejected papers.
2. Verify title, authors, year, venue, and publication status against an
   authoritative source. Use `unverified` rather than guessing.
3. Record a specific decision rationale; never silently delete a rejection.
4. Add or update a concise decision-relevant note for every candidate, strong
   candidate, selected paper, and any rejection worth deeper understanding.
5. Update the relevant topic map, `literature/coverage.md`, and
   `literature/search-log.md`.
6. Recompare related papers and update `syllabus/outline.md` if the evidence
   changes the course structure.

The required loop is:

`READ -> IDENTIFY GAPS -> SEARCH -> VERIFY -> READ -> COMPARE -> RECORD -> UPDATE COVERAGE -> SEARCH AGAIN`

## Evaluation rules

- Prefer algorithms, abstractions, runtimes, protocols, verification or
  analysis mechanisms, and illuminating negative results over benchmark rank.
- Treat "LLM + prompt + existing tools" and ordinary applications with an LLM
  controller as likely agent washing unless the agent mechanism is central.
- Do not infer depth from recency, author reputation, venue, scale, or the word
  "agent".
- Keep the corpus selective. Three to six defensible readings per mature topic
  are better than a paper dump.
- Use surveys to find terminology and citation paths, not as default primary
  readings.
- Include foundational non-agent work when it clarifies the agent problem, but
  do not let it displace the course's agentic focus.

Allowed paper statuses are `discovered`, `unread`, `skimmed`, `candidate`,
`strong_candidate`, `selected`, `rejected`, and `superseded`.

Allowed ratings for `technical_depth`, `insight`, and `course_fit` are `low`,
`medium`, `high`, and `very_high`. Ratings must be discriminating.

Reconsider a rejected paper only when a new version or publication status,
newly found technical contribution, or changed syllabus need warrants it; log
the reason.

## Editing conventions

- `literature/papers.csv` is the canonical paper index.
- Topic files are evolving research maps, not unannotated bibliographies.
- Paper-note filenames use stable lower-case kebab-case slugs.
- URLs should point to proceedings, publisher pages, OpenReview, ACL Anthology,
  USENIX, or arXiv records rather than search results.
- Preserve concise, decision-relevant notes and explicit uncertainty.

## Publication and evidence checks

- Prefer the final proceedings/publisher record over arXiv metadata. If versions
  disagree, record the discrepancy in the note.
- `accepted_in_press` means acceptance is authoritative but final proceedings
  were not available at the time of review. Recheck before syllabus freeze.
- Do not compare raw benchmark scores across different model generations,
  budgets, test access, benchmark revisions, or contamination controls as if
  they measured only the proposed mechanism.
- For a strong candidate, inspect the method, experimental setup, at least one
  central result/ablation, and limitations—not only the abstract.
