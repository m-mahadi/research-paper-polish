---
name: research-paper-polish
description: >-
  Line-edit and clarity-audit a research-paper manuscript (ACL/EMNLP/NLLP style
  and similar) so it reads precisely and lands on a single pass, WITHOUT changing
  the science. The enemy is cognitive load, not grammar. Use this whenever someone
  is editing, polishing, or finalizing a paper draft and says things like "polish
  this section", "make this readable", "line edit this", "is this too dense / a
  mouthful", "does this sound AI-generated", "reduce cognitive load", "clarity
  pass", "make the method feel inevitable", "tighten this without adding length",
  "are my headings/paragraphs doing their job", "is my confidence calibrated",
  "check the appendix references / did we cite every table", "what does this
  caption mean", "% vs percentage points", or "is the paper ready to submit". Also
  use it to state the controlling idea, run a whole-manuscript clarity audit, a
  final freeze/blocker check, or an appendix traceability audit. Trigger even when
  the request is loose ("make this easier to read", "does this flow", "clean up my
  methods section").
---

# Research paper polish

For the writing stage of a paper: the science is settled and the prose now has to
carry it. A paper can be technically correct and still exhausting to read when the
reader must hold too many distinctions in working memory at once. The problem to
fix is cognitive load, not grammar.

Steer the reading experience toward

> **claim, then reason/evidence, then implication**

and away from

> setup, terminology, qualification, another qualification, result, and an
> explanation several sentences later.

The whole job is to lower reader effort while keeping the science, the numbers,
and the level of certainty exactly as they are.

## Who you're writing for

Anchor every edit to one imagined reader: **competent in the field, but knowing
nothing about this specific project.** They understand the discipline (the
methods, the statistics, the general techniques), but they have never seen your
dataset, your conditions, your control, your metric, or your method. Every rule
below is a consequence of writing for that person.

So:

- **Explain everything, step by step, in order.** Walk the reader from setup to
  result. Do not assume they can reconstruct a setup from a sentence three
  paragraphs later, or fill a gap from knowledge only your team has.
- **Never name a thing before you have explained it.** No term, method, metric,
  condition, control, or abbreviation should appear before its meaning is on the
  page. The reader should never have to infer what a word means from how it is
  used later.
- **Unpack before you compress.** Say the idea in plain words first, then
  introduce the shorthand, name, or formula that stands for it.
- **Make every sentence easy on the first read.** If the reader would have to go
  back and re-read it to parse it, it is too dense. Split it, reorder it, or cut a
  distinction out of it.

The test for any paragraph: *could this reader follow what you did without asking
you a question afterward?* If the answer is no, the prose is still too compressed,
and the fix goes on the page, not into a verbal explanation.

## The controlling idea

Every paper orbits one insight the reader takes away. State it in a single
sentence before drafting, and check that every section, table, and figure ladders
up to it. If you cannot state it in one sentence, the paper is not ready to draft,
and a list of loosely connected contributions is not a controlling idea.

Reinforce that sentence in the same words throughout. Rephrasing the thesis in
fresh synonyms each section reads as drift, not range. The abstract says what was
learned, not which techniques were used; the conclusion crystallises the takeaway
rather than re-listing results.

## How it should read on the first pass

The reader should reach your method and feel they could have proposed it. That
feeling is not evidence the work was easy; it is evidence the writing did its job.
Most readable papers share one argument shape:

    familiar capability or setup
      -> one precise limitation, with a concrete case where it fails
        -> one surprisingly simple observation
          -> an intervention the reader could have imagined
            -> progressively stronger tests of it

The moves that produce that feeling:

- **Open on something granted, then instance the limitation.** First a sentence no
  one will argue with, then the precise thing that setup cannot do, attached to a
  case the reader can picture. "The parser fails on answers that omit the letter
  prefix" motivates a method; "models struggle with formatting" is filed away and
  forgotten. A picture motivates; an abstract gap does not.
- **A concrete instance before every load-bearing abstraction.** Order is
  instance, then name, then definition, never the reverse. One real question, its
  retrieved provision, and one model answer should appear before the metric that
  scores them.
- **Make the contribution look small.** State the method in one plain sentence
  with no framework nouns (paradigm, pipeline, architecture) around it, and let
  the results argue for it. A method that sounds elaborate invites the reviewer to
  ask whether the elaboration was necessary; one that sounds obvious invites them
  to check the numbers, which is where you want them. Never inflate a difficulty
  so the solution looks impressive.
- **Let a named constraint force each design choice.** Justify a choice by the
  alternative it rules out or the confound it prevents, not by a stated benefit.
  "We freeze X because it prevents Y" carries more than "we freeze X for
  stability", and it moves the argument onto the constraint instead of the choice.
- **Sequence experiments as the reader's next doubt.** Each result answers the
  question the previous one raised, so Results reads as an argument, not a
  benchmark dump. Before drafting, write the doubt each cluster answers, in order.
  A cluster that answers no doubt belongs in the appendix.
- **Concede inline when the concession is immediately answerable.** When the
  reader is about to notice a weakness, name it, say why it is expected, and bound
  it in the same paragraph. If it cannot be answered there, it is a limitation and
  it waits for the Limitations section.

None of this licenses bending the evidence. A finding that is really a null, a
mixed effect, or a dissociation is presented on this arc; it does not acquire a
cleaner one. Order experiments by the reader's doubt, never by whichever order
flatters the result.

## Do the two stages in order

Facts first, prose second. Mixing them means editing sentences you are about to
delete or that are about to change meaning.

1. **Scientific consistency.** Contradictions, unsupported claims,
   result/caption mismatches, stale text left over from an experiment or table
   update, wrong numbers, causal overreach. Get the facts stable.
2. **Readability.** Only once the facts hold: simplify, reorder, cut cognitive
   load, tighten transitions.

Do not start a stylistic pass while the numbers might still move.

## Non-negotiable constraints

**Preserve the science.** Never change experiments, results, model names, numbers,
statistical meaning, caveats, conclusions, level of certainty, citations,
methodological meaning, or terminology that carries a precise experimental
meaning. Never add claims, remove substantive claims, inflate novelty, add
deployment claims, turn a descriptive finding into a causal one, or hide a null or
negative result.

**Same length or shorter.** The main paper has a strict page budget, so a clarity
fix that adds words usually is not a fix. Improve prose by *replacing* a dense
phrase with a clearer one, moving the explanation before the shorthand, deleting
redundant setup, combining repeated caveats, and removing process narration,
rather than by adding explanation everywhere. Report original and revised word
counts.

**Line editor, not ghostwriter.** Do not rewrite a paragraph just because another
wording is possible. If a sentence is already clear, precise, and doing useful
work, the correct output is **KEEP IT**. The purpose is to minimize reader effort,
not to maximize textual difference.

## Structure and paragraphs

Work the skeleton before the sentences.

- **One message per paragraph, stated first.** Put the point in the opening
  sentence, then evidence, then meaning, then boundary. A paragraph carrying two
  arguments is two paragraphs, and a paragraph whose point only emerges at the end
  makes the reader hold everything until then.
- **Close every paragraph.** The last sentence concludes, synthesises, or sets up
  the next. Endings like "which we detail below" or a trailing bare citation leave
  it hanging.
- **Bridge adjacent paragraphs explicitly** with a real logical move: cause,
  contrast, consequence, refinement, or example. Paragraph-to-paragraph breaks are
  a more common failure than section-to-section ones.
- **Headings are claims, not topics.** "Five checkpoints benefit from supplied
  law" beats "Results". A skim-reader should learn the finding from the heading.
- **Keep decompositions consistent.** If a section promises X, Y, and Z, the
  subsections cover exactly X, Y, and Z, in that order, with the same names and
  count wherever they reappear. An intro promising three things and delivering two
  is a structural bug.
- **Reverse-outline before calling a section done.** Write the thesis, then each
  paragraph's topic sentence, then the evidence under each, and check that every
  topic sentence maps to the thesis and every piece of evidence maps to its topic
  sentence. If reverse-outlining is hard, the structure is the problem, not the
  prose.

Then, before touching a paragraph, confirm a reader who does not know the project
can answer: what is the claim, and why is this paragraph here? What did they need
to know before this sentence? Is a term used before it is explained? Does the
result arrive before the comparison? Can they tell what changed, what was held
fixed, and why? Is the sentence asking them to hold too many objects at once? A
strong technical paragraph lets them answer: what are we comparing, why, what
happened, and what does that let us conclude.

## Style rules

These are the recurring fixes. Each carries its reasoning; apply the reasoning,
not the letter.

**State the problem, not the process.** Process narration ("We set out to...",
"We wanted to...", "Our goal was to...", unnecessary "We ask whether...") delays
the point. Open with the scientific claim.
- Avoid: *We set out to investigate whether fine-tuning helps models use supplied legal context.*
- Prefer: *Fine-tuning can improve legal-QA accuracy without improving use of supplied law.*

**Operation first, name second.** Do not introduce a compact name before the
reader knows what it stands for.
- Harder: *We use constrained option scoring.*
- Clearer: *We append `FINAL ANSWER: (` and select the highest-scoring next token among A, B, C, and D. We call this constrained option-letter scoring.*

The same pattern rescues any dense method term: unpack the idea, *then* name it.
For a difference-in-differences, first say that a fine-tuned model can improve even
with no supplied law, so a general gain does not show more reliance on law; then
compare how much context helps after versus before fine-tuning; then give the
formula and say what a positive value means. For a rotation criterion, describe
rotating the answer choices through all four positions and counting an item
correct only if it is right in every rotation, then call it strict consistency.

**Function before formula.** Say what a component or metric buys before defining
it. A reader who knows what a quantity is for will follow its definition; a reader
who meets the definition first has to hold it unexplained until the payoff arrives.
A version string, a scorer ID, or a config name is a label, not an explanation.

**No implementation clutter in main prose.** Script names, notebook filenames,
internal run names, helper-function names (`bootstrap_gold.py` and the like)
belong in appendices. The main text discusses the method or analysis, not the file
that performs it, unless reproducibility specifically requires the name there.

**Name the referent when it is ambiguous.** "this effect", "this result", "the
method", "it": if more than one referent is possible, say which one. The reader
should never have to guess what "this" points back to. Every mechanism, baseline,
metric, and control should have a proper name; a term that could appear in any
paper in the field is not doing work in this one.

**Concrete numbers over rhetoric.** Numbers reduce the ambiguity that adjectives add.
- Prefer *the gain is +3.0%* over *the improvement is dramatically smaller.*
- Prefer *five of six models improve by 14.7 to 19.3%* over *most models improve substantially.*

**Calibrated confidence.** Assertive for measured facts ("achieves", "rises by
14.7 points", "reverses"); hedged for causal explanation ("we observe", "this
suggests", "the likeliest cause"). Never hedge a number, and never assert an
unproven mechanism. "Because" or "leads to" in an assertive tone smuggles in a
mechanism you did not measure; "may" or "could" modifying a reported result
under-claims a fact you did.

**Say what the system did, not what it knew.** A model selects, predicts, or
scores. It does not understand, believe, or reason unless that is what you
measured.

**Preserve precise experimental terms.** Where a word names the experimental
object (a legal *section* the model receives, versus a looser synonym), keep it; a
casual swap can quietly change what was measured. Keep distinctions the experiment
depends on: retrieval failing to supply the needed item, the item being present
but unused, and the evaluation misreading the output are three different things
and must not collapse into one generic "model failure". Choose one canonical term
per concept and use it everywhere; synonym cycling reads as drift after a few
revision rounds.

**State each caveat once, compactly.** Do not remove limitations, but do not
restate the same caution in several rhetorical forms. Say it once, concretely,
next to the claim it limits.

## The "AI-ish writing" audit

A whole-manuscript pass often turns up one dominant tic: the repeated shape

> claim, then qualification, then contrast, then cautious conclusion

built from constructions like "X, not Y", "supports, but does not prove", "rather
than", "does not establish", "should not be interpreted as". Any one is fine; the
problem is repetition across the paper, which reads as over-engineered or
machine-written. Concretely, hunt for:

- **Rhetorical negation as decoration** ("X, not Y", "not only ... but also",
  "rather than") where a positive statement carries the same content. Keep factual
  negations that name a real gap ("the model cannot recover the provision").
- **Throat-clearing openers**: Moreover, Furthermore, Additionally, Notably,
  Importantly, Crucially, Indeed, It is worth noting that. Start with the claim;
  keep a discourse marker only when a real logical move follows it.
- **Filler adjectives**: novel, significant, substantial, comprehensive, robust,
  powerful, promising, state-of-the-art. Replace with a number, a named mechanism,
  or nothing. Domain terms keep their technical sense ("significant" is fine for
  statistically significant).
- **Fake depth from trailing -ing clauses**: "highlighting the importance of",
  "underscoring its role", "reflecting the broader trend". Cut them.
- **Significance inflation and vague authority**: "pivotal", "a testament to",
  "marks a turning point", "studies show" with no named study.
- **Rule-of-three padding** when the three members are near-synonyms.
- **Uniform rhythm**: identical sentence lengths and identically sized paragraphs
  are a tell. Let the idea set the length.
- **Em dashes**: house rule, none in paper prose outside a verbatim quotation.
  Replace with a comma, colon, parentheses, or a new sentence.
- **Two claims stitched into one sentence**: if a sentence needs "while",
  "unlike", or a semicolon to join separate claims, it is two sentences.
- **Wordy stock phrases**: "in order to" to "to", "due to the fact that" to
  "because", "utilize" to "use", "demonstrate" to "show", "it is worth noting
  that" to nothing.

What to **preserve**, because it makes a paper feel grounded: awkward experimental
details, concrete numbers, negative findings, human judgments, limitations, and
implementation decisions that matter scientifically. What to **reduce**:
rhetorical symmetry, generic section-opening framing, "This finding is important
because..." labels, reader-directed interpretation when the evidence already
speaks, and repeated contrast templates.

## Explaining a table or caption

When asked what a caption or table "means", do not restate the columns. Show how
it relates to the main result and walk one concrete row through the arithmetic. A
good caption test: **it should make clear how an appendix table relates to the
main table, not merely describe its columns.**

> Table 9 is an extension of Table 3. Table 3 reports the mean of the BM25 and
> dense DiD values; Table 9 shows BM25 and dense separately alongside that mean.
> Example, Bangla Llama-3.2-1B, vs. none: BM25 +3.0, dense +6.0, mean +4.5, which
> is the +4.5 in Table 3.

Two rules make floats pull their weight:

- **Interpret, do not merely cite.** "Figure 3 shows the gap closing as format
  compliance rises" tells the reader what to notice; "see Figure 3" makes them
  hunt for it.
- **Captions are self-sufficient.** A caption states what the visual shows,
  defines its symbols and units, and names the takeaway, so a caption-scanner gets
  the point before deciding to read the body.

If an explanation still needs oral interpretation afterward, the prose or caption
is too compressed. Fix it there, not in conversation.

## Appendix traceability

Separate from prose polish: when the main text makes a claim whose supporting
detail lives in an appendix, it should point there explicitly.

> If a main-text numerical claim, robustness claim, diagnostic, or methodological
> compression has supporting evidence in an appendix table or section, add a nearby
> `(Appendix~\ref{...})` or `(Table~\ref{...})` pointer.

This is about traceability of results the paper *uses*, not coverage of everything
the appendix contains. Implementation details, prompts, provenance, and failed
runs can stay appendix-only. Do not add a citation just so every appendix letter
appears. Audit both directions (appendix to main, and main to appendix) and give,
for each gap, the exact sentence, the supporting table, and the smallest LaTeX
insertion. The full audit prompt is in [references/prompts.md](references/prompts.md).

## A note on statistical wording

`%` versus percentage points recurs. Rather than reopening the whole paper for a
notation rewrite, one manuscript-wide sentence usually settles it: *"All accuracy
differences are absolute on the 0 to 100 percentage scale, not relative changes."*
That keeps the compact `%` notation while fixing the meaning.

## When to stop

Broad editing should end once the reader can follow the experiment, terminology is
stable, and every claim is supported. Remaining changes are then just personal
preference. At that point run the freeze audit (objective blockers only: grammar,
inconsistencies, number mismatches, stale terminology, wrong references, undefined
shorthand, claims stronger than the evidence) and **do not open another stylistic
pass**. Read the final PDF once for argument and once for visual defects; a clean
compile is not a visual check. Then freeze the prose and send the paper.

## Reusable prompts

[references/prompts.md](references/prompts.md) has four paste-ready prompts for
handing a pass to a fresh model: (1) section-by-section line editor, (2)
whole-manuscript clarity audit, (3) final freeze audit, (4) appendix
cross-reference audit.
