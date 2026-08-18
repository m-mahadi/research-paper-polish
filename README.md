# appendix-cross-reference-audit

A Claude skill for a single, narrow, easy-to-botch technical-writing task:
making sure a research paper's main text **points to** every appendix result it
actually relies on — without dragging appendix-only material up into the page
limit.

It answers the question a supervisor or reviewer really asks — *"when the main
paper uses a result whose detail lives in an appendix, does it cite that
appendix/table right there?"* — and produces:

- a two-directional audit (appendix → main, and main → appendix),
- a clean, chat-pasteable mapping table (`✅` / `🟡` / `❌`),
- the exact minimal LaTeX fix for each missing pointer, with an added-word count,
- supervisor-ready phrasing.

## Install

Clone into your Claude skills directory:

```bash
git clone https://github.com/<you>/appendix-cross-reference-audit \
  ~/.claude/skills/appendix-cross-reference-audit
```

Claude loads it automatically when a request matches the description in
`SKILL.md` (paper prep, "check the appendix references", "did we cite every
table", cross-reference audits, and the like).

## Contents

- `SKILL.md` — the skill: the rule, what counts as "used", how to run the audit,
  and the two output formats.
- `references/audit-prompts.md` — two ready-to-paste prompts for an independent
  second-opinion audit by a fresh model.
