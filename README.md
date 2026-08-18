# research-paper-polish

A Claude skill for the **writing stage** of a research paper (ACL/EMNLP/NLLP style
and similar): line-edit and clarity-audit a manuscript so it reads precisely and
easily **without changing the science**. The target it fixes is *cognitive load*,
not grammar — a paper can be technically correct and still exhausting to read.

## What it does

- **A reader model** the whole skill hangs off: field-competent, but knows nothing
  about your project, so explain step by step and never name a thing before you've
  explained it.
- **The controlling idea** — one insight, one sentence, everything ladders to it,
  reinforced in the same words.
- **First-read craft** so the method feels inevitable: open on a granted capability
  then instance the limitation, a concrete instance before every abstraction, make
  the contribution look small, sequence experiments by the reader's next doubt,
  concede inline.
- **Line editing** toward `claim, reason/evidence, implication`, same length or
  shorter, keeping strong sentences unchanged ("KEEP IT" is a valid output).
- **A two-stage workflow**: scientific consistency first, readability second, so
  you don't polish sentences that are about to change.
- **Structure discipline** — message-first paragraphs, headings that state the
  finding, and reverse-outlining to catch broken skeletons.
- **Style rules** with the reasoning behind each: state the problem not the
  process, operation and function before name, calibrated confidence (assert facts,
  hedge mechanisms), say what the system did not what it "knew", concrete numbers
  over rhetoric.
- **An "AI-ish writing" audit** — a concrete tell-list (rhetorical negation,
  throat-clearing openers, filler adjectives, fake-depth -ing clauses, the
  no-em-dash house rule) plus what to preserve vs. reduce.
- **Appendix traceability**, **caption/float explanation**, the `%` vs.
  percentage-points fix, and a **final freeze audit** that finds only objective
  blockers and stops.

## Install

Clone into your Claude skills directory:

```bash
git clone https://github.com/<you>/research-paper-polish \
  ~/.claude/skills/research-paper-polish
```

Claude loads it automatically when a request matches the description in
`SKILL.md` (polishing/line-editing a paper, "make this readable", "is this too
dense", "does this sound AI-generated", clarity audits, appendix reference checks,
"what does this caption mean", "is the paper ready to submit").

## Contents

- `SKILL.md` — the workflow, constraints, per-paragraph diagnostic, style rules,
  the AI-ish audit, caption explanation, appendix traceability, and the freeze rule.
- `references/prompts.md` — four paste-ready prompts: section-by-section line
  editor, whole-manuscript clarity audit, final freeze audit, and appendix
  cross-reference audit.
