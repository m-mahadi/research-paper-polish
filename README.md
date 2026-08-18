# research-paper-polish

A Claude skill for the last mile of a research paper: making it read well, making
its evidence findable, and explaining what changed — **without ever altering the
science.**

It covers the four jobs that come up together when a draft is nearly done:

1. **Polishing prose** for readability and consistency while leaving experiments,
   numbers, results, and claims untouched (and describing that boundary honestly).
2. **Appendix cross-reference audit** — checking that the main text points to every
   appendix result it actually relies on, without dragging appendix-only material
   up into the page limit. Produces a chat-pasteable `✅ / 🟡 / ❌` mapping table and
   the exact minimal LaTeX fix for each missing pointer.
3. **Explaining a table or caption** by walking one concrete row through the
   arithmetic.
4. **Reporting to a supervisor** in the right tone and length.

## Install

Clone into your Claude skills directory:

```bash
git clone https://github.com/<you>/research-paper-polish \
  ~/.claude/skills/research-paper-polish
```

Claude loads it automatically when a request matches the description in
`SKILL.md` (paper polishing, "make it readable without changing the results",
appendix cross-reference audits, "what does this caption mean", supervisor
updates, and the like).

## Contents

- `SKILL.md` — the skill: prose polish, the cross-reference audit, caption
  explanation, and supervisor communication.
- `references/audit-prompts.md` — two ready-to-paste prompts for an independent
  second-opinion cross-reference audit by a fresh model.
