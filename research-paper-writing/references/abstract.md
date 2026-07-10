# Abstract Writing Guide

## Goal

Write a strong abstract by doing three things repeatedly:

1. Think through the abstract logic first.
2. Follow one template (Version 1/2/3 below).
3. Revise the abstract many times.

## Pre-Writing Questions (Important)

Answer these before writing:

1. What technical problem do we solve, and why is there no well-established solution? (important)
2. What is our technical contribution?
3. Why can our method work in essence?
4. What technical advantage and new insight do we provide? (important)

## Version 1: Challenge -> Contribution

Introduce the technical challenge, then use one to two sentences to present the technical contribution that solves the challenge.

### Structure

1. Task.
2. Technical challenge for previous methods.
3. One to two sentences introducing the technical contribution for solving the challenge.
4. Benefits of the technical contribution.
5. Experiment summary.

### Expert Notes

1. Discuss previous work around the technical challenge that we actually solve.
2. For the contribution sentence(s), usually mention the technical term/name only; do not explain every detailed step.
3. The technical term must be easy to understand; readers should not feel a jump.
4. This ability is very important for writing a good abstract.

Version 1 local cite:

1. `references/examples/abstract/template-a.md`

## Version 2: Challenge -> Insight -> Contribution

Introduce the technical challenge, then use one to two sentences to present the insight for solving the challenge, and then one sentence to present the technical contribution that implements this insight.

### Structure

1. Task.
2. Technical challenge for previous methods.
3. One sentence introducing the insight for solving the challenge.
4. One to two sentences introducing the technical contribution that implements the insight.
5. Benefits of technical novelty.
6. Experiment summary.

### Expert Notes

1. Discuss previous work around the technical challenge that we actually solve.
2. Introduce the insight in one clear sentence.
3. For the implementation sentence(s), usually mention the technical term/name only; do not explain every detailed step.
4. The technical term must be easy to understand; do not create a jump in reading.
5. This ability is very important for writing a good abstract.

Version 2 local cite:

1. `references/examples/abstract/template-b.md`

## Version 3: Multiple Contributions

Version 3: When there are multiple technical contributions, describe each contribution together with its technical advantage.

### Structure

1. Task.
2. If needed, one contrast sentence about prior methods.
3. Contribution sentence 1 + technical advantage.
4. Contribution sentence 2 + technical advantage.
5. Contribution sentence 3 + technical advantage.
6. Experiment summary.

### Expert Notes

1. When there are multiple technical contributions, describe each contribution together with its technical advantage.
2. The ability to express "contribution + advantage" in one sentence is very important for writing a good abstract.

Version 3 local cite:

1. `references/examples/abstract/template-c.md`

## Example Bank

1. `references/examples/abstract-examples.md`
2. `references/examples/abstract/template-a.md`
3. `references/examples/abstract/template-b.md`
4. `references/examples/abstract/template-c.md`

## Version 4: Applied / Systems Paper (Domain -> Gap -> Solution -> Evidence)

Field-tested pattern for an applied ML/RL/control/systems paper aimed at an engineering journal. It produces an abstract a skeptical reviewer can parse in one pass: what field, what is broken, what we propose, how it works, what the numbers show. Use it when the contribution is a problem reformulation plus an empirical study, not a brand-new theoretical object.

### Structure (8-10 sentences)

1. Domain hook: name the application area with 2-3 concrete deployment scenarios, then the operating constraint that motivates the work.
2. Consequence: why that constraint makes the target objective primary rather than secondary.
3. Dominant paradigm: the method family (e.g., RL) yields capable results, but optimizing the naive objective alone causes a concrete failure.
4. Established remedy and its brittleness: name the standard fix, then in one sentence state how it fails (must be retuned per setting, gives no guarantee, can even backfire). This sentence is the gap.
5. Proposal pivot: "Therefore, this paper formulates/proposes [METHOD] ...". Reframe the problem (e.g., a constraint instead of a penalty); name the technical term only.
6. Mechanism: one sentence on the core mechanism and what it removes (e.g., manual weight tuning).
7. Setup: trained end-to-end and compared against [baselines] across [N conditions] on [platform/simulator].
8. Results: open with "Experiments show that ..."; give the headline numbers and the consistency claim.
9. Significance: "These results indicate that [reframed principle] provides a [property, property] route ... that transfers across [conditions]."
10. Optional: code/repository availability line.

### Expert notes

1. The gap (sentence 4) and the proposal (sentence 5) are the load-bearing pair; keep each as one self-contained sentence.
2. Keep specific numbers in the abstract; do not move them into contribution bullets.
3. Name the method and reframed principle; do not unfold every step.

Version 4 fits the "challenge -> insight -> contribution" logic of Version 2, specialized for applied papers with a controlled empirical study.

## Prose Conventions (apply to Abstract AND Introduction)

These are the sentence-level conventions that made the rewrite read as professional, non-AI academic prose. Apply them on every pass.

1. No em-dash ("---") between sentences or as a parenthetical sandwich. Use commas, "namely", parentheses, or split into a separate sentence. Keep "--" only for numeric ranges (e.g., 14--65\%).
2. Use explicit pivots between the gap and the counter-move: "However," to introduce the limitation, "Therefore,"/"Accordingly," to introduce the proposal.
3. Lead results with "Experiments show that ..." rather than "We demonstrate ..." (the latter implies a formal proof).
4. Replace vivid or informal verbs with neutral academic ones. Examples: "buys mission range" -> "extends mission range"; "power-hungry actuation" -> "high-gain, energy-wasting actuation"; "prices the budget" -> "is updated online"; "overspends" -> "exceeds its budget"; "cutting power" -> "reducing power".
5. State the gap as one explicit, self-contained sentence; do not bury it inside a long subordinate clause.
6. Drop value-judgement adjectives used as standalone praise ("principled", "novel", "robust") unless the body backs them; prefer a mechanism word or a measured observation.

## Abstract Quality Checklist

1. Can a reader identify task, challenge, insight/contribution, and results in one pass?
2. Are all major claims supported by experiments?
3. Are technical names self-contained and readable?
4. Is there any sentence that mixes too many messages?
