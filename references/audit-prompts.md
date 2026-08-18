# Ready-to-paste audit prompts

Two prompts. Hand them to a fresh model when you want an independent
cross-reference audit of a compiled paper. The first is a strict first pass; the
second re-audits from scratch and returns a cross-check table you can verify by
hand.

## Prompt 1 — strict first-pass audit

```text
I need a strict appendix cross-reference audit of this paper.

Goal:
Check whether every substantive result, diagnostic, robustness check,
methodological detail, or supporting analysis that appears in the appendix and
is relied on or summarized in the main paper (pages 1–8) is explicitly pointed
to from the relevant place in the main paper.

Important: I am NOT asking whether every appendix detail is repeated in the main
paper. Most appendix-only implementation details, prompts, provenance logs,
training diagnostics, etc. can stay only in the appendix.

What I want you to check is:
- If the main paper states or summarizes a result whose detailed evidence is in
  an appendix table/section, does the main-paper sentence explicitly point to
  that appendix/table?
- If the main paper makes a robustness claim, diagnostic claim, sensitivity
  claim, seed-level claim, retrieval decomposition claim, translation-audit
  claim, scorer comparison, sparse-cell claim, etc. whose supporting detail is
  in the appendix, is there a nearby Appendix X, Table Y, or Section X reference?
- If an appendix table directly supports a numerical claim in the main text,
  flag it if the table is not referenced nearby.
- If the main paper already has an adequate pointer, mark it as covered.
- Do NOT add references merely because an appendix contains extra implementation
  details that the main paper does not rely on.
- Do NOT rewrite prose, change claims, alter numbers, or suggest stylistic edits.
- Do NOT increase text unnecessarily. We have a strict 8-page main-paper limit.
- Prefer the smallest possible fix.

Audit Appendices A–J systematically. For each appendix:
1. List its substantive contents.
2. Identify which of those contents are actually used/summarized in pages 1–8.
3. Show where the main paper currently references them.
4. Flag any used appendix result that lacks an explicit nearby pointer.
5. Give the exact minimal LaTeX insertion needed and the exact sentence/location
   where it should go.

At the end, give me only:
A. Already adequately referenced
B. Missing cross-references that should be added
C. Appendix-only material that does not need a main-text reference

Be conservative. The question is whether every appendix result USED BY THE MAIN
PAPER is traceable from the relevant main-text claim.
```

## Prompt 2 — from-scratch re-audit with a cross-check table

```text
Please re-audit the current compiled paper from scratch for appendix
cross-references.

Goal:
Check whether every substantive appendix result, diagnostic, robustness check,
methodological detail, or supporting analysis that is USED, summarized, or relied
on in the main paper (pages 1–8) has an explicit nearby pointer to the relevant
appendix section or appendix table.

Important:
- Do NOT assume your previous audit was correct.
- Re-read the current compiled paper and current LaTeX source.
- Ignore stale/unincluded .tex files. Only analyze the files actually included
  in the compiled paper.
- I am NOT asking whether every appendix detail should appear in the main paper.
  Appendix-only implementation details, prompts, provenance logs, failed runs,
  hashes, etc. can remain appendix-only if the main paper does not rely on them.

Audit rule: for each main-paper claim supported by appendix material, ask:
1. Is the supporting appendix result actually used or summarized here?
2. Is there a nearby explicit pointer such as Appendix~\ref{...}, Table~\ref{...},
   or Section~\ref{...}?
3. If yes, is that pointer specific enough for a reviewer to find the evidence?
4. If not, flag it.

Pay special attention to: raw scoring/parser accuracies; seed-level robustness;
over-adaptation claims; position-bias results; withheld-variable decomposition;
confidence intervals underlying main tables; sparse-cell counts; method
decompositions (e.g. BM25 vs dense); difference-in-differences by condition;
lexical-overlap robustness; translation-audit and translation-robustness claims;
protocol repairs/chronology; training details the main text explicitly relies on;
reproducibility/release claims only if the appendix is needed as evidence.

Audit Appendices A–J one by one, then do the reverse check: go through pages 1–8
and identify every numerical or robustness claim supported by an appendix table
or analysis, and confirm each has an explicit nearby pointer.

Do NOT: rewrite prose; change numbers; suggest scientific or stylistic changes;
add references just so every appendix letter appears; increase text unnecessarily.

For every missing reference, give: (1) exact current sentence; (2) exact
supporting appendix/table; (3) exact minimal LaTeX change; (4) number of added
words.

OUTPUT FORMAT — give me a TABLE so I can cross-check every item by hand:

| Main paper section | Main-text claim / sentence | Main-text location (file + line) | Supporting appendix | Supporting appendix table/section | Current cross-reference | Status | Exact fix if missing |

Status is ONLY one of: ADEQUATE, MISSING, OPTIONAL.

After the table, give:
A. Required fixes only
B. Optional references
C. Appendix material not used in the main paper
D. Final count of required fixes

Be conservative. If the main text already has a sufficiently nearby pointer
covering the claim, mark it ADEQUATE rather than inventing another citation.
```
