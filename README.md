# research-paper-polish

A Claude skill for the **writing stage** of a research paper (ACL/EMNLP/NLLP style
and similar): line-edit and clarity-audit a manuscript so it reads precisely and
easily **without changing the science**. The target it fixes is *cognitive load*,
not grammar — a paper can be technically correct and still exhausting to read.

## What it does

- **Line editing** toward `claim → reason/evidence → implication`, same length or
  shorter, keeping strong sentences unchanged ("KEEP IT" is a valid output).
- **A two-stage workflow** — scientific consistency first, readability second — so
  you don't polish sentences that are about to change.
- **Concrete style rules** with the reasoning behind each: state the problem not
  the process, operation before shorthand name, no implementation filenames in
  main prose, name ambiguous referents, concrete numbers over rhetoric, state each
  caveat once.
- **An "AI-ish writing" audit** for the repeated `claim → qualification → contrast
  → caution` tic that makes prose read as machine-written.
- **Appendix traceability** — checking the main text points to every appendix
  result it relies on, without over-citing.
- **Explaining a table/caption** by walking one row through the arithmetic.
- **A final freeze audit** that looks only for objective blockers and stops.

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
