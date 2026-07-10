# Claude Code Skills

Personal skills for [Claude Code](https://claude.com/claude-code), distilled from real
iterative feedback on academic journal manuscripts (CACAIE, Advanced Engineering
Informatics, IEEE, Wiley).

## Skills

- **academic-paper-writing** — style and quality rules for drafting and revising
  academic journal papers: section templates, contribution/highlight discipline,
  anti-overclaim word lists, figure/table conventions, abbreviation rules,
  reference verification.
- **review-response** — drafts point-by-point response-to-reviewers letters
  (reviewresponse `.tex` and journal reviewer forms) in an established rebuttal style.

## Install

Copy the skill folders into your Claude Code skills directory:

```bash
cp -r academic-paper-writing review-response ~/.claude/skills/
```

Each skill is a single `SKILL.md` loaded on demand by Claude Code.
