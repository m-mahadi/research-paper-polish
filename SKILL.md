---
name: research-paper-polish
description: >-
  Line-edit and clarity-audit a research-paper manuscript (ACL/EMNLP/NLLP style
  and similar) so it reads precisely and easily WITHOUT changing the science.
  The enemy is cognitive load, not grammar. Use this whenever someone is editing,
  polishing, or finalizing a paper draft and says things like "polish this
  section", "make this readable", "line edit this", "is this too dense / a
  mouthful", "does this sound AI-generated", "reduce cognitive load", "clarity
  pass", "tighten this without adding length", "check the appendix references /
  did we cite every table", "what does this caption mean", "% vs percentage
  points", or "is the paper ready to submit". Also use it to run a whole-
  manuscript clarity audit, a final freeze/blocker check, or an appendix
  traceability audit. Trigger even when the request is loose ("make this easier
  to read", "does this flow", "clean up my methods section").
---

# Research paper polish

For the writing stage of a paper: the science is settled and now the prose has to
carry it. A paper can be technically correct and still exhausting to read if the
reader must hold too many distinctions in working memory at once. **The problem to
fix is cognitive load, not grammar.**

The reading experience you are steering toward is:

> **claim → reason/evidence → implication**

not

> setup → terminology → qualification → another qualification → result →
> explanation several sentences later.

The whole job is to lower reader effort while keeping the science, the numbers,
and the level of certainty exactly as they are.

## Who you're writing for

Anchor every edit to one imagined reader: **competent in the field, but knowing
nothing about this specific project.** They understand the discipline — the
methods, the statistics, the general techniques — but they have never seen your
dataset, your conditions, your control, your metric, or your method. Every rule
below is a consequence of writing for that person.

So:

- **Explain everything, step by step, in order.** Walk the reader from setup to
  result. Don't assume they can reconstruct a setup from a sentence three
  paragraphs later, or fill a gap from knowledge only your team has.
- **Never name a thing before you've explained it.** No term, method, metric,
  condition, control, or abbreviation should appear before its meaning is on the
  page. The reader should never have to infer what a word means from how it's
  used later.
- **Unpack before you compress.** Say the idea in plain words first, then
  introduce the shorthand, name, or formula that stands for it.
- **Make every sentence easy on the first read.** If the reader would have to go
  back and re-read it to parse it, it's too dense — split it, reorder it, or cut
  a distinction out of it.

The test for any paragraph: *could this reader follow what you did without asking
you a question afterward?* If the answer is no, the prose is still too compressed,
and the fix goes on the page — not into a verbal explanation.

## Do the two stages in order

Facts first, prose second — mixing them means editing sentences you're about to
delete or that are about to change meaning.

1. **Scientific consistency.** Contradictions, unsupported claims,
   result/caption mismatches, stale text left over from an experiment or table
   update, wrong numbers, causal overreach. Get the facts stable.
2. **Readability.** Only once the facts hold: simplify, reorder, cut cognitive
   load, tighten transitions.

Don't start a stylistic pass while the numbers might still move.

## Non-negotiable constraints

**Preserve the science.** Never change experiments, results, model names, numbers,
statistical meaning, caveats, conclusions, level of certainty, citations,
methodological meaning, or terminology that carries a precise experimental
meaning. Never add claims, remove substantive claims, inflate novelty, add
deployment claims, turn a descriptive finding into a causal one, or hide a null
or negative result.

**Same length or shorter.** The main paper has a strict page budget, so a clarity
fix that adds words usually isn't a fix. Improve prose by *replacing* a dense
phrase with a clearer one, moving the explanation before the shorthand, deleting
redundant setup, combining repeated caveats, and removing process narration — not
by adding explanation everywhere. Report original and revised word counts.

**Line editor, not ghostwriter.** Don't rewrite a paragraph just because another
wording is possible. If a sentence is already clear, precise, and doing useful
work, the correct output is **KEEP IT**. The purpose is to minimize reader effort,
not to maximize textual difference.

## Per-paragraph diagnostic

Before touching a paragraph, check that a reader who doesn't know the project can
answer:

- What is the immediate claim, and why is this paragraph here?
- What do they need to know *before* this sentence?
- Is a technical term used before it is explained?
- Does the result appear before they understand the comparison?
- Can they tell what changed, what was held fixed, and why?
- Is the sentence asking them to hold too many objects at once?

A strong technical paragraph lets the reader answer: **what are we comparing? why?
what happened? what does that let us conclude?**

## Style rules

These are the recurring fixes. Each has a why — apply the reasoning, not the
letter.

**State the problem, not the process.** Process narration ("We set out to…", "We
wanted to…", "Our goal was to…", unnecessary "We ask whether…") delays the actual
point. Open with the scientific claim.
- Avoid: *We set out to investigate whether fine-tuning helps models use supplied legal context.*
- Prefer: *Fine-tuning can improve legal-QA accuracy without improving use of supplied law.*

**Operation first, name second.** Don't introduce a compact name before the reader
knows what it stands for.
- Harder: *We use constrained option scoring.*
- Clearer: *We append `FINAL ANSWER: (` and select the highest-scoring next token among A, B, C, and D. We call this constrained option-letter scoring.*

The same pattern rescues any dense method term — unpack the idea, *then* name it.
For a difference-in-differences: first say that a fine-tuned model can improve even
with no supplied law, so a general gain doesn't show more reliance on law; then
compare how much context helps after vs. before fine-tuning; then give the formula
and say what a positive value means. For a rotation criterion: describe rotating
the answer choices through all four positions and counting an item correct only if
it's right in every rotation, *then* call it strict consistency.

**No implementation clutter in main prose.** Script names, notebook filenames,
internal run names, helper-function names (`bootstrap_gold.py`, and the like)
belong in appendices. The main text discusses the method or analysis, not the file
that performs it — unless reproducibility specifically requires the name there.

**Name the referent when it's ambiguous.** "this effect", "this result", "the
method", "it" — if more than one referent is possible, say which one. The reader
should never have to guess what "this" points back to.

**Concrete numbers over rhetoric.** Numbers reduce the ambiguity that adjectives add.
- Prefer *the gain is +3.0%* over *the improvement is dramatically smaller.*
- Prefer *five of six models improve by 14.7–19.3%* over *most models improve substantially.*

**Preserve precise experimental terms.** Where a word names the experimental object
(e.g. a legal *section* the model receives, vs. a looser synonym), keep it — a
casual swap can quietly change what was measured. Likewise keep distinctions the
experiment depends on: retrieval failing to supply the needed item, versus the
item being present but unused, versus the evaluation misreading the output, are
three different things and must not collapse into one generic "model failure".

**State each caveat once, compactly.** Don't remove limitations, but don't restate
the same caution in several rhetorical forms. Say it once, concretely, next to the
claim it limits.

## The "AI-ish writing" audit

A whole-manuscript pass often turns up one dominant tic: the repeated shape

> claim → qualification → contrast → cautious conclusion

built from constructions like "X, not Y", "supports, but does not prove", "rather
than", "does not establish", "should not be interpreted as". Any one of these is
fine. The problem is repetition across the paper — it reads as over-engineered or
machine-written.

- **Preserve** the things that make a paper feel grounded: awkward experimental
  details, concrete numbers, negative findings, human judgments, limitations,
  implementation decisions that matter scientifically.
- **Reduce** rhetorical symmetry, generic section-opening framing, "This finding
  is important because…" labels, reader-directed interpretation when the evidence
  already speaks, and repeated contrast templates.

## Explaining a table or caption

When asked what a caption or table "means", don't restate the columns — show how it
relates to the main result and walk one concrete row through the arithmetic. A good
caption test: **it should make clear how an appendix table relates to the main
table, not merely describe its columns.**

> Table 9 is an extension of Table 3. Table 3 reports the mean of the BM25 and
> dense DiD values; Table 9 shows BM25 and dense separately alongside that mean.
> Example — Bangla Llama-3.2-1B, vs. none: BM25 +3.0, dense +6.0, mean +4.5, which
> is the +4.5 in Table 3.

If an explanation still needs oral interpretation afterward, the prose or caption
is too compressed — fix it there, not in conversation.

## Appendix traceability

Separate from prose polish: when the main text makes a claim whose supporting
detail lives in an appendix, it should point there explicitly.

> If a main-text numerical claim, robustness claim, diagnostic, or methodological
> compression has supporting evidence in an appendix table or section, add a nearby
> `(Appendix~\ref{…})` / `(Table~\ref{…})` pointer.

This is about traceability of results the paper *uses*, not coverage of everything
the appendix contains — implementation details, prompts, provenance, and failed
runs can stay appendix-only. Don't add a citation just so every appendix letter
appears. Audit both directions (appendix → main, and main → appendix) and give,
for each gap, the exact sentence, the supporting table, and the smallest LaTeX
insertion. The full audit prompt is in [references/prompts.md](references/prompts.md).

## A note on statistical wording

`%` vs. percentage points recurs. Rather than reopening the whole paper for a
notation rewrite, one manuscript-wide sentence usually settles it: *"All accuracy
differences are absolute on the 0–100 percentage scale, not relative changes."*
That keeps the compact `%` notation while fixing the meaning.

## When to stop

Broad editing should end once the reader can follow the experiment, terminology is
stable, and every claim is supported — remaining changes are then just personal
preference. At that point run the freeze audit (objective blockers only: grammar,
inconsistencies, number mismatches, stale terminology, wrong references, undefined
shorthand, claims stronger than the evidence) and **do not open another stylistic
pass**. Then freeze the prose and send the paper.

## Reusable prompts

[references/prompts.md](references/prompts.md) has four paste-ready prompts for
handing a pass to a fresh model: (1) section-by-section line editor, (2) whole-
manuscript clarity audit, (3) final freeze audit, (4) appendix cross-reference
audit.
