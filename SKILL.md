---
name: appendix-cross-reference-audit
description: >-
  Audit a research paper so that every appendix result the main text actually
  relies on is traceable from the exact claim that uses it. Use this whenever
  someone is preparing a paper for submission and asks to "check the appendix
  references", "make sure the main paper points to the appendix", "did we cite
  every table", "cross-reference audit", or when a supervisor/reviewer asks
  whether appendix material (tables, robustness checks, decompositions,
  diagnostics) is pointed to from the relevant place above. Also use it to build
  a clean appendix-to-main mapping table, to write the exact minimal LaTeX fix
  for a missing pointer, or to phrase the result for a supervisor. Trigger even
  when the user just says "is everything in the appendix referenced?" without
  naming an audit.
---

# Appendix cross-reference audit

The job is narrow and easy to get wrong. A supervisor or reviewer wants to know:
**when the main paper makes a claim whose supporting detail lives in an appendix,
does the main text explicitly point there?** — e.g. `(Table~\ref{...})`,
`(Appendix~\ref{...})`.

The most common mistake is answering a different question: *"is every appendix
fact repeated in the main paper?"* It should not be. Prompts, generation
procedures, failed training runs, provenance logs, hashes, and full diagnostic
dumps belong only in the appendix. Dragging them up would make the paper worse
and blow the page limit. So the audit is about **traceability of the results
that are used**, not coverage of everything that exists.

## The one rule

> If a main-text numerical claim, robustness claim, sensitivity claim,
> diagnostic, decomposition, or methodological compression has its supporting
> detail in an appendix table or section, there should be an explicit pointer at
> the end of that claim.

If the pointer is already there and specific enough for a reviewer to find the
evidence, mark it done and move on. Do **not** invent a second citation just so
every appendix letter shows up in the body.

## What counts as "used" (audit these first)

These are the claim types that almost always have appendix backing and are the
ones reviewers actually chase:

- raw scoring / parser accuracies and scorer comparisons
- seed-level robustness ("holds across seeds")
- position / order bias spreads
- withheld-variable or ablation decompositions
- confidence intervals behind a headline table
- sparse-cell counts and coverage caveats
- retrieval / method decompositions (e.g. BM25 vs dense)
- difference-in-differences broken out by condition
- lexical-overlap / leakage robustness
- translation or annotation audits and their sensitivity checks
- protocol repairs / chronology when the main text relies on them

Appendix-only material that needs **no** pointer unless the main text leans on
it: implementation details, prompt text, hyperparameter dumps, abandoned runs,
repository/run hashes, provenance tables.

## How to run the audit

Do it in **both directions** — each direction catches what the other misses.

1. **Forward (appendix → main).** Go appendix by appendix, A, B, C, .... For each
   one, list its substantive contents, decide which of those the main paper
   actually uses or summarizes, find where the main text currently references it,
   and flag any used result with no nearby pointer.
2. **Reverse (main → appendix).** Read pages 1–N and, for every numerical or
   robustness claim, ask whether its support is in an appendix and whether a
   nearby pointer exists.

Work from the **compiled PDF plus the LaTeX that is actually `\input`/`\include`d**.
Ignore stale or unincluded `.tex` files — a pointer that only exists in a file
the build doesn't use is not a real pointer. Do not assume a previous audit was
correct; re-read.

Two ready-to-paste audit prompts (a first pass and a stricter re-audit with a
cross-check table) live in [references/audit-prompts.md](references/audit-prompts.md).
Hand those to a fresh model when you want an independent second opinion.

## Output: the mapping table

Give the user something they can paste into chat and hand to a supervisor. Go
appendix by appendix so it reads top to bottom. Keep it tight — line numbers,
not paragraphs.

```
| Appendix | What of it appears in the main paper | Main-paper line(s) | Pointed to? |
|---|---|---:|---|
| A — Corpus construction | sources + hierarchy-preserving conversion | 187–189 | ✅ Appendix A |
| D / Table 8 — Set composition | 795 / 712 / 658 breakdown | 204–207 | ✅ Table 8 |
| G — Additional results | reversal holds across seeds | 464–465 | ❌ add Appendix G |
```

Status legend, and nothing else:

- ✅ adequately referenced
- 🟡 optional — a nearby pointer already covers it, a second would be tidy not required
- ❌ missing — a used result with no nearby pointer; give the fix

Sort the real problems (❌) to the top of your summary so the user sees the
required work first.

## Output: the minimal fix

For every ❌, give exactly this, nothing more:

1. the exact current sentence,
2. the exact supporting appendix / table,
3. the exact minimal LaTeX change,
4. the number of words it adds (page limits are real).

**Example.**

Current:

```latex
This reversal holds across seeds, although the Gemma adapter shows signs of
over-adaptation.
```

Fix (adds 3 words):

```latex
This reversal holds across seeds (Appendix~\ref{app:addl}), although the Gemma
adapter shows signs of over-adaptation.
```

Never rewrite prose, change a number, alter a claim, or suggest a stylistic
edit. The smallest insertion that makes the claim traceable is the whole job.

## Explaining a table's caption

Supervisors often ask "what does this caption actually mean?" Answer by walking
one concrete row through the arithmetic and naming what the numbers become
elsewhere. Show the reduction, then state the mapping.

> Table 9 decomposes the R−N and R−I values in Table 3 by retriever. For each
> seed we compute the difference-in-differences separately for BM25 and dense,
> average the two within that seed, then report the three-seed mean in Table 3.
> Example: Bangla Llama-3.2-1B, vs. none: (3.0 + 6.0)/2 = 4.5, which is the
> +4.5 shown in Table 3.

## Reporting to a supervisor

The reader is a busy expert who will actually read what you write, so:

- Lead with the verdict and the count: "2 required fixes, both added; the rest
  were already referenced."
- Never label anything "simple version" or "easy version for sir" — they see the
  label and it reads as condescending.
- Don't reproduce the entire mapping when a one-screen summary answers the
  question. Offer the full table, don't force it.
- State plainly what you did and did not touch: "readability and cross-references
  only; no experiments, results, numbers, or claims changed."
- If nothing is missing, say so directly: "no required missing references."
