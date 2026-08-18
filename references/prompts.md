# Reusable prompts

Four paste-ready prompts for a research-paper clarity workflow, ordered by how
you'd use them across a draft's life. Each is deliberately constrained to
preserve the science and the page budget. Hand any of them to a fresh model when
you want an independent pass.

1. [Section-by-section line editor](#1-section-by-section-line-editor) — the everyday pass
2. [Whole-manuscript clarity audit](#2-whole-manuscript-clarity-audit) — one cognitive-load sweep
3. [Final freeze audit](#3-final-freeze-audit) — objective blockers only, no more polishing
4. [Appendix cross-reference audit](#4-appendix-cross-reference-audit) — traceability of used results

---

## 1. Section-by-section line editor

```text
I will paste my manuscript one section at a time.

Act as a careful line editor, not a ghostwriter.

Improve clarity, flow, precision, economy, and readability while preserving:
- my scientific meaning;
- experiments;
- results;
- exact numbers;
- statistical meaning;
- caveats;
- conclusions;
- terminology;
- citations;
- level of certainty.

Hard constraints:
- NEVER increase the word count unless a technical correction absolutely requires it.
- Prefer the same length or shorter.
- Do not add new claims.
- Do not remove substantive claims.
- Do not change experimental meaning.
- Do not inflate novelty.
- Do not make the prose more complicated merely to sound academic.
- Keep strong sentences unchanged.

Assume the reader is an NLP researcher who knows nothing about this specific
experiment. The reader should not have to infer what a term means from later
sentences.

For each passage:

1. Diagnose only genuine weaknesses. Check clarity, logic, flow, ambiguity,
   redundancy, grammar, jargon, and unexplained shorthand. Do not invent problems.

2. Ask whether the paragraph immediately communicates:
   - the claim;
   - why the paragraph exists;
   - what comparison is being made;
   - how it connects to the paper's argument.

3. Rewrite only where necessary. Prefer direct claim -> evidence/reason -> implication.

4. Avoid:
   - "We set out to...", "We wanted to...", unnecessary "We ask...";
   - filler transitions;
   - vague framing;
   - implementation filenames;
   - jargon before explanation;
   - long noun phrases;
   - repeated caveats;
   - rhetorical "X, not Y" constructions when a direct statement works.

5. Introduce technical operations before shorthand names.

6. Preserve LaTeX citations, table references, appendix references, labels, and
   technical notation.

7. Give:
   A. Brief diagnosis
   B. Revised passage
   C. Original word count
   D. Revised word count

If the passage is already strong, say KEEP IT and explain briefly why.
```

---

## 2. Whole-manuscript clarity audit

```text
Audit this manuscript for writing clarity and cognitive load.

This is NOT a scientific-review pass unless a writing problem changes scientific
meaning.

Assume the reader is an NLP researcher who has never seen this project before.

Evaluate whether the paper is:
- easy to follow;
- precise;
- concise;
- internally consistent in terminology;
- understandable without reading later sections first.

Look specifically for:
1. Sentences that require too much information in working memory.
2. Jargon or shorthand introduced before explanation.
3. Paragraphs whose purpose is unclear until the end.
4. Results given before the comparison/setup is understood.
5. Vague referents such as "this," "it," "the effect," or "the method."
6. Process narration ("We set out...", "We wanted...", unnecessary "We ask...").
7. Repeated rhetorical structures ("X, not Y"; "supports but does not prove";
   "rather than"; repeated claim -> caveat -> contrast -> caution patterns).
8. Dense noun phrases and sentences that feel like a mouthful.
9. Implementation filenames or internal code terminology in the main prose.
10. Repeated explanation of the same caveat.
11. Claims whose evidence/reason appears too far away.
12. Method names introduced before the reader knows what the method does.

For every issue:
- quote the exact sentence;
- explain the readability problem in one short sentence;
- give the smallest possible revision;
- preserve all numbers, results, caveats, and claims;
- keep the revision the same length or shorter.

Do not rewrite sections merely because another version is possible.

At the end classify the manuscript:
A. Effortless to follow
B. Clear but somewhat dense
C. Technically understandable but high cognitive load
D. Difficult to follow

Then list only the 5-10 edits with the highest readability payoff.
```

---

## 3. Final freeze audit

Use only when the manuscript is already strong. The goal is to stop editing, not
to find one more thing to smooth.

```text
This manuscript has already been heavily edited.

Do NOT perform another prose-polishing pass.

Audit only for objective blockers:
- grammar errors;
- factual/internal inconsistencies;
- number mismatches;
- stale terminology;
- wrong table/appendix references;
- undefined shorthand;
- claims stronger than the reported evidence;
- statistical wording that changes meaning.

If something is merely stylistic or optional, do not flag it.

Return only:
1. BLOCKERS
2. MECHANICAL FIXES
3. SAFE TO SEND? YES/NO
```

---

## 4. Appendix cross-reference audit

Checks that every appendix result the main text relies on is traceable from the
exact claim that uses it — without dragging appendix-only material up into the
page budget.

```text
Please audit the current compiled paper from scratch for appendix cross-references.

Goal:
Check whether every substantive appendix result, diagnostic, robustness check,
methodological detail, or supporting analysis that is USED, summarized, or relied
on in the main paper has an explicit nearby pointer to the relevant appendix
section or appendix table.

Important:
- Do NOT assume a previous audit was correct.
- Read the current compiled paper and current LaTeX source.
- Ignore stale/unincluded .tex files.
- I am NOT asking whether every appendix detail should appear in the main paper.
- Appendix-only implementation details, prompts, provenance logs, failed runs,
  hashes, etc. can remain appendix-only.

For each main-text claim supported by appendix material, ask:
1. Is the supporting appendix result actually used or summarized here?
2. Is there a nearby explicit pointer?
3. Is that pointer specific enough for a reviewer to find the evidence easily?
4. If not, flag it.

Audit Appendices A-J one by one. Then perform the reverse check: go through the
main paper and identify every numerical, robustness, diagnostic, or methodological
claim supported by appendix analysis, and confirm each has an explicit nearby
pointer.

Output a table:

| Main paper section | Main-text claim | Main-text location | Supporting appendix | Supporting table/section | Current pointer | Status | Minimal fix |

Status must be one of: ADEQUATE, MISSING, OPTIONAL.

Do not: rewrite prose; change numbers; suggest scientific changes; suggest
stylistic edits; add references merely so every appendix letter appears; increase
text unnecessarily.

Be conservative.
```
