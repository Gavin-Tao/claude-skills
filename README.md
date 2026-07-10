# Claude Code Skills for Academic Writing

Personal skills for [Claude Code](https://claude.com/claude-code), distilled from real,
repeated revision feedback on academic journal manuscripts (Elsevier CACAIE / Advanced
Engineering Informatics, IEEE, Wiley) and multiple real peer-review rebuttal rounds.

## Skills

- **academic-paper-writing** — style and quality rules for drafting and revising journal
  papers: section templates (Abstract → Conclusion), contribution/highlight discipline,
  claim–evidence audit, anti-overclaim word lists, figure/table/caption conventions,
  abbreviation rules, reference verification, Overleaf git workflow.
- **review-response** — point-by-point response-to-reviewers letters (reviewresponse
  `.tex` and journal reviewer forms): reply templates, comment triage, blue-edit
  letter/manuscript synchronization, blue-collection grouping, full figure/table
  reproduction rules.
- **research-paper-writing** — section-level structure and flow guidance for ML/CV-style
  papers, with abstract/introduction/conclusion templates and worked examples.
- **scientific-figure-making** — publication-ready matplotlib figures (bars, trends,
  heatmaps, multi-panel) with a consistent house style, export conventions, and a
  Windows font note.

## Install

Copy the skill folders into your Claude Code skills directory:

```bash
cp -r academic-paper-writing review-response research-paper-writing scientific-figure-making ~/.claude/skills/
```

Each skill is loaded on demand by Claude Code when the task matches its description.

## Notes

These encode one researcher's accumulated preferences — treat them as a starting point and
adapt the rules to your own venue and taste. No manuscript content, reviewer text, or
personal data is included.
