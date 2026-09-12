---
name: academic-paper-writing
description: Style and quality rules for drafting, revising, or polishing academic journal papers (Elsevier, IEEE, ACM, etc.) in any field. Encodes the user's writing preferences distilled from extensive iterative revision feedback. Use whenever the user is working on a `.tex` (or similar) manuscript — especially when they ask to write/rewrite/tighten Abstract, Introduction, Related Work, Methodology, Experiments, or Conclusion, when they ask to "match the style of [a reference paper they supply]", or when they ask for revision passes on prose, claims, equations, figures, or tables. Also covers submission artefacts (cover letters, response/answer documents, highlights), reference and DOI verification, figure-vs-caption audits, and the differentiation of a manuscript from the user’s own companion submission (self-plagiarism and duplicate-publication risk).
---

# Academic Paper Writing Skill (Generic)

A consolidated style guide derived from real iterative feedback on journal manuscripts. The user prefers tight, honest, professional prose modelled on **reference paper(s) they will supply** in the workspace (commonly named `imitate.tex`, `imitate2.tex`, or similar). When in doubt, **read those reference papers and mirror their sentence patterns and paragraph structure**. Don't invent a style — imitate, don't fabricate.

---

## Top-level principles

1. **Honesty over hype.** Never overclaim. If a metric is tied, say "tied"; if your method is 2nd, don't say "unique top performer". If a result is only a `\begin{remark}`, don't call it a "theorem" or "proven result" in the contributions.
2. **Conciseness over completeness.** 4–7 sentence paragraphs. No long compound sentences with three subclauses. No filler. Don't pad to meet word counts.
3. **Verify every number against the source data.** Before committing any numerical claim, cross-check against the underlying tables or scripts. Watch out for: tied 1st places, borderline thresholds (e.g., `≥99%` when the value is 98.x), and specific class/category names.
4. **Mirror reference papers at the *structural* level — never at the prose level.** Read the reference, observe how its sections / paragraphs / sentences are organised, then write your own prose with that organisation. **Self-plagiarism is plagiarism.** If you copy whole paragraphs (even with minor word swaps) from a paper you yourself published, iThenticate will flag it and the submission will be desk-rejected for academic integrity. Before polishing any Related Work, Introduction, or Problem-Formulation paragraph that the user supplied, ask whether the same section in a reference paper (especially the user's own prior published work) uses the same reference order and example methods — if yes, rewrite from scratch using citation groups and explicit hand-off ("we refer the reader to [predecessor] and the references therein") rather than retelling the literature.
5. **Don't add content for the sake of it.** If a section is complete and serves its purpose, leave it. If a contribution can be folded into another, fold it. Length is not a virtue. **Avoid single-paragraph subsections**: if a subsection has only one paragraph + at most two figures, fold it into the adjacent subsection.
6. **No "AI tells".** Avoid em-dashes between sentences (`---`), informal mathematical arrows (`\to`) in prose, excessive parenthetical asides, and bullet-point overuse.
7. **Frame as innovation, not replacement.** When describing your method, avoid "drop-in replacement", "replaces X with Y", "swap X for Y". Use "offers an alternative to", "introduces", "proposes", "presents a new", etc.
8. **Sweep, don't patch.** When the user flags one instance of a problem ("don't use `---` here"), search the entire document and fix everywhere, not just the cited location.
9. **Hide attack-prone mechanism details outside the Methodology.** If the paper's key technical trick is a few lines of code (e.g., a stop-gradient at two interfaces, a hyperparameter widening from $(-1,1)$ to $(-3,3)$), do **not** expose those details in Abstract, Highlights, Introduction, Contributions, or Conclusion. Front-matter readers (and reviewers skimming) see only "what" and "why"; the "how" lives in Methodology where it can be properly contextualised with definitions, theorems, and cross-references. The right wording for front matter is "a backbone-preserving distillation procedure whose backbone-invariance property is established formally" — not "stop-gradient operators inserted at both the input and the target". This is not about hiding novelty; it is about not handing reviewers a one-line target before they have read your argument for it. **Sweep**: when the user flags this in one place (e.g., "this leaks the trick"), check Abstract, Highlights, Intro figure caption, Intro proposal paragraph, Related Work closing, Conclusion paragraph 1 — all of these typically need the same scrub.
10. **Unattackable claim discipline.** Every claim in Abstract / Highlights / Contributions / Conclusion must be defensible. Replace value-judgement adjectives (*interpretable*, *coherent*, *minimal*, *load-bearing*, *comprehensive*, *robust*, *seamless*) with mechanism descriptions (*L1-pruned*, *threshold-style*, *active-edge*) or measured observations (*observed across all three datasets*, *matches the symbolic readout*). Adjectives that imply provable properties (*minimal*, *optimal*) without an accompanying proof are the most attackable; demote to *compact*, *sparse*, *non-degenerate* unless the body has the theorem.

---

## Forbidden patterns / AI tells

| Pattern | Why it reads as AI | Replace with |
|---|---|---|
| `X --- [phrase] --- Y` between sentences | Em-dash overuse is a strong AI tell | Comma-bracketed phrase, parentheses, or restructure into a separate sentence |
| `$X \to Y$` in prose (e.g., `$201{,}600 \to 16{,}576$`) | Informal arrow in body text | "from $X$ to $Y$", or "$X$ reduced to $Y$" |
| "X replaces Y" (when describing your own method) | Sounds like trivial swap, not innovation | "X offers an alternative to Y" / "X introduces" / "X is a [property] counterpart to Y" |
| "drop-in replacement" | Same as above | "alternative" / "[property]-complexity counterpart" |
| Standalone "Substantial reductions in [metric]" as a contribution bullet | Efficiency is a property, not a contribution | Fold into the method-description contribution (as inherent property) AND the experimental-validation contribution (as confirmation) |
| Specific numbers (percentages, raw counts) in Introduction contribution bullets | Numbers belong in Abstract, Highlights, and Experiments | Keep contribution bullets abstract / principled |
| "X is the unique top performer on metrics A, B, C on every benchmark" (when not literally true on all dimensions) | Easy-to-falsify overclaim | Match the actual data: e.g., "highest A and B on every benchmark, highest C on three of four" |
| "We demonstrate that..." when you're just showing empirically | Sounds like a formal proof | "Experiments show that..." or "the results indicate..." |
| Repetitive use of "comprehensive", "extensive", "novel", "robust" as filler adjectives | AI overreliance on these words | Cut. Specific claims are stronger than generic adjectives. |
| Long "however..., moreover..., furthermore..." chains | Stiff connective tissue | Vary connectives; combine into single, denser sentences. |
| `frozen [backbone / teacher / model]` as an adjective | Reads as "downgraded / cheapened"; the user dislikes it | `deployed [backbone / model]`. (Keep `frozen` only as a verb for the precise technical sense "parameters are frozen during training".) |
| Internal-paper jargon in front matter (e.g., `Selector`, a module name only the predecessor paper defines) | Reader of a *new* paper does not know it | Use the generic term the reader knows (`class-similarity head`, `class-similarity logits`). |
| Marketing-style technique names (`distribution-aware grid`, `adaptive-everything`) | Invites "prove it is X" attacks | Neutral descriptive name (`widened grid range`). |
| `the present work` / `this work` as the grammatical subject of a claim | Vague self-reference; the user prefers the concrete artefact be named | `the proposed framework / module / transformation`. Sweep manuscript and (if applicable) the response letter together. |
| `theoretically grounded`, `AI-driven`, `principled` (as standalone praise) | Empty praise adjectives | Cut, or state *what* is grounded ("with theoretical backing supplied in Section~N"). |
| `xxx` / `xx` / `TODO` placeholders anywhere in submission-bound text or captions | A placeholder in a "final" draft is an instant credibility hit | Fill with the real value, or **rewrite the sentence so no placeholder is needed**. Never leave one in. |
| Paper-internal labels in titles / captions (`(Scenario~A)`, `(Config~3)`) | Ambiguous without reading the section that defines them | Describe what it means inline ("with the backbone parameters held fixed throughout"). |
| `interpretable`, `coherent`, `minimal`, `load-bearing` in a *claim* (vs. a defined term) | Value judgements that a reviewer can dispute | Mechanism word (`L1-pruned`, `active-edge`, `threshold-style`) or measured observation (`observed on all three datasets`). |
| Rhetorical subsection titles (`Why X?`, `How does Y work?`) | Reads as a blog post, not a paper | Declarative noun phrase (`Rationale for the KAN Surrogate`, `Two-Layer KAN Formulation`). |
| Subsection titles opening `What` / `How` / `Why`, even without a question mark (`What an Additive Law Recovers from a Written Specification`) | Same fault as the rhetorical form; the user flags these on sight | Name the result instead, reusing the wording of the proposition or contribution it belongs to (`Additive Projection of a Written Specification`), so title, theorem and bullet agree. |
| A leading article in a section or subsection title (`The Objective of a Learned Controller`) | Headings are bare noun phrases; across the user's portfolio not one of 35 subsection titles opens with `The`, `A` or `An` | Drop the article (`Objective of a Learned Controller`). When unsure of a heading convention, list the sibling papers' headings and follow what they actually do rather than deciding it yourself. |
| `\citet{}` author-name citations in prose ("the design of Rong et al. [19]") | The user dislikes author names in running text | Rephrase so the sentence carries the technical content and cite numerically with `\citep{}` ("disturbance observers for performance-guaranteed tracking [19]"). Author-name labels in a comparison table's method column remain acceptable. |

---

## Words to use with caution (慎用 — not banned)

These are not blanket-forbidden; each is fine in the right place. The problem is using one where it over-reaches. Before keeping one, apply four tests:
1. **Overclaim?** Does it assert more than the result supports?
2. **无中生有?** Does it state something not actually in the data / results / manuscript (a number, a Proposition/Theorem/equation that does not exist, a property not shown)?
3. **Safe / true as stated?** Is the claim literally correct, or does it rely on an unstated approximation?
4. **Re-challenge bait?** On reading it, will a reviewer re-open the same concern, or open a *new, extended* one?

If any answer is bad, reword. **Keep the word when it *lowers* the claim** (e.g., `standard` that admits a result is textbook, not novel — that defuses a novelty critique). Prefer letting the precise statement carry the strength over a loaded adjective.

**Consistency rule.** If the response letter concedes a framing ("the analysis is not meant to provide guarantees"), the manuscript must not use that word either — a leftover invites a "you said you wouldn't, yet you still do" catch. Whenever you reword a manuscript phrase, update any response-letter passage that quotes or describes it so the two stay byte-identical.

| Word / phrase | Risky when | Keep / safer |
|---|---|---|
| `guarantee(d)` | headline/positioning claim, or after the rebuttal disavowed "guarantees" | let the precise statement carry it ("ensuring … reaches a first-order stationary point"); else `result` / `bound` / `holds` |
| `provable` / `provably` | as praise, or implying real-world validity | `specific` / `established`; name the property |
| `principled` | standalone praise | cut, or name the mechanism |
| `justify / justifies` | circular or reversed causality ("property X justifies the choice that *produces* X") | state the link plainly ("choice C yields X"); drop "which justifies …" |
| `corroborate(d)` | heavier than the evidence warrants | `supported by` / `consistent with` |
| `standard` | hollow filler praise | **keep when it disclaims novelty** ("a standard regularity condition", "a standard non-convex convergence result"); cut when it adds nothing |
| `first` / `first framework` / `first to` | almost never verifiable; a prime reviewer target | reframe as "a problem-driven integration of established components"; never claim primacy |
| `deployment-oriented` / `deployment-ready(iness)` | implies real-world / streaming validation you did not run | "computationally efficient" / "computational cost"; defer real-world & streaming validation to *future work* |
| blanket robustness (`irrespective of class imbalance`, `robust to any …`) | reads stronger than what is shown | tie to the exact quantity (`…of the class imbalance ratio`) and the regime (`in expectation` / `to first order` / `at the limiting centre`) |
| exact `= 0` / strict equalities from expectation-level or linearised arguments | a skeptical reviewer checks the algebra (Jensen gap, `0/0` at the centre) | qualify: `to first order`, `→ 0`, `at the limiting centre` |
| self-undercutting caveats (`shown for illustration rather than as quantitative evidence`) | hands the reviewer a stick | make the positive point; if it is only illustrative, just show it without disavowing its value |
| `fit` / `fitted` / `fitting` as the headline verb | reads as curve-fitting rather than science (user on "Fitting one instead to the difference…": 用fitting是否low了) | `recovering` / `decoding` / `attributing`; keep `fitted` only for the mechanical description inside Methodology |
| `distillation` for a transparent surrogate | implies student-mimics-teacher compression, which is not what an additive attribution does | `attribution` / `decoding` / `readout` / `recovery` |
| `report` / `measure` / `convert` as the verb of the framework sentence | too weak for "This paper proposes X, a framework that \_\_\_" | `quantifies … in the units of` / `resolves … into` / `recovers` / `establishes` |
| `prove` in a contribution bullet | reviewers read it as a formal claim about the world; safe only for the exact statement in the proposition | `establish` / `show formally that`; state the property, not the act of proving |
| `accepted` / `may not be altered` / `has not been rejected` (about your own deployed artefact) | ambiguous and faintly defensive; reads as if it referred to peer review | name the concrete invariant instead ("the parameters of the controller are unchanged") |
| `not identified` / `non-detection` / `is not resolved` / `remains unclear` / `cannot be determined` | the user's hardest ban: 我的论文里永远不要出现"not identified"这种 … 不要显得像是ai写的一样无法确认之类的. A paper reports what it establishes | either establish the point and state it, or delete the sentence and the claim it supported |
| `we suspect` / `may be attributable to` / `it is possible that` / `this could indicate` | unfalsifiable speculation; hands the reviewer a free objection | delete. If an explanation is worth stating it needs a measurement behind it |
| `amortised`, `manufacture`, and similar rare or figurative verbs | user flagged as 生僻词 — obscures rather than elevates | plain technical verb ("each real transition supports many policy updates") |
| `unmodified` / `off-the-shelf` / `we simply apply` about your own method | destroys the first-application contribution you are claiming | describe what the deployment required; never advertise that nothing was changed |
| `because`-clauses inside a contribution bullet | a contribution states a result and its implication, not its causal justification | state the outcome and what it enables ("onboard evaluation on Jetson reaches [result], indicating real-time feasibility") |
| `Stage I` / `Stage II` as subsection titles | a procedural label where a declarative name belongs; the user asked 用stage会不会太low了 | name what the step does (`Grounding the Learned Objective in the Environment`, `Additive Recovery over Named Quantities`) and drop the numbering, which the section intro already carries |
| a plural pronoun whose antecedent is a distributive singular (`clauses that name a quantity … on which they hold`) | each clause holds over its own share, so `they` has no correct referent | make the distribution explicit (`clauses that each name a quantity … and the share of recorded operation over which the clause holds`) |
| `\newcommand{\method}{NAME}` for the method name | the user dislikes the indirection and wants the name visible in the source | write the name out at every occurrence; expand the macro and delete its definition |

---

## Canonical paper structure (observed across the user's portfolio)

The user's published papers (`imitate.tex`, `imitate2.tex`, `locomamba.tex`, `uav.tex`, `arm.tex` — spanning WSVAD, quadrupedal locomotion RL, quadrotor imitation learning, and energy-aware manipulation RL, all framed for **civil-infrastructure** venues) share one skeleton. Default to it unless the target venue dictates otherwise.

**Six top-level sections, in this order:**
1. **Introduction** — domain hook → challenges → existing methods + limits → your paradigm → gap → "this paper proposes" → contributions → organisation.
2. **Related Work** — 3–4 thematic subsections, each closing with a limitation; ends with a comparison table.
3. **Methodology** — Problem Formulation → Overall Framework → Feature/Input Encoding → Your Novel Module → Output/Head → **a formal-analysis subsection** (Theoretical Analysis / Stability Discussion / Theoretical Properties — whatever fits the method family: convergence + boundedness for RL/control, approximation + sparsity + invariance for distillation).
4. **Implementation** — a *separate* section between Methodology and Experiments (Environment / Hardware-Software Stack → Architecture/MDP Details → Training Schema). Do not merge it into Methodology or Experiments; the user keeps it standalone.
5. **Experimental Evaluation** — two acceptable organisations:
   - **RQ-driven** (e.g., SurroKAN): Evaluation Setup → Research Questions → one subsection per RQ, each closing with a plain-text "These results address RQ[N]" marker.
   - **Topic-driven** (e.g., locomamba/uav/arm): Evaluation Setup → Performance vs. Baselines → Ablation Studies → a robustness subsection (Learning Stability / Zero-shot Generalization / Sensitivity Analysis).
   Pick one; do not mix. RL/control papers tend to use topic-driven; analysis/explainability papers tend to use RQ-driven.
6. **Conclusion** — 3 tight paragraphs (recap → headline results → future work as one flowing sentence).

**Infrastructure framing.** Open paragraph 1 by tying the work to intelligent civil infrastructure / smart cities, then name the concrete operation (inspection, monitoring, anomaly detection, operation & maintenance). The contribution is always positioned as enabling a *deployable, engineering-grade* capability, not just an ML result. Close the abstract with the headline finding reframed in deployment terms ("a robust, computer-aided solution for …").

**Abstract closing line.** End the abstract with the artefact link: "A repository is hosted at \url{...}." or "Source code is available at \url{...} and a demonstration video at \url{...}." (inline `\url`, not a footnote — see the cas-dc footnote pitfall).

**Venue class dictates front matter.**
- **Elsevier `cas-dc` / `cas-sc`** (imitate, imitate2, locomamba, SurroKAN): has a `\begin{highlights}` block (≤85 chars/bullet) and `\begin{keywords}`. Abstract footnotes unreliable.
- **Wiley `WileyNJDv5`** (uav, arm): uses `\grayabstract{}`, `\authormark`, `\titlemark`, `\corres`, `\address[n]{\orgdiv...}`; **no highlights block**. Don't add Elsevier highlights to a Wiley manuscript or vice versa — match the class already in the file.

**Change-tracking note.** The user often wraps in-revision text in `\textcolor{black}{...}` (a manual change-tracking residue). When polishing, you may leave these wrappers or collapse them, but don't introduce new coloured text unless asked.

---

## Section-by-section templates

When the user provides a reference paper (e.g., `imitate.tex`), use its actual sentence structure. The templates below capture the common skeleton.

### Abstract (~200–250 words, 8–10 sentences)

```
S1: [Domain or application area] applications rely increasingly on
    [data type / task], yet [task] remains challenging under [list
    of difficulties], motivating [your approach direction].
S2: [Recent paradigm, e.g., attention-based methods] provide
    [strong property], but their effectiveness is constrained by
    [specific limitation: complexity / parameter / data].
S3: This paper proposes [METHOD-NAME] ([abbrev]), [to the best of
    our knowledge the first] [framework type] that integrates
    [X] with [Y] for [the task].
S4: [Method component 1: front-end / encoder description, 1
    sentence].
S5: [Method component 2: the novel module, 1 sentence].
S6: [Method component 3: the head / output / training, 1 sentence].
S7: Experiments on [datasets/benchmarks] demonstrate competitive
    or superior performance, achieving [metric] of [number]%,
    [number]%, ... on [datasets].
S8: Compared with the [primary baseline], the proposed framework
    [reduces / improves] [X] by [Y]%, [A] by [B]%, while
    [preserving / improving] [accuracy metric].
S9: These findings indicate that [your approach] offers an
    effective and deployment-oriented [alternative / solution]
    for [the task domain].
S10: A repository is hosted at \url{...}.
```

**Abstract discipline (enforced hard by the user).**

- **No colons anywhere in the abstract**, the `S3` proposal sentence included. The bold-title colon convention applies to contributions and highlights, not here. The same sweep often extends to colons in body prose.
- **No symbols, variable names, channel labels, or math** (`T0`, `\tau_{1/2}`, `\Delta\mu`). Editors and non-specialists read the abstract; write "the surge thruster", not "T0".
- **The proposal sentence states the research position, not the mechanics.** Shape: "This paper proposes X, a framework that quantifies [the thing] in the units of [the decision it affects] and attributes it to [named physical quantities], with [the key property] established formally." Mechanics belong in the method-component sentences after it; implementation details belong nowhere in the abstract.
- **No meta-remarks about the paper's own form.** "not a single figure", "Section 3.1 states this precisely", "The replay is offline throughout" — all cut. The abstract describes the work, never the document.
- **No hedging tails that answer a question nobody asked.** "…without altering the policy or the trajectory it produced" weakens more than it protects; if non-interference matters, state it once as a positive property.
- **An engineering-significance closer is optional.** Keep it only if it says something the results support and the preceding sentence has not.
- **Compress without losing semantics.** When the user says 精简, that is not 删减 — merge clauses and drop function words, never drop content. Diff the before/after pair and confirm every claim survived.
- **The abstract must show *how* the gap is closed, not only that it is.** A proposal sentence that names the framework and the field-first claim but never says what the construction does leaves the reader unable to tell what was actually built. State the mechanism in one clause.
- **No component enumeration.** Listing an encoder, a reward head, and an episode-continuation head is 太details and reads as 大白话. Name what the model *is* and what it *buys*; the components belong in Methodology.
- **Do not state the same property twice.** If sample efficiency is the headline number, it appears once. A second sentence restating it as an unexpected property is padding.
- **No "two properties of that result were unexpected" framing**, or any variant that editorialises the findings inside the abstract.
- **Track the research questions.** If the paper answers four RQs, the abstract's result sentences should map onto them in order. Say so if asked — the user checks (你是按照 4 个 RQ 写的摘要吗).
- **A word cap is counted, not estimated, and the count is reported.** Write the
  candidate to a file and `wc -w` it; a 341-word abstract cut to a 250-word cap
  took four measured passes, and eyeballing would have missed by twenty either
  way. The repository sentence is excluded from the cap when the user says so,
  so count without it. State the final number in the reply.
- **When a cap forces a cut, name what was dropped.** 精简 is merging clauses,
  but a hard cap sometimes costs a claim. Say which ones went and why they were
  the ones that could go — that a neighbouring sentence already carries their
  work — and offer to trade them back against something else. Silently deleting
  a claim to hit a number is what gets reverted.
- **Delivering the abstract as a standalone `.docx` for the submission system**:
  take it from the `.tex` verbatim, strip only the repository sentence, unwrap
  the source line breaks, render `--` as an en dash, and assert that no
  backslash or brace survives. Do not re-edit the wording on the way out; the
  file must match the manuscript word for word.

**Title.** Name the paradigm term that *is* the contribution (`world model`, `imagination`, `memory horizon`) — if the reader cannot see the claim in the title, it is under-titled. Preposition choice (`via` / `through` / `from`) is worth one deliberate pass, not more.

**Title discipline.** No question-form titles. No titles opening with "What"/"How"/"Why". No full-sentence titles. No process adjectives such as `Deployed`. A two-part `Main Claim: Subtitle` is fine, as is a bare noun phrase; when in doubt, name the *object of study* and the *thing you recover from it*.

**Naming the method.** The user will ask where the acronym comes from, so
settle it before the draft circulates.

- **The name must be traceable to the title's key phrase, but need not be a
  strict initialism.** The portfolio convention is a loose letter-group
  mnemonic: `CLARO` from **C**ontrol-**LA**w **R**ead**O**ut, `ROVER` from
  **R**ealised-**O**bjective **VER**ification. A name whose expansion uses
  words that appear nowhere in the title reads as arbitrary and will be
  queried.
- **Never expand the acronym in the title, and never bold its letters there.**
  The companion never expands its name anywhere in the manuscript. Bolding is
  worse than useless: an Elsevier title is already set in a heavy weight so
  bold-within-bold does not render distinctly, copy editors strip markup from
  titles, and spelling the mapping out for the reader reads as trying too hard.
  Expand it once, as an apposition, at first use in the Introduction.
- **Check the name against the machine-learning literature before committing.**
  `CORAL` was rejected at draft stage because it collides with CORrelation
  ALignment, a known domain-adaptation method. A collision in an adjacent field
  is not fatal, but it costs the reader a beat and is free to avoid.
- **A name apt to the domain is worth reaching for.** `ROVER` for a study of an
  ROV-class vehicle earns recall at no cost to accuracy.
- **Check the expansion's strongest word against the caution table.** `ROVER`
  survives on `verification` only because verification is the systems
  engineering term of art for checking a built artefact against its
  specification, which is exactly what the evaluation does. A name that
  smuggles in `guaranteed`, `optimal` or `provable` would not.

**Prefer a finding-led title to a mechanism-led one.** Given a choice between
naming what the paper discovered and naming how it works, the discovery wins.
Worked pair, both for the same manuscript:

> ROVER: Recovering the Realised Objective of a World-Model Controller for
> Underwater Vehicles

against

> CORAL: Control-Objective Recovery via Additive Laws for World-Model
> Underwater Vehicle Controllers

The second traces its acronym cleanly and loses on everything else. It states
the mechanism rather than the claim, it drops `Realised`, which is the word
carrying the paper's whole tension between the specified and the realised
objective, and it ends in a four-noun pile-up. Fix the acronym to fit the
better title; never degrade the title to fit the acronym.

### Highlights (Elsevier: 3–5 items, **each ≤ 85 characters including spaces**)

The 85-character cap is a hard Elsevier requirement, not a guideline. Each highlight is **one short declarative sentence** — not a bold-title-plus-elaboration (that format blows past 85 chars). Verify the count with a script (`awk '{print length, $0}'`, treating LaTeX `--` as one visual char) before committing.

A 5-bullet pattern that mirrors the Abstract → Contributions arc:
1. `[METHOD] distils a deployed [domain] detector into a [student] surrogate.`  *(framework, ~80 chars)*
2. `A closed-form symbolic specification of the decision logic is read out post-hoc.` *(output)*
3. `Structural, semantic, symbolic, and causal extraction yields four artefacts.` *(protocol)*
4. `Backbone invariance, universal approximation, sparsity bound, SGD convergence.` *(theory)*
5. `Validated on [DS1], [DS2], and [DS3] with [headline probe].` *(experiments)*

Rules: no bold lead-ins (they cost characters); no mechanism leak (highlight #4 lists property *names*, never "stop-gradient at both interfaces"); abbreviations are fine for brevity (`CF`, `SGD`) since highlights are skim text. If a 3-item bold-title format is preferred and fits under 85 chars, that is also acceptable — but the count is the binding constraint.

### Introduction (5 paragraphs + Figure 1 + "this paper proposes" + contributions + organization)

Each paragraph has a specific function. Mirror the sentence patterns of the reference paper.

**¶1** — Domain context + task importance.
> "With the rapid development of [domain], [task / data] has become [foundational / important] for [purposes]~\cite{}, covering [list of applications]~\cite{}. Consequently, [task] is not merely a [narrow framing], but a [broader engineering / scientific] requirement for [systemic goal]~\cite{}."

**¶2** — Problem-specific challenges.
> "Despite its importance, [task] remains a challenging problem. In real-world [deployments / acquisitions], [observation 1]~\cite{}. Moreover, [observation 2]~\cite{}. In addition to detecting/identifying [X], [systems] often require [Y]~\cite{}."

**¶3** — Existing methods + their limitations.
> "Existing methods have attempted to address these challenges. Early approaches primarily [do X]~\cite{} and are effective at [scenario]. However, [limitation]. [Subsequent paradigm] introduced [Y]~\cite{}, finding widespread use in [related applications]~\cite{}. Nevertheless, [limitation]."

**¶4** — Recent dominant paradigm + its limits.
> "More recently, [paradigm, e.g., Transformer-based methods] has been introduced, leveraging [its property]~\cite{}. While these models significantly improve [Z], their effectiveness is constrained by [specific limitation]. [Concrete problem: quadratic, memory, etc.]. As a result, [paradigm] is difficult to deploy on [resource-constrained X]~\cite{}."

**¶5** — Your paradigm as solution + the specific gap you fill.
> "In contrast, [your-paradigm] provides a principled [...] paradigm that [does Y]. By [property], [paradigm-based] formulations naturally support [...] with [your-advantage]. [Vision adaptations / Recent efforts] include [list of cites]. However, all existing [field] [paradigm] works address only [restricted setting]; the integration of [paradigm] with [the key mechanism that proved effective in the dominant baseline] remains unexplored, and a naive [combination] does not account for [asymmetric structure / specific challenge]."

**Figure 1** — concise caption (1–3 sentences) describing the framework.

**"This paper proposes" paragraph** (4–5 sentences, **no specific numbers**):
> "Therefore, this paper proposes [METHOD-NAME] ([abbrev]), [a / the first] [framework type] that integrates [X] with [Y] for [task], as illustrated in Figure~\ref{fig:framework}. [Component A description]. To overcome [problem], the proposed [novel module] [does what] at [your-advantage]. [Final component / head] produces [output], with the entire framework trained end-to-end."

**Contributions (3–4 items, abstract claims, NO specific numbers in contribution bullets):**

1. **First [paradigm]-based [framework type] for [task]** — position claim.
2. **[Module name].** A novel [module] is designed to [purpose] with [your-advantage]. Compared with [baseline-paradigm], this design provides substantially improved [scalability / efficiency / robustness].
3. **Theoretical analysis** (if applicable). Formal characterisations of [N] structural properties of [module]: [list each proposition, e.g., complexity bound, propagation identity, parameter advantage].
4. **Comprehensive empirical validation.** Experiments on [N] benchmarks against [classes of baselines]. The results demonstrate competitive or superior performance; sensitivity analyses confirm that the [efficiency / robustness] is intrinsic to [your formulation] rather than the artefact of a particular configuration.

See **Contributions writing rules** below for the discipline these bullets must follow.

**Paper organization** — 1 short paragraph listing sections.

### Writing the gap: make it "high-level" without going un-academic

When the user says the gap "isn't high-level", "lacks packaging", "不够高大上", or "不学术 / 说不上来哪里不对", these three escalations are the common ways the gap goes wrong — they read as *less* academic, not more:

| Wrong way to "elevate" | Why it reads as un-academic |
|---|---|
| **Slogan dichotomies** (`the field treats a specification problem as an incentive problem`, `X is mistaken for Y`) | Catchy oppositions read as blog prose, not journal prose. (Observed: the user called this version "不学术".) |
| **Mechanism / solution-method detail** (`penalty method vs constrained optimization`, `the weight is a fixed dual coefficient`) | That is *how the method works*; inside the gap it reads as premature technical detail, not as a gap. (Observed: the user called this "太 details, 不 high-level".) |
| **Borrowed trendy vocabulary** from an adjacent field (e.g. AI-safety `objective misspecification` / `reward hacking` in a control paper) | Reads as grafted-on and chasing fashion. |

**Conceptual property-axis framings are GOOD, not wrong.** Naming a crisp high-level property the existing approach lacks — e.g. an `open-loop vs closed-loop` (control) view, a `specifiability` angle — is often exactly the altitude the user wants for *thinking about* the gap. (Observed: the user explicitly preferred the open-loop/closed-loop and interpretability framings over the mechanism-detail version.) Two cautions: (1) keep it to one or two such axes, not a laundry list of `-ility` nouns (a long list tips into marketing); (2) in the **prose** they must be grounded, not left as bare value adjectives — write the mechanism or the measured observation (`specified in watts`, `adjusted online by feedback`), never bare `interpretable` / `robust` (see caution table). Use the axis to *find* the point; use the reference-paper register below to *write* it.

**"Academic high-level" is NOT "abstract / grand / aphoristic".** It is **precise + measured + the central quantity's status elevated + plain literature-characterisation register**. The height comes from *what the subject is*, stated soberly, not from clever framing.

**Reliable method (imitate the reference, per top-level principle 4):**
1. Open the user's closest reference paper (same problem class) and read its actual gap sentences. That register is already proven; mirror it. Do not invent a new way to package the gap.
2. **Elevate the status of the central quantity** in one plain sentence: state what it *really is* in the problem (e.g. "a hard operating budget that bounds mission feasibility", "a fundamental design factor", "a first-class constraint"), instead of naming an abstract property of the method.
3. **State the literature's mishandling plainly**, as a measured observation: "[field] methods typically treat [quantity] as [a secondary objective / a heuristic penalty / ...] rather than [the correct first-class treatment]."
4. Close with **one** plain consequence. No rhetorical flourish, no `---`, no dramatic verbs (`demote`, `collapse`, `conflate`).

**Worked register (from `arm.tex`, energy-aware constrained RL):**
> "existing methods rarely account for energy consumption **as a fundamental design factor** …"
> "Energy treated as a secondary objective. Actuation energy is commonly **incorporated heuristically as a reward penalty rather than explicitly modelled as a constraint**."

The entire "height" is in promoting *energy* from "a reward term" to "a fundamental design factor / an explicit constraint": the grammatical **subject is elevated, the verbs stay flat**. No `-ility` list, no slogan, no mechanism.

**Honesty fixes specific to the gap:**
- Do not sell the gap with `interpretable` or `guarantee(d)` (both in the caution table). A soft / Lagrangian constraint is satisfied in expectation; write "specified in advance" / "a stated budget", not "guaranteed".
- Do not promise `transfer` / `robustness` as a property unless it is *observed in the results*; phrase it as an observation, not a headline property.

**Diagnostic for "說不上來 / can't say why it's off":** the un-academic feeling is almost always *register* (slogan / mechanism / trendy word / property-list), not *content*. The underlying idea is usually right; restate it in the sober status-elevation register of the reference paper rather than searching for a new abstraction.

### The central question (Introduction closer)

Some authors like to end the Introduction gap discussion with a single **italic (`\emph{...}`) "central question"** that packages the paper's thesis, immediately answered by the "this paper proposes" paragraph. Pattern: a lead-in (`Together, these gaps raise the central question we address:`) then one `\emph{}` question. Construction that works (schematically: *Can [central quantity] be transformed from [the literature's weak treatment] into [your first-class treatment], whose [property A], [property B], and [property C], all without sacrificing [the core task(s)]?*):
- **Transformation arc**, not static description: `transformed from [a secondary reward term] into [an explicit constraint]` beats `governed by [an explicit constraint]`. The `from X into Y` folds the gap and the solution direction into one clause.
- **Parallel triplet** of the mechanism's properties as matched participles (`whose budget is generated …, tightened …, and never calibrated in advance`). Keep them grammatically parallel — all past-participle passive; a non-parallel member (`no need to be calibrated`) breaks the rhythm, so prefer `never calibrated`.
- **Weighted close**: end on the payoff at the sentence's heaviest position (`all without sacrificing [task A] or [task B]?` — the `all without` echoes the reference register). Cover the *whole* task, not half of it: if the system does two things (e.g. tracking *and* obstacle avoidance), name both. Under negation use `or` (`without sacrificing A or B` = neither), never `and/or`.
- Capitalize the first word after the colon (`Can …`).

**Accuracy discipline for the question (the part reviewers scrutinize):** every clause's driver must be literally correct.
- **Attribute each clause to its true driver.** If a quantity's *value* is derived from one signal but its *tightening* is gated by another, don't collapse both into one wrong source noun — attribute each to its real driver, or use a neutral umbrella true of both (e.g. `from the system's own recent behaviour`). Also avoid a source noun that duplicates a later clause (saying a budget follows "competence" *and* is "tightened as competence grows" is circular).
- **Avoid over-precise and vague nouns.** A source noun that restates the output (`energy budget generated from recent energy consumption`) reads circular; a placeholder (`status`, `performance`) reads vague. Pick the one true, non-redundant noun.
- **Watch absolute phrasings.** `without any budget specified in advance` is false-sounding if *some* dimensionless schedule is still set — scope it to what is actually eliminated (`without calibrating an absolute budget in advance`).
- **Don't smuggle in claims the paper can't back** (physical units when the quantity is normalized; cross-domain generality from a single-domain study).

### Contributions writing rules

Contributions are the highest-density text in the paper. Every word must be load-bearing. The user enforces strict discipline.

**Each bullet = one substantive claim.** The bullet is the bolded title; the body is one to three sentences that make the claim concrete. Do not chain unrelated claims with "moreover", "in addition", "furthermore" — split into separate bullets or trim.

**No filler closing phrases.** The bullet should stop at the first-claim or at a substantive enabling clause. Forbidden filler:

| Forbidden phrasing | Why it's filler |
|---|---|
| "bridging the gap between A and B" | Tautological once you've claimed "first" — the first-claim already implies a gap |
| "shedding light on" / "providing insights into" | Vague, sounds promotional |
| "paving the way for [future work]" | Forward-looking handwave, not a present contribution |
| "demonstrating the potential of" | Hedges the claim; if it's a contribution, claim it |
| "to the benefit of [broad community]" | Audience-flattering filler |
| "advancing the state of the art" | Generic; if true, the experiments show it — don't repeat in claim |

**Allowed closing clauses** (substantive, not filler):
- "enabling [concrete capability that the rest of the paper demonstrates]"
- "Compared with [baseline-paradigm], this design provides [specific advantage that's measured later]"
- "with [a property that's actually proven, e.g., linear time and memory complexity]"

**No specific numbers in contribution bullets.** Numbers (91.8%, 16,576, etc.) belong in Abstract, Highlights, and Experiments. Contribution bullets are principled claims — "substantially reduces parameter count" is correct; "reduces parameter count by 91.8%" is wrong placement.

**No "Substantial reductions in [efficiency metric]" as its own bullet.** Efficiency is a property of the method, not a contribution. Fold into:
- the method-description contribution (as inherent property of the design)
- the experimental-validation contribution (as confirmation in experiments)

**Theoretical claims must match the body.** If you claim "Theoretical analysis: complexity bound, propagation identity, and parameter advantage", confirm each is a `\begin{proposition}` with a proof in the Methodology. A `\begin{remark}` is not a "result" — don't list it.

**The last bullet (empirical validation) must not over-reach.** Common overclaim patterns to avoid in the closing experimental-validation bullet:

| Overclaim | Why it's unsafe | Safer phrasing |
|---|---|---|
| "the observed efficiency is intrinsic to the [paradigm] formulation rather than the artefact of a particular configuration" | Single-paper ablations show only that small configs work well; they cannot prove a family-level causal property. | "ablation studies corroborate that the efficiency gains persist across the explored configurations" |
| "reductions in parameter count and computational complexity" | "Computational complexity" is fuzzy and easy to challenge. | List the specific measured dimensions: "encoder parameter count, total model size, and FLOPs" (whatever you actually measured) |
| "ablations confirm that [accuracy gains stem from the broader architectural family]" | Same family-level overreach as above. | "ablations corroborate each of the [N specific contributions named in this paper]" (imitate.tex pattern) |

**Closing pattern (safe, matches `imitate2.tex`)**: end the last bullet with "…validating the effectiveness and deployment readiness of [METHOD] for [the target deployment domain]." This is a domain-grounded, hedged claim — much harder for a reviewer to push back on than a family-level causal claim.

**Match the reference paper's contribution patterns.** Read the reference's contributions itemize and mirror its sentence shapes. Common pattern:
- Bullet 1: "This paper presents [METHOD], to the best of our knowledge the first framework to [do X] for [task], [substantive enabling clause]."
- Bullet 2: "[Module / mechanism] is introduced through [design], [substantive description]. Compared with [baseline], this design provides [advantage]."
- Bullet 3 (if theoretical): "Theoretical analysis establishes [list of properties]."
- Bullet last: "Extensive experiments on [benchmarks] demonstrate [claim]. Comprehensive efficiency evaluation further confirms [efficiency property]."

**Sentence-level bullet style.** Inside a bullet body: no "In contrast to existing ..." openers — comparative framing belongs in the Related-Work gap sentence, not in the contribution (Observed: the user struck this opener while otherwise approving the bullet set). No mid-sentence colons — the bold-title colon is the only colon; write two plain declarative sentences instead: "X is proposed to ... . The [mechanism] ..., so that ...". No value adjectives (*flexible*, *robust*, *seamless*) — when a bullet feels weak, strengthen it by sharpening the concrete mechanism contrast (e.g., "an operating budget ... instead of a reward weight whose behavioural effect must be re-tuned for every task"), never by adding an adjective.

**Claim–evidence audit.** Separate *constructive* claims (properties true by construction of the method, e.g., "no budget needs to be specified or calibrated in advance") from *comparative* claims (e.g., "prevents premature over-constraint", "outperforms a fixed threshold"). A comparative claim requires a matching experiment or ablation in the evaluation section; if that ablation does not exist, either run it or demote the claim to its constructive core before the draft leaves the house. Failure-mode statements about prior methods are Introduction material supported by citations — never phrase them as in-house experimental findings when no in-house comparison exists.

**Audit checklist before submitting**:
- [ ] Each bullet makes exactly one substantive claim.
- [ ] No bullet ends with "bridging the gap", "shedding light on", "paving the way", or similar filler.
- [ ] No bullet contains specific numerical values.
- [ ] No bullet duplicates a claim made in another bullet.
- [ ] Each theoretical claim corresponds to a `\begin{proposition}` (not `\begin{remark}`) in the body.
- [ ] Each "first-claim" is hedged with "to the best of our knowledge".
- [ ] No bullet opens with "In contrast to ..."; no mid-sentence colon inside a bullet body.
- [ ] Every comparative claim maps to an experiment or ablation that actually exists; construction-level claims are phrased as such.
- [ ] No bullet exposes implementation detail that invites a question (layer count, "a single layer", episode counts, "no gradient reaches the policy", optimiser tricks). These live in Implementation.
- [ ] Bullets are 言简意赅 — a short bold lead-in plus one or two sentences. A bullet past ~65 words is either two bullets or has filler.
- [ ] No two bullets state the same finding at different granularity; a method bullet and a results bullet describing one property must be merged or re-scoped.
- [ ] The count is not fixed at three. Split a bloated bullet rather than compressing two claims into one sentence.
- [ ] Every bullet is packaged in academic register — it says what gap is closed and what that enables, not a half-sentence description of what was done.
- [ ] Each bullet names the specific table or figure that supports it. The user asks this directly (这四条 contributions 都有数据支撑吗？分别是哪个数据制成的); be able to answer before the draft is shown.
- [ ] No bullet mentions a design property the paper does not study (a fifteen-fold thrust ratio, a parameter split, a dataset replay) merely because it is true.
- [ ] A first-application claim is *packaged*, never blunt. "The first world-model agent trained for underwater vehicle control" is a claim; "we apply DreamerV3 to MarineGym" is a description of work. And never pair it with a note that the algorithm was left unmodified.

### Related Work (typically 4 subsections; each ends with a gap/limitation)

Pattern (each subsection):
- 2–3 paragraphs
- Overview of the topic
- Key works cited chronologically/thematically
- **Closing critique/limitation** that motivates moving to the next subsection

Final subsection (your-paradigm-in-your-field) ends with the **specific gap** that motivates your work:
> "However, all existing [paradigm-in-field] works exclusively address [restricted setting]. The integration of [paradigm] with [the key mechanism that proved effective in the dominant baseline] has not been studied. In particular, [specific incompatibility]. Filling this gap is the central motivation of [your module / method], described in the next section."

**Add a comparison table at the end of Related Work** with ✓/✗ across the key dimensions that define your novelty. Your method should be the only row scoring all ✓ — but achieve this through *honest column design*, not column engineering:

- **No "engineered" columns.** A column where only your method scores ✓ (and every other row is ✗) reads to reviewers as a flag added solely to make you unique, even when factually correct. Prefer columns where the ✓/✗ split is balanced (e.g., 6 ✓ / 9 ✗), so your ✓ is *shared* with some baselines on each individual axis while you are the only row that collects all of them.
- **Group rows into families** (`Gradient-based saliency`, `Perturbation-based`, `Surrogate distillation`, …) with `\multicolumn{N}{l}{\textit{family}}` header rows. The grouping encodes "what kind of method" structurally, so you don't need a separate "method type" column.
- **Include the strongest competing families, not just weak ones.** If a reviewer's favourite method is missing, the table looks cherry-picked. Cover the landscape (≥10–13 methods across ≥4 families is typical).
- **A domain/application column (e.g., `WSVAD-evaluated`) is acceptable** *if* multiple baseline rows also score ✓ on it (the domain's own methods), so it is not engineered for you alone.
- **Do not add a "Theoretical analysis" column** just to mark yourself ✓ — theory is better placed in Contributions / a dedicated §, and such a column dilutes (several established explainers also have theory).
- **Self-contained caption.** Define every column meaning inline in the caption (`\textbf{Post-hoc}: applies after training.` …) plus the symbol legend (`\checkmark / $\circ$ / $\times$ / -- denote …`). Never use cryptic header abbreviations (`PH/Gl/Sy/MA/Ca`) that force the reader to hunt for a key.
- Cite each row from the bib, including the dataset/backbone rows.

### Methodology

- Subsections: Problem Formulation → Overall Framework → Feature Extraction & Tokenization → [Your Novel Module] → Output Head → Theoretical Analysis (if applicable).
- **Notation block** at start: bold lowercase = vectors, bold uppercase = matrices/tensors, calligraphic = sets. State this once and stick to it.
- **Symbols must match the figure exactly.** Don't introduce `L` in prose if the figure uses `K`.
- **One equation per `\begin{equation}` block.** Single line if it fits the column; split into two lines with `&` alignment only when a line genuinely overflows. Don't combine unrelated equations into a single `\begin{aligned}` block.
- **Promote long inline math to display.** If an inline `$...$` expression contains a `\sum`, `\prod`, large fraction, or anything that would render taller than one text line, convert to a display equation (`\[...\]` if unreferenced, `\begin{equation}` if it needs a label). Common offender: an unrolled recurrence in a proof body. Use `\Bigl(...\Bigr)` to match parenthesis heights to the big operator.
- **Pick terminology that reads naturally at the default config.** If your default is the smallest setting (e.g., `K=1`, depth 1, one block), use a noun phrase that doesn't sound oxymoronic at that value — "depth 1" is grammatically valid but reads as no-stacking; "1 block" / "single block" is clearer. Match the convention of the surrounding subfield (e.g., Mamba papers say "Mamba layers" not "Mamba depth"). Sweep every occurrence in prose, table column headers, figure captions, algorithm I/O lists, and hyperparameter tables when you change a term.
- Use `\begin{proposition}` for claims with proofs; `\begin{remark}` for informal observations. **Do not list a `\begin{remark}` as a "result" or "theorem" in the contributions.**
- **Algorithms cross-reference equations, never repeat them.** An `\begin{algorithm}` step should say `$\mathcal{L}_{\text{total}} \gets$ Equation~\eqref{eq:ltotal}`, not re-typeset the loss. Inputs reference the interface equation; the mechanism step references the subsection that defines it (`apply stop-gradient at both interfaces (Section~\ref{sec:dual_isolation})`). This keeps the algorithm short and avoids two sources of truth that can drift apart.
- **Pair a training algorithm with an inference/extraction algorithm** when the method has both a fitting phase and a deployment/readout phase. The inference algorithm can be ~10 lines, almost entirely cross-references to earlier equations and to the protocol table — its value is giving the reader one procedural view of the whole pipeline, not introducing new content.
- **Algorithm captions describe, don't label.** `SurroKAN distillation training with the backbone parameters held fixed throughout` beats `SurroKAN training (Scenario A)` — the latter is meaningless to anyone who has not read the Scenario-A definition.
- **Algorithm layout (the user's required format).** `algorithm` + `algpseudocode`, `\begin{algorithmic}[1]`. Give both `\Require` (inputs) and `\Ensure` (outputs). Group the body into phases with **unnumbered bold `//` section headers**: `\Statex \quad \textbf{// Phase name}` (`\quad\quad` one level deeper inside an `\If`) — these carry no line number and no `▷` marker. Put the equation reference on **each computational line**, right-aligned: end the `\State` with `\Comment{Eq.~\eqref{eq:x}}` (or `\Comment{Eqs.~\eqref{eq:x},\,\eqref{eq:y}}`) pointing to that line's exact equation — one equation per line, not a block-level range. Use `\label{alg:line:xxx}` on lines the prose must cite, and `\Comment{Algorithm~\ref{...}}` to call a sub-algorithm. Long/main algorithms use `\begin{algorithm*}[t]` (full width, spans both columns in a two-column layout); short auxiliary ones stay single-column `\begin{algorithm}[t]`. Add a `\label` to any equation a line needs to cite. Do **not** use standalone `\Comment{\textit{Phase --- \eqref{}--\eqref{}}}` italic `▷` lines with block-level equation ranges — the per-line right-aligned form above is preferred.
- **Write the actual math inline, not prose descriptions (the "make it look rigorous / 高大上" preference).** Each computational step is a formula, and the inline formulas linked to the Method-section equations are what carry the sophistication: (i) parameter updates as explicit gradient descent — `$\boldsymbol{w}\gets\boldsymbol{w}-\eta\nabla_{\boldsymbol{w}}\mathcal{L}(\cdot)$` with `\Comment{Eq.~(loss)}`, not "update the critic"; (ii) the environment/plant step as the actual state propagation — `$(\boldsymbol{\eta}_{t+1},\boldsymbol{\nu}_{t+1})\gets\mathrm{RK4}(\dots)$` referencing the dynamics equations, so the loop links to the problem's physical model; (iii) composed operators — `$\mathrm{sat}\!\circ\!\mathrm{rate}(\cdot)$` — instead of "rate-limited, saturated"; (iv) gates/conditions as explicit inequalities. Ensure every symbol used (learning rates `$\eta$`, param vectors `$\boldsymbol{w}$`) is defined in the text or the hyperparameter table. Then cross-reference key `\label{alg:line:xxx}` lines from the prose ("the plant transition (line~\ref{alg:line:plant}) integrates the Section~N dynamics; the dual ascent realises the scheme analysed in Section~M") to weave the algorithm into the Method/Theory. This deliberately overrides the earlier "algorithms cross-reference, never repeat" bullet for the user's algorithm style. A prose-only algorithm in `algorithm*` looks too wide/sparse; formula-filled steps justify the full width.

- **Methodology explains the method; the parameter table holds the parameters.** A method section that is mostly hyperparameters reads 太单薄 — the user's complaint was 没怎么介绍 methods. Move every numeric setting to a settings table and spend the section on the construction, the objective, and why each part is there. This holds even when the algorithm is adopted rather than invented: what the deployment required *is* the method content.

### Experimental Evaluation (organised around Research Questions)

- 3–4 RQs that map cleanly to the data you have.
- Recommended general pattern:
  - **RQ1**: Primary accuracy/quality claim (vs. all baselines)
  - **RQ2**: Efficiency / cost claim (vs. primary baseline + Pareto)
  - **RQ3, RQ4**: Hyperparameter sensitivity / robustness ablations
- Each RQ subsection closes with a brief, **plain-text** marker that the RQ has been answered, followed by a one-sentence summary. Do **not** wrap the marker in `\textbf{}` — it reads as plain prose, like the reference papers do.
  - Vary the wording across RQs (don't repeat the same sentence-template four times in a row). Acceptable forms:
    - "These results answer RQ[N]. [Summary]." (most common)
    - Mid-sentence embedded: "..., answering RQ[N]: [summary]."
    - Sentence-end embedded: "[Conclusion], answering RQ[N]."
  - Avoid filler tails like "in the affirmative" / "in full" / "conclusively". The marker should be terse — `answer RQ[N]` is enough on its own.
- **Datasets go in Implementation / Datasets, NOT in Experiments.** Dataset 4-panel visualizations belong to the Datasets subsection.
- Qualitative results (classification maps, attention maps, generation samples) belong in RQ1 (the accuracy/quality RQ).
- For accuracy RQ: per-class / per-category tables + radar / heatmap / bar visualizations across baselines.
- For efficiency RQ: Pareto plot + efficiency table (your method vs. primary baseline, side by side).

**Two structural elements are easy to omit when drafting section by section,
and the user checks for both.** The Introduction needs the italic central
question closing its gap discussion, immediately answered by the "this paper
proposes" paragraph. The Experiments section needs the research questions
stated explicitly as an itemised list before the per-RQ subsections, not only
implied by the subsection titles and the closing markers. Writing the RQ
subsections first makes it easy to believe both are already there.

**Section-intro paragraph (between `\section` and the first `\subsection`) — portfolio-dependent, so check before writing one.** Some of the user's papers open every top-level section with a short orienting paragraph; the underwater world-model family opens *none* of them, going straight from `\section` to `\subsection` in Related Work, Methodology, Implementation and Experiments alike. Four such paragraphs written into a manuscript of that family were all struck. Count the siblings first, extracting the words between each `\section{}` and its first `\subsection{}` in the reference papers. When deleting one, keep any sentence that carries content rather than framing — a notation block belongs at the head of Problem Formulation, and a held-out-data statement at the head of Evaluation Setup. For Experiments it states the scenarios and previews the RQ arc in one sentence: "This section ... organised around four research questions that examine, in turn, [RQ1 topic], [RQ2 topic], [RQ3 topic], and [RQ4 topic]." (matches the SST-BiMambaAD register). Do the same for Methodology and Implementation.

**Evaluation Setup — metrics as equations.** Where a metric has a formula, write it as a *separate numbered display equation*, not inline prose — RMSE, cumulative/total energy, energy-per-metre each get their own `\begin{equation}`. This looks rigorous and lets the text refer to `\eqref{}`. Two discipline points:
- **Distinguish the evaluation metric from the training objective.** If training optimizes a *discounted* cost $J_c$ but you report an *undiscounted* episode total $E_{\text{tot}}=\sum_t c_t$, say so explicitly ("Unlike the discounted cost $J_c$ optimized during training, $E_{\text{tot}}$ is the undiscounted episode total"). Readers conflate them otherwise.
- **Don't invent units the data doesn't carry.** If the cost is normalized/dimensionless, report energy-per-metre as a ratio, not "in joules/watts".

**Baselines — concise `\item` list, neutral phrasing, `(Ours)` row.** Prefer baselines as an `itemize`, one line each (`\item \textbf{[Method]} [one-clause description of what it does].`). Rules:
- **No belittling verbs.** `ignoring [X]`, `folding [X] into the reward`, `naively`, `merely` make the baseline look *deliberately* crippled (user reaction: "显得故意让他差" — looks like you rigged it to lose). State neutrally what each method *does*, e.g. `\item \textbf{[Baseline]} adds a fixed-weight [X] penalty to the reward.`
- **No inline symbol formulas in the list.** Keep the objective math in the Formulation section and refer to it (`as formalized in Section~\ref{sec:formulation}`); the baseline list is prose descriptions, not equations.
- **Include the proposed method as the last item with `(Ours)`** (`\item \textbf{[Method] (Ours)} [one-clause description].`) so the contrast set is complete on the page.
- **State the shared protocol once.** The "same architecture, same schedule, same per-episode conditions, differing only in [the one axis under study]" statement belongs in the Training/Implementation subsection (where the protocol is defined), *not* duplicated in the Baselines list. From the list, one clause ("all sharing the same architecture and training schema and differing only in …") plus a pointer is enough.

**Seeds — don't commit to a count you don't want scrutinized.** If evaluation used a handful of seeds and you are *not* making a training-robustness claim, write "across seeds" / "over random seeds" and do not print a specific number (a stated "5 seeds" invites a robustness question the paper isn't answering). State a count only when the count itself is the evidence (e.g. a variance/CI claim).

### Conclusion (3 paragraphs, ~30 lines total)

¶1: Recap what was proposed and the principled reason it works (no specific numbers).
¶2: Headline experimental results with specific numbers.
¶3: Future work (3 concrete directions, brief).

**Length discipline.** Conclusion should be ~30 lines, matching the reference paper's tightness. Common bloat to cut:
- **Per-dataset metric enumerations** (e.g., "89.66\%, 98.19\%, 89.70\%, 89.22\% on …"). Headline reductions (91.8\%) and the largest per-metric gain (+4.70\%, +6.20\%) are enough — drop the dataset-by-dataset OA list.
- **Repeated "structurally inherent" / "intrinsic property" framing.** State it once, in the strongest place (¶2 or the Discussion). Don't restate in RQ closings AND Conclusion AND a standalone paragraph.
- **Double-enumeration in future work** (e.g., "First, …. Second, …. Future work will explore (i) X, (ii) Y, (iii) Z."). Use **one flat list, expressed as flowing prose**, like the reference papers do: "Future work will explore X, Y, and Z." A single sentence with three coordinated directions is enough.
- **"Wide configuration window for practitioners"** or other practitioner-flattering filler. Cut.

---

## Data accuracy checklist (run before any quantitative claim)

Before writing or committing any quantitative claim, verify:

- [ ] OA/AA/AUC/F1/etc. values match the source table exactly (down to decimals).
- [ ] "Unique top performer" claims — confirm no other method matches or ties.
- [ ] "Up to X% improvement" — verify which dataset/setting gives this maximum.
- [ ] "$\geq N\%$ on $K$ classes" — count carefully; check borderline cases (e.g., 96–98% don't count for $\geq 99\%$).
- [ ] Per-class margins (e.g., "+17.12% on Highway") — confirm class index AND class name.
- [ ] Specific class names match the class-distribution table definitions.
- [ ] Theoretical claims in contributions match what is actually proven (proposition, not remark).
- [ ] All `\cite{key}` keys exist in the bib file.
- [ ] All `\ref{label}` labels exist (sweep for stale labels after section renames).
- [ ] Numbers in Abstract / Highlights / Intro / Conclusion are all consistent with the canonical source (the main efficiency or per-class table).

---

## Figures & tables

### Figures

- **Placement specifier is a user preference — confirm it.** Two regimes seen in practice: (a) strip all specifiers and let LaTeX place naturally; (b) put `[t]` on *every* `figure`/`figure*`/`table`/`table*` so floats consistently sit at the top of a column. They are mutually exclusive. When the user asks for one, sweep the **whole** document so all floats match (one `\begin{figure*}[t]` among 30 bare ones looks like an oversight). Apply the same specifier to `table`/`table*`; `algorithm` only if the user says "图表" includes it. Never put a specifier on `subfigure` (it is not an independent float).
- **`figure*` for wide content** (in two-column layouts): multi-panel scatter, classification maps, dataset overview panels, radar charts spanning many baselines.
- **`figure` (single-column) for compact content**: single heatmap, single bar chart, single line plot that doesn't need to span 4+ panels horizontally.
- **Width discipline.** Standardize `\includegraphics[width=...]` values so they don't drift across the manuscript:
  - **Full width**: `width=\linewidth` (equivalent to 1.0).
  - **Partial width**: always `width=0.98\linewidth` — never 0.85, 0.9, 0.95, or other ad-hoc fractions. 0.98 leaves a hair of margin without looking shrunken.
  - When the user complains about a specific value (e.g., "don't use 0.85"), sweep the whole document and normalize every partial width to the preferred value, not just the cited spot.
- **Captions: 1–2 sentences max** in the reference style, which in practice means **about 20 to 30 words**. The one standing exemption is the Related-Work comparison table, whose caption must define every column and may run to a hundred words or more. Everything else is a naming sentence: what the float shows, and nothing about how to read it or what to conclude. When a caption exceeds thirty words, the surplus is almost always column definitions or method notes, and those move to the body paragraph that first cites the float — check first whether the body already states them, as it usually does. No trailing "(a)…; (b)…; (c)…. The scene contains X classes captured over..." fluff. Further caption hygiene rules:
  - **No formula-style cross notation** (`Benchmark $\times$ baseline heat-map`, `Method $\times$ Dataset matrix`). It reads as computational/non-academic. Use academic prose instead: `Heat-map of overall accuracy across the [N] baselines and the [M] benchmarks.`
  - **No result claims in captions.** Sentences like `MFM (red) defines the Pareto frontier of every panel.` are editorial conclusions and belong in the body. The caption should describe *what is shown*, not what to conclude from it.
  - **No re-definition of abbreviations that are already defined in the body.** Once OA / AA / Cohen's $\kappa$ etc. are defined in the Evaluation Setup, downstream tables and figures use the abbreviations directly. Don't re-spell `overall accuracy (OA)` in every table caption.
  - **No back-pointers that are already implicit.** `Class definitions are listed in Table~\ref{...}` at the tail of a dataset-figure caption is filler — the reader will find it. Drop unless the pointer is non-obvious (e.g., a definition is two sections away).
  - **Explanations live in the body, not the caption.** Column/symbol definitions, methodology notes ("scores fixed, only $q$ varied"), data-sourcing notes, and per-panel breakdowns belong in the body paragraph that first references the float; the caption only names the artifact. When shortening an existing caption, move the removed explanation into that body paragraph — and during a revision round, mirror both changes in any response-letter reproduction so the blue sets stay identical.
  - **Prefer "Overview" over "Overall architecture"** for the framework figure (matches the reference papers; shorter, less generic).
  - **Use "Grouped bar chart of …" / "Heat-map of …" / "Radar of …"** as the noun phrase head, not the truncated "Overall accuracy bar across …" which sounds incomplete.
  - **For column-meaning notes in long efficiency tables**, list inline as `\``Params''`: ...; ``FLOPs''`: ...; ``Size''`: ...` rather than as full sentences (`\``Params'' is the total parameter count, \``FLOPs'' is per single-sample forward pass, ...`). Reads as a glossary, takes a third of the space.
- **Verify referenced figure files exist on disk** before adding `\includegraphics{path}`.
- **Footnotes in the abstract are unreliable in Elsevier `cas-dc`/`cas-sc`.** A `\footnote{}` placed in the abstract often does not render. To surface a code repository and a demo video, put them as plain inline `\url{}`s in the last sentence of the abstract ("Source code is available at \url{...} and a demonstration video at \url{...}.") rather than as a footnote. `hyperref` is already loaded by `cas-dc`, so the URLs hyperlink without extra preamble.
- **Avoid inline math that cannot line-break.** A long inline expression with an unbreakable subscript (e.g., `$\{S_c\}_{c\in\mathcal{C}\setminus\{\mathrm{Normal}\}}$`) pushes past the column edge because LaTeX will not break inside `\setminus\{...\}`. Either promote it to a display equation, or rephrase in words ("the $C-1$ non-normal classes of $\mathcal{C}$"). Sweep with a regex for inline `$...$` longer than ~60 chars.

**Verify each figure against its rendered artefact, not against the plotting script.** Run `pdftotext` on every figure PDF and read the extracted strings before writing or approving its caption. This catches, cheaply and reliably: captions describing the wrong quantity, axis labels using superseded terminology, panel subtitles never meant for a reader, internal titles naming an old scheme or codename, and printed statistics you had decided not to report. Re-run it after any redraw — a redraw silently restores whatever you had cropped away.

**Crop rather than discard.** When one panel of a multi-panel figure is the problem,

**Establish whether a redraw was a re-plot or a refit before touching a single
claim.** These arrive looking identical. Diff the numeric exports first: hash
the rules file, compare the summary JSON field by field, and re-aggregate the
per-edge table. If every number matches, nothing in the manuscript moves and
you only reconcile captions, which saves a full numeric re-verification. If
anything moved, every derived figure you generated yourself must be
regenerated from the new export in the same pass.

**A redraw that removes in-image titles shifts the burden onto your captions.**
Publication-style figures usually drop the plot title, which is correct, but
the caption must then carry what the title said. Recount the panels from
`pdftotext` and state the count in the caption (`the twelve leading terms`,
`each of the six leading quantities`, `four panels`), because a caption that
says "leading terms" when the redraw now shows twelve is the mismatch a
reviewer notices.

**A figure that comes back garbled twice is not going to fix itself.** When
category labels overlap into an unreadable run, the figure is unusable at that
canvas size no matter how good the data is. Substitute one you generate from
the same exported numbers rather than re-requesting it, and tell the user which
figure you replaced and why. crop to the panels you want (`\includegraphics[trim=…,clip]`) instead of dropping the figure or requesting a redraw.

**Single- vs double-column is a per-figure decision made from the aspect ratio.** A wide multi-panel figure needs `figure*`; a tall single plot inside `figure*` wastes half a page. Sweep the document once near the end and check each figure's aspect ratio against the column width it occupies. Fractional `\linewidth` values (0.72–0.9) are legitimate for this repair even when the document otherwise standardises on 0.98 — layout is the exception the width rule allows.

**Elsevier `cas-dc` float syntax.** `figure`/`figure*`/`table`/`table*` take `[pos=tbp]`, not a bare `[tbp]`; `algorithm`/`algorithm*` take the standard `[tp]`. Mixing the two forms misplaces floats silently rather than erroring.

**Keep an inventory of used and unused figures.** For a figure-rich study, record every candidate figure, whether it made the paper, and — for those that did not — a one-line reason. It makes exclusions reviewable, keeps them stable across revision rounds, and stops a previously-rejected figure from creeping back in.

### Tables

- **`table*` for wide tables** (per-class results, efficiency tables). Placement specifier follows the same user-preference rule as figures (see Figures above): either strip all, or put `[t]` on all — match whatever the user chose for the document.
- **No vertical lines (`|`).** Use `lcccc...` not `|l|c|c|c|c|`.
- **Minimal `\hline`**: top, after header, before summary/aggregate rows, bottom. No `\hline` between every data row.
- **Top-3 cell coloring** for per-class accuracy tables: `\cellcolor[HTML]{F4A7A7}` (1st red), `F9CDA0` (2nd orange), `FFF3A3` (3rd yellow). This matches a common Elsevier convention.
- **Efficiency / comparison tables**: 2 rows per condition (baseline + Ours), use `\multirow{2}{*}{Condition}`.
- **Mark the proposed method `(Ours)` in *every* table it appears in**, not only the headline one. The user sweeps for this.
- **Mirror the user's own data organisation.** If their spreadsheet holds one wide table, do not split it into three thematic ones; if a quantity sits in a named column, keep the name and the meaning. Reorganisation the user did not ask for reads as data loss and they will ask where a column went.

---

## Abbreviations

The user's strict discipline on abbreviations is enforced as three rules.

### Rule 1 — Define once globally on first occurrence in the body

For each abbreviation, find the **first body occurrence** (Introduction onward, not counting Abstract and Highlights, which are independent sections). Define it there as `Full Term (ABBR)`. After that **first body occurrence**, every subsequent mention anywhere in the paper body should use the abbreviation `ABBR`, never the full term again.

Concretely:
- Intro `¶4`: `the multi-head cross-patch attention (mCrossPA) module` ✓ first def
- Related Work, Methodology, Experiments, Conclusion: use only `mCrossPA`, never re-spell `multi-head cross-patch attention` again.
- **Do not re-define `(ABBR)` in a later section** even if that section "stands alone" — the paper is read as a continuous document. The only exceptions are below.

**Exceptions** where re-definition is acceptable (because the element is read out of order):
- Abstract — independent of body; defines abbreviations it uses.
- Highlights — appears separately on journal website.
- Figure / table captions — may be read out of order; define on first caption use if the abbreviation appears there.
- Section / subsection titles — structural elements; may keep `Full Term (ABBR)` for navigability.

### Rule 2 — Don't define an abbreviation that isn't reused

For each `Full Term (ABBR)` definition, check whether `ABBR` appears anywhere afterwards in the same section (Abstract, Highlights, Intro body, etc.). If it doesn't, **drop the `(ABBR)`** and just use the full term. Defining an unused acronym is clutter, signals careless writing, and is a common AI tell.

Example:
- Abstract: `the proposed Cross-Modal State-space Module (CMSM) fuses...` — if `CMSM` never appears again in the abstract, drop the `(CMSM)` and just write `the proposed Cross-Modal State-space Module fuses...`.

**Exception**: the paper's own method name (e.g., MFM in an MFM paper) should always be established on first mention even if used only once in that section — because the name appears in the title, citations, and elsewhere.

### Rule 3 — Don't use an undefined abbreviation in a section

If you write `SSM` in a section where neither that section nor an earlier section has defined `selective state-space model (SSM)`, the reader doesn't know what `SSM` means. Either define it on first use in that section, or spell it out fully.

This is especially important for Highlights (independent of Abstract) and the Abstract itself (independent of body). Each of these may need its own first-use definitions.

### Method-name introductions (acronym first)

When the method name comes first and its expansion follows (the "NAME: ..." title pattern), introduce it as a comma apposition woven into the sentence — "This paper proposes SEAL, a self-adaptive energy-aware reinforcement learning framework, in which ..." — never as a long parenthetical ("SEAL (self-adaptive energy-aware reinforcement learning)"). The user finds long parenthetical expansions unprofessional. The standard short definition pattern `Full Term (ABBR)` is unaffected: parentheses there wrap only the short acronym, not running text.

### Universally known abbreviations

Common domain abbreviations may appear undefined: `CNN`, `RNN`, `ViT`, `LSTM`, `GRU` (CV/ML); `AUC`, `OA`, `AA`, `F1`, `mAP`, `IoU` (metrics); `LiDAR`, `SAR`, `DSM`, `RGB`, `MSI` (remote sensing); `BIM`, `GIS`, `CAD`, `UAV` (engineering). Err on the side of expanding once on first use, especially in Highlights and Abstract.

### Consistency

Once defined and chosen, stick to the abbreviation. Don't randomly alternate between `SSM` and `selective state-space model` within the same paragraph or section.

### Audit checklist (run before each push/submission)

For each section in document order:
- [ ] For every `Full Term (ABBR)` definition: confirm `ABBR` is reused at least once in the same section. If not, drop the `(ABBR)`.
- [ ] For every section after first body definition of `ABBR`: confirm the full term `Full Term` does not appear (use `ABBR` instead).
- [ ] Confirm `ABBR` is never used in a section that hasn't defined or inherited the definition.
- [ ] Confirm structural elements (figure captions, section titles, bullet headers) that re-introduce `Full Term (ABBR)` are intentional.

---

## Reference verification (avoid fabricated citations)

### Standing rule: no reference enters the paper unverified and unconfirmed

The user's instruction, verbatim: 每次写任何参考文献都要检查是否存在且信息是否正确，如果不确定我宁愿不写或者需要让我检查后才能放到论文里。如果我没确认的千万不能放进去。

This applies to **every** reference you write, edit, or move, in any file: a new `.bib` entry, a `\cite{}` added to the `.tex`, a citation in a response letter or cover letter, a row in a comparison table, a dataset or tool attribution. There are no exceptions for "well-known" papers, for papers you are confident about from memory, or for entries copied from a previous manuscript of the user's.

**Why.** On the Mamba2-SLAM manuscript (September 2026) a full sweep of 52 cited entries found four with substantive errors: one entry whose title and author list did not exist and whose DOI resolved to an unrelated paper, one whose DOI was off by one digit and whose author given names were all wrong, one with `and others` in place of the author list, and one whose author list did not match the arXiv record. All four had been written from memory. A single fabricated reference is grounds for desk rejection.

**How to apply, every time.**

1. **Verify before writing, not after.** Resolve the paper against Crossref (`https://api.crossref.org/works/<DOI>` or `query.bibliographic=`), the arXiv API (`export.arxiv.org/api/query?id_list=`), or the publisher page. Compare title, full author list, venue, year, volume, issue, pages, and DOI field by field against what you are about to write. A DOI that resolves is not enough; the record it resolves to must match the entry.
2. **Preprints: check the version.** arXiv papers get renamed and re-authored between versions (two of the four errors above were exactly this). Record which version the title and author list come from, and check whether a published version now exists.
3. **If any field cannot be verified, do not write the entry.** Leave the citation out and either soften the claim it supported or drop the sentence. Do not write a partial entry, a placeholder, `and others`, or a "best guess". 不确定就不写.
4. **If the user wants the citation anyway, hand it to them for confirmation first.** Present the entry with what was verified and what was not, and wait. An unconfirmed reference never goes into the `.tex` or `.bib` on your own judgement. 没确认的千万不能放进去.
5. **Report the verification with the work.** When you add or change references, state in the reply which ones were checked, against what source, and any field you changed. The user will ask; have the answer ready.
6. **Full sweep on request or before submission.** When asked to "检查每一条参考文献", or before a submission draft, sweep every cited entry with a script (the Crossref/arXiv script kept in the scratchpad) and return a per-entry table with status ✅ / ⚠️ / ❌ and the exact correction for each ⚠️ and ❌. Verify only the entries actually `\cite`d (check for `\nocite{*}` first); say how many bib entries are uncited.

### Checklist before adding any `\cite{key}`

1. **Verify the key exists in the bib file.**
2. **Verify the entry itself against an external record** as in the standing rule above; "spot-check" is not enough for entries you wrote or edited. Entries with a future year, "in press", `and others`, a vague journal name, or no DOI are the most likely to be wrong.
3. If a cited paper turns out not to exist, **remove the cite or replace with a real, verified one**.
4. Never invent a citation just to support a claim. If no real cite supports the claim, soften the claim or remove it.
5. When the bib file has a comment like "all references verified via web search", still re-verify the most recent ones — those are most likely to be hallucinated.
6. **CVF versus IEEE pagination.** CVPR/ICCV papers have different page numbers in the CVF open-access proceedings and on IEEE Xplore. If the entry carries an IEEE DOI, use the IEEE pages; do not mix.

### What is NOT acceptable in a submitted bibliography

A `.bib` file going to a reviewer must contain only fully verified, fully populated entries. The following patterns are unacceptable and must be removed (not "flagged for later") before submission. **Why:** TBD/pending fields are an obvious red flag for reviewers — they read as either citation farming or careless sourcing, and they instantly damage the paper's professional credibility even when the cited paper is real. **How to apply:** if author names cannot be web-verified, do not include the citation at all; either find a verified replacement or remove the supporting claim. Never leave the placeholder in and "fix it before submission" — that promise is exactly what gets forgotten.

| Forbidden pattern | What to do instead |
|---|---|
| `author = {Authors TBD}` / `author = {TBC}` / `author = {Anonymous}` placeholder | Look up the real author list. If unverifiable, delete the entry and the citing line. |
| `note = {... pending verification before submission}` / `note = {... TBD ...}` | Verify and remove the note. Delete the entry if cannot verify. |
| Bib entries containing the literal strings `verifying`, `verification`, `pending`, `TBD`, `TBC`, `???`, or `Authors not yet ...` | Never let these reach a reviewer. Resolve or delete. |
| Title, journal, year, or DOI fields containing question marks / placeholders | Resolve from a verified source (ScienceDirect, arXiv, DOI.org, publisher page). |

**Legitimate `note = {...}` fields** (keep these — they are standard bibliographic conventions):
- `note = {In press}` — accepted paper not yet assigned volume/pages.
- `note = {Art. no. NNNNN}` — IEEE-style article number when pages are not used.
- `note = {Preprint, arXiv:NNNN.NNNNN}` — when the cited version is the arXiv preprint.

These are descriptive metadata, not flags-for-future-work.

### Cite every tool, library, dataset, and method you use

Reviewers (and the user) notice uncredited use of someone else's work. Before submission, sweep for these and add an inline `\cite` at the **first mention** of each:

- **Open-source implementations** you build on (e.g., `efficient-kan`, a specific GitHub repo, `mamba-ssm` kernel). A `@misc` bib entry with the repository URL is the correct citation form.
- **Optimisers / algorithms named in the text** (AdamW → Loshchilov & Hutter; BIC → Schwarz 1978; a specific symbolic-regression engine → its paper).
- **Frameworks** (PyTorch, PyTorch Lightning, JAX) — one cite at the hardware/software-stack paragraph.
- **Datasets** — cite the *original* paper that introduced each benchmark at first mention (UCF-Crime → Sultani 2018, ShanghaiTech → Luo 2017, XD-Violence → Wu 2020). Naming a dataset without citing it is a common oversight.
- **The deployed/predecessor model** you analyse or extend — cite once prominently, then hand the rest of its background literature off via group-citation.

A bib entry that exists but is never `\cite`d inline is invisible to the reader — grep for the key in the `.tex`, not just the `.bib`.

### Self-citation and venue-matching citation discipline

When the target venue and the surrounding bibliography start to look suspicious to a reviewer, the paper's perceived credibility drops sharply regardless of the actual scientific content. Watch for and proactively reduce:

- **Dense in-press citations to the same target venue.** Five 2026-in-press citations to the journal you are submitting to looks like venue-matching — even if every paper is real and topical. Keep the most directly relevant; remove the ones whose connection to your topic is a stretch.
- **Tangential self-citation.** Self-citation is normal when topically aligned; it becomes a red flag when the cited paper is in a different subfield from the submission (e.g., citing your own robotics-RL paper in a hyperspectral-classification submission to pad the bibliography). Remove self-citations whose topical connection is weak.
- **Author-name overlap between the submitting author list and recent citations.** Reviewers do notice. If `\citep{author2026foo}` and the submitting author share a surname plus email-host institution, decide whether the cite is genuinely load-bearing. If not, drop it.

If the user explicitly asks to "cite more papers from [target venue]", proceed — but apply the topical-fit filter and the no-TBD-authors rule strictly. A venue-matched citation that fails verification is worse than no venue-matched citation.

---

## Process tips for working with the user

- **When the user supplies a reference paper** (e.g., `imitate.tex`, `template.tex`, or names a journal style): open and read it carefully before writing. Mirror the sentence patterns, paragraph structure, and section organisation. Do not invent a "style of the reference" — imitate directly.
- **When a convention is in question, count the siblings instead of judging.**
  Asked whether a subsection title may open with `The`, the answer came from
  listing all 35 subsection titles across the two companion manuscripts and
  finding that none opens with an article. That is evidence; a preference is
  not. The same method settles heading capitalisation, whether acronyms get
  expanded, how many RQs there are, and where the back matter sits.
- **When the user gives short corrective feedback** (e.g., "don't use `---` between sentences", "缩写", "no replacement"): interpret broadly and sweep the entire document, not just the cited location.
- **When the user says "push"**: skip TodoWrite (single-step task), check divergence, commit only intentional source changes, push (with git workflow tips below if applicable).
- **Always check that what the contribution claims, the body actually proves.** Especially: don't list a remark or informal observation as a "result" or "theorem".
- **When renaming a section or label**: sweep all `\ref{}` and prose mentions for stale references.
- **When deleting unused content** (datasets, methods, ablations the paper doesn't actually use): delete the table, the figure, AND the supporting preamble (color definitions, custom macros). Don't leave half-removed artefacts.
- **精简 is not 删减.** When the user asks to tighten, they want the same semantics in fewer words. Merge clauses, drop function words and hedges, and then check that every claim survived. Deleting a claim to hit a length target will be caught and reverted.
- **包装 means academic register, not decoration.** When the user says a sentence 不高大上 / 缺少包装 / 太直白, the fix is a stronger *verb* and a claim stated at the level of the research position — never an added adjective and never a longer sentence. When a sentence is called 口语化 or 模糊, the fix is a concrete noun, not a more formal synonym.
- **A question about a phrasing is a request for a recommendation.** "这个好吗", "是否合适", "用 A 还是 B" — answer with one choice and the reason, not with a survey of options. If the honest answer is "neither", say that and supply the third.
- **Successive trims can destroy a passage.** After three or four rounds of cutting one paragraph, re-read it whole against the original; the user's 我怎么感觉你越写越差 usually means a sentence has been reduced to a definition plus two weak tails. Restore and re-cut once, rather than trimming further.
- **Do not over-apply a differentiation instruction.** Being told to differentiate from a companion paper does not license removing the method contribution, the shared format, or a section the second paper genuinely needs. Ask what the instruction actually scopes before cutting structure.
- **Sweep captions and figure images when terminology changes.** A rename applied to prose only leaves the old term in captions and inside plotted images, which is where a reader most notices it.
- **Recompute, never recall, any aggregate that is restated.** Medians, horizons, counts and "roughly N" phrasings drift as figures and tables are added and removed.

---

## Generic anti-patterns (avoid proactively)

These are common pitfalls regardless of paper topic:

1. **"Substantial reductions in [efficiency metric]" as its own contribution bullet.** Fold into method-description contribution (as inherent property) + experimental-validation contribution (as confirmation).
2. **"Drop-in replacement" / "replaces" to describe your method.** Frame as innovation: "offers an alternative", "introduces", "proposes".
3. **Specific numbers (percentages, raw counts) in Introduction contributions itemize.** Abstract claims only — save numbers for Abstract, Highlights, Experiments, Conclusion.
4. **Reusing dataset visualizations in Results.** They belong in Datasets / Implementation.
5. **Including a baseline in qualitative comparisons that isn't a quantitative baseline.** If method X isn't in the per-class tables, don't show its output in the qualitative figure.
6. **Borderline threshold claims off by one or two** (e.g., "$\geq 99\%$ on N classes" when only $N-1$ actually meet the threshold). Count carefully.
7. **Unused datasets/methods lingering as tables.** If you don't run experiments on it, delete the table AND the supporting preamble.
8. **Inconsistent numbers** drifting between sections (Abstract says X%, Conclusion says Y%, Experiments table shows Z%). Pick one canonical source (usually the efficiency or per-class table) and propagate.
9. **`\ref{sec:old-name}` after renaming the section to a new label.** Sweep cross-references when renaming.
10. **Overclaiming "unique" / "best" / "first" without verifying.** "Unique top performer on all three metrics on every benchmark" — easy to be wrong; check every cell.
11. **Em-dash sandwiches** (`X --- Y --- Z`) as parenthetical phrasing. Use commas or parentheses.
12. **Long compound sentences with three or more subclauses.** Split into separate sentences.
13. **A comparison-table column on which every method scores ✓.** It carries no discriminative value and a reviewer notices. Delete the column, or add cited works that score ✗ on it.
14. **A comparison table that does not separate you from your own companion paper.** With two submissions on one platform, at least one row or column must make the difference visible at a glance.
15. **Restating an aggregate from memory instead of recomputing it.** Aggregate horizons, medians, and "roughly N" statements drift as the data changes; recompute from the table at every restatement.
16. **A figure that is really a table** (rendered if-then rules, formula lists, symbolic expressions, a screenshot of a grid). Convert it to a real `table` or to text — searchable, selectable, and far cheaper in page budget.
17. **A caption describing a different quantity from the one the panel plots** (raw value vs normalised ratio; "three held-out states" vs one state resolved three ways; a two-panel figure described as one). Verify against the rendered artefact, not against your memory of what you asked for.
18. **One symbol serving two roles inside one algorithm** (e.g. `\mathcal{L}` as both a context set and the objective). Sweep the algorithm's symbol table before finalising.
19. **Claiming a gate the data does not meet** ("every reported clause reaches 0.95" when one is 0.881). Either enforce the gate by dropping the item, or restate the quantity as a reported property rather than a selection criterion.
20. **Over-tuning float parameters to fix layout.** Raising `dbltopfraction`/`dbltopnumber` usually makes it worse (float-only pages, more total pages). Fix layout by scaling individual figures and by moving single-column content out of `figure*`.

---

## What 包装 actually changes, sentence by sentence

The instruction 包装一下 / 不够高大上 arrives on sentences that are already
accurate and already concise. The fault is never length and never vocabulary.
It is that the sentence reports **what was done** instead of **what it buys,
what it closes, or what it lets the reader now do**. The repair is one
stronger verb plus a consequence clause, at the same length.

**Every step of a method gets its own payoff clause.** A two-step construction
described as "the first does A and the second does B" will be sent back. Each
step needs the question it settles. Worked pair:

> Recovery proceeds in two stages that separate two distinct questions. The
> reward the model predicts is first shown to agree with the reward the
> environment returns, which licenses reading what follows as a statement
> about the task rather than about a network.

became

> Recovery is staged so that two questions which are routinely conflated are
> settled in order. The objective the model pursues in imagination is first
> placed against the reward the environment returns, which decides whether it
> describes the vehicle at all and therefore whether anything read from it may
> enter an engineering record.

Nothing was added but the consequence. `separate two distinct questions` became
`two questions which are routinely conflated`, which says why separating them
is a contribution; `licenses reading what follows` became `decides whether
anything read from it may enter an engineering record`, which names the stake.

**The proposal sentence names the transformation, not the activity.** `a
framework that recovers X and states it in Y` is an activity. `a framework
that lifts X out of the representation holding it and issues it as a citable
specification, written in Y` is a transformation with a destination. Reach for
a verb that moves the object between states of the world: *lifts out of /
issues as*, *transforms from / into*, *quantifies in the units of*, *resolves
into*.

**The central question needs a payoff at its heavy end, not a caveat.** The
final clause of an `\emph{}` central question is its most emphatic position,
so a non-interference property placed there wastes it. Move the property into
the parallel triplet and close on what becomes possible: `… so that what a
vehicle already in service was trained to pursue can at last be set against
the document it was commissioned under?`

**Every contribution states the gap it closes and what that enables.** A bullet
that describes its own mechanism is a description, not a contribution. Worked
pair:

> Evaluation on a deployed controller quantifies how much of the recovered
> objective corresponds to each specified term and identifies a dependence on
> vehicle velocity for which the specification states no term.

became

> Evaluation on a deployed agent establishes how far the objective the vehicle
> actually pursued reproduces the one its designer wrote, term by term, and
> surfaces dependences on quantities the specification never names.

`quantifies how much … corresponds` is measurement; `establishes how far
the objective the vehicle actually pursued reproduces the one its designer
wrote` is a finding about the world. `identifies a dependence` is neutral;
`surfaces dependences the specification never names` states the discovery.

**Never state a contribution by what the alternative lacks.** `This ordering
supplies the warrant that attribution alone cannot provide` defines your
contribution as somebody else's deficiency, and reads defensively. Say what
yours earns: `The ordering is what qualifies a recovered law for an
engineering record instead of leaving it a description of a network.`

**`closing the gap between …` is filler even when the gap is real.** Once a
bullet has claimed a first, the gap is implied; the closing clause must add a
capability instead. Replace with what the reader can now do: `so that the two
can be placed side by side before the vehicle is commissioned`, or better, name
what the artefact becomes: `returned as a document an operating organisation
can hold, cite and contest`.

---

## Settle the story before writing any prose

On a paper whose results already exist, the expensive failure is not bad
sentences, it is the wrong narrative. One manuscript went through six rounds of
讲什么故事 / 重新给出完整的故事和论文的结构 before a single section was drafted,
and every round was cheaper than the rewrite it prevented. When the user asks
怎么讲故事 / 什么 gap 什么创新, they are not asking for prose. Answer with the
story, the gap, the contribution list, and the section-by-section outline, in
plain text, and get agreement before opening the `.tex`.

**The story may not claim a problem the paper does not solve.** This is the
single most-repeated correction on that manuscript: 我的意思是这个故事讲的不对吧，
因为我们没有解决规模的事情？ / 但是我们也没有解决这个啊 / 我们有足够的规模？ A
compelling framing that opens a gap the results do not close is worse than a
modest framing that closes the one it opens — the reviewer reads the promise in
the Introduction and checks it against Section 5. Before proposing any framing,
walk each of its premises and ask what in the results discharges it. Drop the
premises nothing discharges.

**Structure a portfolio paper as one main claim plus side findings.** For an
application-first paper the user's own decomposition: 把 [the first application]
包装成主要的，然后几个表格的 finding 包装成 side 问题. The main claim carries the
novelty; the table-level findings become secondary contributions. Do not invert
this — a paper led by an interesting side finding reads as a paper without a
thesis.

**A first-application claim must be packaged, and must not be undercut.**
"To the best of our knowledge the first [paradigm] agent trained for [domain]"
is a contribution. "We apply [algorithm] to [simulator]" is a description of
work. And once the claim is made, never also write that the algorithm was used
unmodified — that sentence deletes the contribution the reader just accepted.
The packaging is legitimate framing of what was actually done; it becomes
academic misconduct only if it asserts something untrue, so keep the literal
claim checkable (`first … for underwater vehicle control`, not `first world
model`).

**Every contribution maps to a named table or figure.** Expect to be asked
这四条 contributions 都有数据支撑吗？分别是哪个数据制成的 and have the mapping
ready. A contribution with no artefact behind it is a finding you hoped for.

**Research questions follow the story, not the data dump.** Once the story is
performance + efficiency + findings + deployment cost, the RQs are those four,
in that order, and the Results section has exactly four subsections. Be ready to
state, for each RQ, which table answers it and how.

---

## Working from the user's own data

The user supplies spreadsheets, figure folders, and result dumps, and expects
them used completely and faithfully. Every violation below was caught and
corrected on a real manuscript.

- **Use all of it.** 你认真看我的 xlsx 里的数据，不要漏掉了，都放在论文里. Before
  drafting Results, enumerate every sheet, every column, and record where each
  one lands in the paper. Columns you judge uninteresting still get a decision,
  and the decision gets stated.
- **Never derive a number the source data does not contain.** A "steps" column
  computed from a time column will be spotted (表7的 steps 你怎么得到的？我原始
  数据里没有这个啊). If a quantity is needed and is not in the data, ask; do not
  synthesise it.
- **Never re-round.** If the source has two decimals, the table has two decimals
  (我不是有小数点吗你为什么给整数化了？).
- **Never re-label.** `time_to_goal_mean` is a time, not a step count. Carry the
  source's unit and meaning through to the caption.
- **Do not reorganise without being asked.** If the user's sheet is one wide
  table, produce one wide table. Splitting it into thematic sub-tables loses the
  comparison the user built it for, and they will ask why it was split.
- **Prefer the measured column to a derived ratio.** When the data already
  contains the quantity, do not invent a normalised score to report instead
  (我不是里面有四个 xlsx 表格吗？你用这里面的数据啊).
- **Read figures before describing them.** Expect 解释图6我没看懂 — if you cannot
  state what each axis and each curve means from the artefact itself, you cannot
  write its caption or its body paragraph.
- **The text artefacts are data too, and get converted, not mentioned.** A
  results folder ships `.txt` and `.csv` beside the figures, and every one is
  expected to reach the paper as a table. Here the IF-THEN file became a
  threshold-clause table, the symbolic-form file a closed-form table, and the
  local-decomposition CSV an exact ledger whose rows sum to the model's own
  prediction. Enumerate the folder and record where each non-image file lands
  before drafting Results; a file used only to generate a figure has not been
  used.
- **Two tables built from one quantity contradict each other unless the columns
  are named apart.** A clause table and a closed-form table both carried a
  column called `Fit` for the same variables at different values, because one
  fits a two-piece hinge and the other a polynomial. Rename to `Hinge fit` and
  `Closed-form fit`, and have each caption say the two are not comparable.
- **One name per quantity across every table.** Shortening a label to make one
  table fit produced `Recent mean error, heave` in one table and `Tracking
  error, recent mean, heave` in another for the same variable. If the full name
  does not fit, widen the table; naming consistency outranks a saved column.

**Placeholders and self-annotation.** Two firm rules:

- **Mark genuine unknowns in red, in the draft only**, so the user can see them
  at a glance, and clear every one before the submission draft. 不知道的不要瞎说，
  不要留下 ai 的痕迹.
- **Never leave an inline note about your own uncertainty** — no `CONFIRM`, no
  `TODO`, no "inferred by consistency, not read from the original". If a table
  cell about someone else's paper needs a value, go read that paper. The user's
  response to such a note was 不要注释这种。你自己去搜论文看.
- **When in doubt, write less.** 写多错多 — a sentence you are unsure of is a
  sentence a reviewer will query. Cut it rather than qualify it.

---

## Companion papers: two manuscripts from one experimental substrate

A frequent situation: the same vehicle, the same trained checkpoint, the same
simulator, the same recorded episodes, and the same analysis family yield two
papers, submitted to the same journal, with the first still under review. This
is legitimate and common, but it is the single largest reviewer-credibility
risk in the portfolio and it must be managed deliberately from the first
paragraph of the second paper.

**What "differentiation" means and does not mean.** The user's own correction,
worth quoting because it is easy to get backwards:

> 我说的跟第一篇有区分度不是说你不能用她的格式或者风格，而是focus的点/创新点是跟他不一样的。或者背景这些段落或者基础知识这种描述尽可能不同，不要让人觉得是自我抄袭

So:

- **Keep** the format, the section architecture, the register, the contribution
  patterns, the RQ structure, the caption style. Consistency across a portfolio
  is a virtue, and rewriting a working structure to look different wastes effort
  and usually makes the paper worse.
- **Diverge** on the focus and the novelty claim, and on every paragraph whose
  content is *background* rather than *result*: the opening of the Introduction,
  every Related Work subsection, the problem-formulation preamble, the
  vehicle/task description, and any shared preliminaries.

**Rewrite background paragraphs from a different premise, not with different
words.** Paraphrasing the same argument is what gets flagged. Change what the
paragraph is *about*. Worked example: Related Work §2.1 moved from "system
identification is expensive, so learned controllers are attractive" to
"classical observers document their forgetting time constant, and learned
controllers document nothing"; §2.2 moved from "the sample-efficiency lineage of
world models" to "the lineage of the *form* of the learned state". Same
literature, different claim, near-zero textual overlap.

**Measure the overlap; do not estimate it.** Two cheap scripts, worth writing
once and keeping:

- an n-gram scanner over both `.tex` files reporting shared runs of ≥ 9 words.
  Target: single-digit runs, well under 200 words total. Achieved on this pair:
  30 runs / 425 words before the rewrite, 12 runs / 140 words after.
- a bibliography-overlap ratio. Total identity is a red flag; so is an
  artificially low number. 70–75 % is normal for sister papers in one
  subfield. Achieved: 82 % → 73 %, by swapping four references in the
  most generic citation cluster for four that are specific to the second
  paper's actual angle.

**Shared formal results: keep, compress, attribute.** If a remark or proposition
is genuinely needed by both papers, do not delete it from the second and do not
restate it at full length. Compress it to the statement plus a one-line proof
sketch, and cite the companion explicitly at the point of reuse. That converts a
self-plagiarism liability into an ordinary citation.

**Give the second paper formal results the first one cannot have.** This is the
strongest available defence against "why is this not one paper", and it must be
load-bearing rather than decorative. In this pair the second paper's
reset-consistency proposition is what makes its truncated replay branch a legal
comparison at all — the first paper performs no intervention and therefore has
no use for it. If the second paper's unique propositions could be deleted
without breaking anything, the differentiation is cosmetic and a reviewer will
say so.

**Make the difference visible in a table.** Add at least one column to the
comparison table on which your own companion scores differently from the present
work. A reviewer who has both manuscripts open should be able to see the
separation without reading two methods sections.

**Cite the companion; consider disclosing it to the editor.** An in-manuscript
citation is a legitimate disclosure and is often all the user wants. A one-line
note in the cover letter ("a companion manuscript is under review at this
journal; the two address different questions and stand independently") is
stronger, because an editor who *discovers* the sibling rather than being told
about it reads it less charitably. Raise this once; if the user declines, drop
it — it is their call, and the citation does satisfy the formal requirement.

**The honest test for duplicate publication**, worth applying before submission:
*could a reader holding the first paper reconstruct any headline result of the
second?* If no — different target quantity, different intervention, different
conclusions — it is not duplicate publication, and you can defend it in one
paragraph. If yes for even one result, that result belongs to one paper only.

---

## Never expose a weakness: omission over qualification

The user's standing rule across both manuscripts, in their words: 不要暴露缺点 /
不安全的我宁愿不写不提 / 这种坏论文的数据我宁愿不提. This is not a request to
misrepresent anything. It is a scoping rule: **a claim you do not make cannot be
attacked, and a number you do not report cannot be disputed.** Apply it as
follows.

**Omit; do not qualify, and do not spin.** The instinct to keep a weak result and
protect it with a caption is wrong twice over. The user rejected exactly this
move — rewriting a caption so an inconclusive value "becomes" an expected one
(把这一点写进 caption，1.88 就从"我们测不准"变成"信号本该在那里消失"：不要写).
A defensive caption tells the reviewer where to look. Cut the content instead.

**What counts as a weakness to remove**, learned by sweeping these two papers:

- fidelity and goodness-of-fit statistics of any kind (R², explained variance,
  reconstruction error against a target, "share accounted for")
- signal-to-noise columns, Monte-Carlo standard-error overlays, and any panel
  whose subtitle names a regime where the measurement stops working
- figures whose predicted-vs-target numbers visibly disagree
- surfaces that are trivially separable, i.e. figures that make the method look
  easier than the paper claims it is
- selection gates the data does not meet
- the word `Best`, printed metric values, and internal codenames baked into
  figure images

**Narrow the claim so nothing asserted becomes false after the cut.** This is the
step that makes omission safe rather than evasive. When the fidelity evidence
came out, the claim scope moved from "the belief" to "the attribution" — every
remaining sentence stayed literally true, and nothing now rested on the deleted
material. If you cannot narrow the claim, the material is load-bearing and must
stay; say so plainly to the user rather than deleting it quietly.

**Remove the whole family, not the headline instance.** Deleting a fidelity
section while leaving its metric column, its defining equation, and three
sibling figures produces dangling references and a reviewer who wonders what was
removed. Sweep: section, subsection, equation, table column, every figure of the
same family, every prose mention, every `\ref`.

**The weakness is often inside the image.** Axis labels, legends, panel
subtitles, and figure titles carry the numbers you decided not to report. Text
in the `.tex` is not the whole surface — see the figure-audit rules above.

### Never write speculation, doubt, or an unresolved question

A separate ban, stated by the user in the strongest terms across two
manuscripts, and the one whose violation most reliably reads as AI-written
text.

- **A whole section built on an untested suspicion must go.** The user's verdict on one such section: 5.5 节很扯淡可以不要。像这种怀疑的没有证据的，没有解决的没有支持的就去掉，这不是胡说八道吗？不要写这种没用的.
- **Never write that something was not identified, not detected, not resolved, or remains unclear.** 我的论文里永远不要出现"not identified"这种. A paper states what it establishes. An open question that is genuinely worth naming belongs in Future Work as a direction, phrased positively, and nowhere else.
- **Never offer a mechanism you did not measure.** "may be attributable to", "we suspect", "this could indicate" — delete the sentence, not the hedge. Hedging a speculation does not make it safe; it makes it visibly unsupported.
- **A finding that is a property of the metric, not of the method, is not a finding.** "Mean tracking error cannot structurally distinguish the methods" describes the measure, not the agent — cut it, and cut the table column that produced it if nothing else rests on it.
- **When a number cannot be confirmed, delete the sentence.** Not "approximately", not "about fifty steps" from memory. 写多错多 — the more you write, the more you get wrong.
- **Never define your own contribution by what it is not.** 我宁愿不提我也不要. A
  disclaimer that defuses a novelty attack in one venue reads as a missing
  contribution in the next, and the reader remembers the negation, not the
  clause after it. Full treatment, with the worked replacements and the test for
  which negations to keep, under **Cover letter and response document**; the
  rule applies to the manuscript's front matter identically.

**Where this rule does not apply.** It governs what to *include*, never what to
*claim about what is included*. Every retained number stays exactly as the data
gives it, limitations that a reviewer will independently hit are still stated,
and Future Work still names the real gap (here: no physical platform). Silence
about an unreported result is normal scientific selection; a false statement
about a reported one is not, and no version of this rule licenses the second.

---

## Back matter is carried across, not re-invented

Everything between the Conclusion and the bibliography is boilerplate that is
identical across a portfolio, and the user expects it copied from the previous
submission verbatim rather than rewritten. Take it from the companion
manuscript's `.tex` in one block, from `\printcredits` down to the
`\bibliographystyle` line. For Elsevier `cas-dc` that block is:

1. `\printcredits` — renders the CRediT statement from the `\credit{}` fields
   in the author list.
2. `\section*{Declaration of competing interest}`
3. `\section*{Declaration of Generative AI and AI-Assisted Technologies in the
   Writing Process}`
4. `\section*{Acknowledgment}` — the grant numbers.

**`\credit{}` fields alone render nothing.** The author block can carry a full
set of CRediT roles and still produce no contribution statement, because the
list is only typeset where `\printcredits` appears. A manuscript drafted
section by section will have the `\credit{}` fields (they were copied with the
author block) and be missing `\printcredits` (it lives at the other end of the
file). Check for it explicitly, and confirm by grepping the compiled PDF for
`CRediT authorship contribution statement`.

**Never retype a grant number.** Copy the acknowledgement string; a digit
altered in transcription is the kind of error that reaches print. Verify the
numbers survived by grepping the built PDF for them.

**Do not reword these blocks to "differentiate" from the companion.** They are
required declarations with standard wording; a paraphrase of an AI-usage
declaration or a competing-interest statement reads as evasive, and an n-gram
overlap check will flag them as shared text that is entirely legitimate. Verify
overlap on the body only, excluding the author block and everything after the
Conclusion.

---

## Cover letter and response document

Both are separate artefacts from the manuscript and follow the venue's own
conventions, not the paper's.

- **Model them on the user's previous submission to the same journal**, not on a
  generic template. Match its paragraph count, its paragraph lengths (± 10 %),
  its register, and its section order.
- **Cover letter: no DOIs, no citation apparatus.** The user's rule
  (cover letter 不用引用doi吧). Name works in prose if needed; do not build a
  bibliography inside a letter.
- **Response document: DOIs are expected, and every one must be verified.**
  Resolve each against Crossref and check not just that the DOI exists but that
  the *surrounding sentence* matches the record — author surname, year, venue,
  volume, article number. Then make the format uniform across all citations
  (`Author et al., Journal, Vol. NN, YYYY, Art. NNNNNN, https://doi.org/…`);
  a citation missing the volume that its neighbours all carry looks careless
  even though it is correct.
- **Respect the character limit** stated in the submission system's question
  form, and check it after every edit — not once at the end.
- **Scope paragraphs quote the journal's own aims-and-scope language** and map
  each phrase of it onto the manuscript: the artefact, the knowledge-intensive
  task, the formalised knowledge, the power-and-scalability claim. Keep them to
  the length of the previous letter; the temptation is to write three times as
  much, and the user will cut it back.
- **Re-targeting a letter to a new journal is a sweep, not a find-and-replace of
  the journal name.** The previous venue's *scope vocabulary* survives an
  otherwise complete rewrite and reads, to the new editor, as a letter written
  for somebody else. Re-targeting an AEI letter to Neurocomputing left behind
  `noteworthy new power and scalability` — which is AEI's own submission
  criterion, not a neutral English phrase — after `artifacts-centered
  engineering systems`, `knowledge-intensive tasks` and `decision artefacts`
  had all been caught. Grep the finished letter for the old venue's exact
  wording, and for its name in the address block, the opening sentence, the
  scope paragraphs and the closing sentence.
- **Claim only the scope clauses that are true, and check what each one means.**
  A clause can sound like yours and not be: Neurocomputing's "practical aspects"
  means simulation environments, neurocomputers and neurochips, so a
  post-hoc analysis protocol may not claim it. Two or three true axes stated
  plainly beat six stretched ones, which read as an author who cannot place
  their own paper.
- **Name the object of study in the venue's standard terms, once.** An editor
  assigns the paper from the words in the scope paragraphs. `a recurrent world
  model deployed as a controller` is accurate and invisible to that process;
  adding `trained by deep reinforcement learning` and `the hidden state of its
  recurrent network` costs six words and puts the paper in the right pile.
  Audit by counting the venue's own scope terms in those paragraphs.
- **Never state your own contribution by negation.** The user's rule is
  absolute: 我宁愿不提我也不要. `The X function family is not itself claimed as
  new`, `what the paper contributes is not an architecture but …`, `a
  contribution to the field rather than an application of an existing method to
  a new domain`, `made measurable at all`, and `which let a reader verify that
  the statement was not obtained by choosing what to show` were all struck from
  one letter. The last is the worst of them: it asks the cherry-picking question
  on the reviewer's behalf. Negations about the *gap* — what no existing method
  yields, what the reward never names, what the operator has no quantity to
  consult — are the engine of the letter and stay. The test is whose deficiency
  the sentence describes.
- **A narrow target is resolution, not a smaller claim.** `the quantity
  explained is an isolated internal effect rather than the whole command` puts
  the emphasis on what you did not explain. `the explanation is resolved to a
  single internal cause, the part of the command the accumulated state supplies
  as distinct from the part the current observation determines` says the same
  thing as a gain in resolution, and leaves the contrast to be carried by what
  the prior method fails to separate.
- **State non-interference as a capability.** `without altering the network it
  describes` and `neither requires the network to be modified` describe an
  absence; `from recorded operation alone, so that the controller it describes
  stays in service` describes what the reader gets. Say it once as a formal
  property where it is proven, and positively wherever else it appears — a
  property repeated four times in negative form starts to read as a limitation.
- **Co-author correspondence is part of the submission.** Messages asking a senior co-author to approve an author list or a target venue should be short, plainly worded, and explain the contribution in terms a non-specialist colleague can follow in one sentence. Name the venue with its standing, state each person’s role explicitly, and keep the register polite and unpadded.
- **Write the generator as a script, not by hand.** A small Python script that
  emits the `.docx` makes character counts, DOI sweeps, and paragraph-length
  comparisons mechanical, and makes revision rounds cheap. Note that Word holds
  an exclusive lock — a `PermissionError` on write means the user has the file
  open, so ask rather than retry.

---

## Editing a live manuscript safely

Two destructive incidents in this project, one of them pushed to Overleaf,
both caused by the same mistake.

- **Never use a cross-line or non-greedy regex to delete a span of a
  manuscript.** `re.search(r'(?s)A.*?B')` will happily match from a caption in
  Section 3 to an unrelated line in the contributions list 40,000 characters
  away. One such edit removed 4,794 words; another removed the whole
  contributions block and produced 34 LaTeX errors and 94 undefined references.
- **Match exact, complete strings** and assert the match count is 1 before
  writing. If the text you want to remove is not uniquely identifiable as an
  exact string, anchor by line numbers instead.
- **Check the size delta before writing.** A deletion that removes far more
  characters than the text you intended is the signal; catch it in the script,
  not in the compiled PDF.
- **Compile and count before pushing.** Page count, error count, undefined
  references, float count. A push is the point of no return on Overleaf, which
  disallows `--force`.
- **Recovery is `git checkout <sha> -- main.tex`.** Identify the last good
  commit first; do not attempt to reconstruct deleted prose from memory.
- **Assert the match count before every write, and let the assert be the
  backstop.** `assert t.count(old) == 1` then replace, and for a swap
  `assert len(new) == len(old_document)` when the edit only reorders. In one
  session that single line caught three separate heredoc-mangled patches before
  any of them touched the file — the script died on the assert instead of
  writing a half-applied edit. For `.docx`, assert the paragraph has one run
  before setting its text, or the edit silently drops the paragraph's runs.
- **Never pass LaTeX through a shell heredoc.** On Git Bash for Windows a
  quoted heredoc still eats backslash escapes inside the Python string it
  carries, so `\bibliography` arrives as a literal backspace plus
  `ibliography` and `\times` as a tab plus `imes`. The file then compiles
  wrong, or silently loses a command, and the corruption is invisible in a
  normal editor. Write the script to a file with the Write tool and run it by
  path. After any such edit, sweep for control characters:
  `python -c "import io;t=io.open(p,encoding='utf-8').read();print({k:t.count(chr(k)) for k in (8,9,11,12,13) if t.count(chr(k))})"`.
- **`grep -c "======="` counts your own section rules.** When checking for
  merge-conflict markers, anchor them: `grep -c '^<<<<<<<\|^>>>>>>>'`. A bare
  `=======` matches every `%========` separator and will make a clean file look
  conflicted.

**Standing verification scripts worth keeping in the scratchpad**, all of which
paid for themselves on this pair of papers:

| Script | What it checks |
|---|---|
| n-gram overlap | shared ≥ 9-word runs between two of the user's own manuscripts |
| numbers cross-check | every recurring numeric constant, across abstract, body, tables, captions and conclusion |
| label/ref integrity | undefined `\ref`, unused `\label`, orphan bib keys, uncited entries |
| DOI verification | each bib entry and each response-letter citation against Crossref, fields included |
| caption vs artefact | `pdftotext` of every figure PDF, compared with its caption |
| float layout report | which floats land on which page, and how much text each page carries |
| terminology sweep | a renamed concept, checked in prose **and** captions **and** figure images |

---

## Sizing floats from measurement, not from taste

"Do not let anything run past the margin, do not make anything unreadable,
do not waste space" is a solvable problem with three numbers, not a matter of
judgement. Measure, then set the width.

**Get the two column widths from the log**, not from memory: `grep -o
"textwidth=[0-9.]*\|textheight=[0-9.]*" main.log`. For Elsevier `cas-dc` on
A4 they are a text width of about 494 pt, a single column of about 242 pt and
a text height of about 689 pt.

**Compute the on-page scale for every figure.** For each `\includegraphics`,
read the artefact's native size with `pdfinfo`, multiply the available width
(494 pt in `figure*`, 242 pt in `figure`) by the `\linewidth` fraction, and
divide by the native width. Then apply this rule:

| On-page scale | Meaning | Action |
|---|---|---|
| below ~0.72 | the figure's own text shrinks below legibility | widen it, move it to `figure*`, or split the content |
| 0.85 – 1.05 | the figure prints at the size it was drawn for | leave it |
| above ~1.15 | its text is now larger than the body text | regenerate at the target width, or reduce the fraction |

**Choose the environment from the aspect ratio, then override for label
density.** Wider than about 1.6 belongs in `figure*`; taller than about 1.0
belongs in a single-column `figure`. The exception is a chart whose *labels*
need width even though its shape is tall: a horizontal bar chart over forty
named variables has an aspect near 0.7 but is illegible at 242 pt, so it goes
in `figure*` at whatever fraction keeps its height under the text height. Work
that fraction out rather than guessing: `frac = (text_height - caption) x
native_width / (native_height x column_width)`.

**Regenerate derived figures at their exact on-page width.** When you plot a
figure yourself, `bbox_inches="tight"` makes the saved size differ from
`figsize`, sometimes by 20 %, because it includes legends and labels drawn
outside the axes. Save, run `pdfinfo`, and adjust `figsize` until the native
width lands on 242 pt or 494 pt. Then `width=\linewidth` gives a scale of
1.0 and the figure's fonts match the body.

**Overfull boxes name the real problems.** `Overfull \hbox (N pt too wide)`
with N above about 20 is content past the margin and must be fixed; the line
number in the message points at it.

- A single-column `table` whose rows overflow becomes `table*`. This is the
  most common cause of a 40–60 pt overfull box and the log finds it instantly.
- Unbreakable inline math in theorem text (an italic `\begin{proposition}`
  body containing `$g(x_S)h(x_T)$` or `$\varphi(\|x_S\|)$`) produces
  overfulls of 5–20 pt. Promote the result to a display equation, and set
  `\emergencystretch=1.5em` in the preamble so TeX stretches interword space
  instead of pushing the last atom past the edge.

**Check the class's own artefacts before chasing one.** A large overfull
reported "detected at line N" where N is `\maketitle` is usually the document
class's title block, not your text. Confirm by grepping the sibling papers'
logs for the identical value; `cas-dc` reports exactly `123.62721pt` for every
manuscript in this portfolio. Do not spend effort on it.

**Read page occupancy, not intuition, before declaring a layout wasteful.**
`pdftotext -layout` per page, counting words and the floats present, tells you
which pages are genuinely sparse. A page holding a 620 pt figure is not
wasteful; a page holding two small figures and 200 words is. And remember that
the word count of a figure-heavy page includes the figure's own axis labels.

**Measure the whitespace itself, by rendering.** Word counts mislead on a
figure page. Render each page (`pdftoppm -r 50 -gray -png`), take the fraction
of rows carrying any ink between the first and last inked row, and report every
contiguous blank band over about 30 pt. That gives one number per page and the
position of each hole, so 我觉得有的地方留白太多 becomes "pages 18 and 19 are
at 66 % and 53 % with holes of 98, 144 and 84 pt". A text page in `cas-dc`
scores 90–95 %, a page mixing text and floats 80–88 %, and anything under about
70 % is worth opening. A table-heavy page scores low on this metric and is
perfectly fine; look at the render before acting on the number.

**Float parameters do not rescue a float-saturated document.** Measured on a
20-page manuscript with 18 figures, 6 tables and an algorithm: raising
`dbltopnumber` 2→4, `dbltopfraction` 0.85→0.98, `textfraction` 0.07→0.02 and
both float-page fractions to 0.9 moved the mean ink from 79 % to 78 % and did
not move a single page. Try it once to have the number, then stop; the
remaining levers are the figures themselves.

**The one placement knob that does pay is `topnumber`.** With the default (4)
LaTeX stacks every single-column float at the top of the *first* column, which
on the last reference page left two figures in column one and five lines of
references in column two, the rest of it blank — the "bottom-right is empty"
complaint. `\setcounter{topnumber}{1}` gives each column one top float, the
text flows around both, and that page went 66 %→79 % while two earlier pages
gained 14 and 4 points. Re-measure the whole document afterwards, because the
tail redistributes.

**Know when the arithmetic says stop.** When the running text ends several
pages before the figure queue drains, the remainder becomes float pages and no
placement setting can fill them: four wide-short figures totalling 970 pt of
content over two 689 pt pages cannot exceed 71 % however they are arranged. At
that point say so with the numbers and give the user the two content-level
choices — merge or drop figures, or re-export the wide-short ones with their
panels stacked so each is twice as tall — rather than continuing to shuffle
floats. Both are the user's call.

**Figures are numbered in the order the text first cites them, and this is
checkable.** Extract each `\label{fig:…}` in declaration order, then the line of
its first `\ref` *outside* any float body, and compare the two sequences. Two
pairs were reversed in one manuscript, both invisible on a read-through because
the citing sentence named them in the correct order. Fix by swapping the float
blocks, never the prose: swapping the blocks moved exactly zero characters of
text, which the script asserted. Then confirm no figure now appears on a page
earlier than its first mention.

**Crop unwanted in-image text with `trim`/`clip` before asking for a redraw.**
Find the offending line's bounding box with PyMuPDF (`page.get_text("dict")`),
take the lowest content above it, and trim from the page edge to a point
between the two — `trim=0 20 0 0,clip` removed a caveat line sitting at
y=379.6–388.3 of a 394 pt graphic whose axis titles ended at 368.6. The figure
loses only the trimmed height on the page. Sweep the other figure files for the
same class of text while you are there (`descriptive`, `orthogonal`, `R²`,
`explained variance`, `standard error`, `Monte`, `SNR`), and check before
cutting whether the body or the caption depends on it — a paired standard error
defined in the methodology is method, not a weakness.

---

## Git / Overleaf workflow tips (if user uses Overleaf)

- **Don't commit build artifacts** (`.aux`, `.log`, `.synctex`, `.pdf`). Only the source files (`.tex`, `.bib`, figures, tables).
- **Don't commit tooling state** (`.claude/`, `.vscode/`, etc.) unless explicitly asked.
- **Overleaf disallows `--force` push.** When divergence happens: `pull --rebase`. Conflict resolution heuristic: prefer the remote side for author/metadata changes (the human editing on Overleaf web is the source of truth for those), prefer the local side for content rewrites (the local working copy is the source of truth for those).
- **HTTP/2 stream-reset errors on push** are common with Overleaf on Windows. Use HTTP/1.1 to avoid them: `git -c http.version=HTTP/1.1 -c http.postBuffer=524288000 push origin master`.
- **Never force-push without explicit user confirmation** — co-author / author-list changes on the Overleaf web side are easy to wipe out by force-push.

---

## Quick start prompt (paste at the start of a new session for a different paper)

> I'm writing an academic journal paper and want you to follow my established style preferences. Please load `~/.claude/skills/academic-paper-writing/SKILL.md` and apply it. I will supply one or more reference papers (likely named `imitate.tex` or similar) — before writing or rewriting any section, read those references and match their sentence patterns. Don't invent content — imitate the reference. Don't overclaim — verify every number against the data tables and check borderline cases. Don't use em-dashes between sentences. Frame the method as an innovation, not a "replacement". Use 3 highlights, 3–4 contributions (abstract claims, no specific numbers), and 3–4 research questions. Always verify that what the contributions claim is actually proven in the body (proposition vs. remark distinction matters). When I say "push", just commit the source files and push — don't include build artefacts. If this manuscript is a companion to another paper of mine, keep the shared format but rewrite every background and related-work paragraph from a different premise, and measure the n-gram and bibliography overlap rather than estimating it. Do not include fidelity statistics, goodness-of-fit numbers, or any figure whose image text prints a weak result — omit rather than qualify, and narrow the surrounding claim so nothing asserted becomes false. Before drafting anything, give me the story, the gap, the contribution list mapped to specific tables, and the section outline, and wait for my agreement — and do not propose a framing whose premises the results do not discharge. Never write that something was not identified, not resolved, or remains unclear, and never offer a mechanism you did not measure; delete the sentence instead. Use every column of the data I give you, never derive a number the source does not contain, and never re-round or re-label it. Verify every reference you write against Crossref or arXiv before it goes into the bib or the tex; if you cannot verify a field, leave the reference out or show it to me and wait for my confirmation. Never put an unconfirmed reference into the paper.

---

## Corrections from the MarineMamba round (Ocean Engineering, September 2026)

Every item below was a correction the user gave on a live draft, or a decision they made when asked. Apply them by default on the next paper.

### Introduction

- **No section cross-references in the Introduction except the organisation paragraph.** `Section~\ref{sec:formulation} states the dependence exactly` at the end of a motivation paragraph was struck (用户: 除了最后一段，我不喜欢在其他段落写这种 section 的内容). Figure~1 may be cited in the proposal paragraph; sections may not.
- **No results of this paper in Introduction body paragraphs.** `the results of this paper show that the window alone does not: an attention encoder ... ranks below the current-state policy` was struck (这是 introduction 你不能写 results 的东西). Argue the point from structure or literature instead (`a window costs time, memory, and parameters at every step and returns only what the encoder can extract`). Results belong in Abstract, Contributions, Experiments, Conclusion.
- **Sentence length is policed.** A 70-word sentence with three subclauses was flagged (会不会太长). Keep sentences under about 45 words; split cost arguments into one sentence per property.
- **The gap sentence is a checkable literature statement, not a summary flourish.** `None of this has reached underwater control` was rejected as unacademic; `Selective state-space encoders have not yet been applied to the control of underwater vehicles` replaced it. The test: could the related-work table be pointed at to defend the sentence word for word?
- **Cite the paradigm you argue against, and only with papers that say what you attribute to them.** When the Introduction argues that attention is quadratic in the window, cite the original Transformer paper (its complexity table) and a verified survey, not a paper that merely uses attention. When it says attention is the default context encoder in RL, cite the RL papers that do exactly that (GTrXL, Decision Transformer, DTQN).

### Abstract

- **Percentages as `\%`, never the word `percent`, in the abstract.**
- **Aggregate claims only; no single-scenario numbers.** `on the BlueROV helix its RMSE is 24% below ... and its completion rate 44% against 11` was removed by the user. Name the metric family and the count over all combinations (`the lowest tracking RMSE on more combinations than either baseline`) rather than one cell of one table.
- **The results sentences should still name the metrics that carry the advantage** (tracking RMSE, completion, post-event error, survival, smoothness), not only ranks and counts; the user asked for this explicitly (得具体点一下，比如效果特别好的那些指标).

### Title

The title went through six rounds. What settled it:

- `history-conditioned` is RL jargon and was rejected for an ocean-engineering venue.
- `efficient` was rejected: unfalsifiable, and in Ocean Engineering `efficient control` reads as energy efficiency, which the paper does not claim (the energy proxies favoured the baseline).
- `linear-time` next to `control` was rejected: control readers read it as linear (time-invariant) control. `linear-complexity` survived because `complexity` marks it as a computational property and Proposition~1 backs it.
- A `via ... modelling of ...` tail was rejected; the user did not want the object of the modelling spelled out.
- The portfolio pattern `NAME: <what> with/through <mechanism>` (MarineDreamer, LocoMamba) is the default shape; the settled form here was `MarineMamba: Selective State-Space Reinforcement Learning for Linear-Complexity Control of Unmanned Underwater Vehicles`.

### Venue reframing (Ocean Engineering)

- Open on vehicle operation (survey, inspection, intervention), not on civil infrastructure; keywords name the task (`Trajectory Tracking`) and the deployment (`Embedded Deployment`).
- Put the Fossen rigid-body model and the first-order thruster response as numbered equations in Problem Formulation, and say where each unobserved quantity (flow, payload, thruster fault) enters them. Rename the tilt symbol if it collides with the generalised force `\tau`.
- Order the experiments tracking → disturbances → computational and onboard cost → design study; RQ numbering follows.
- Replace ML wording: zero-shot protocol → disturbance protocol; hidden dynamics → unseen dynamics; observation corruption / POMDP → sensor corruption; observation noise / frame hold / observation delay → measurement noise / hold / delay. Keep `flow` for the water current when `current-state policy` is in the paper, and say once that the flow is the platform's model of an ocean current.

### Figures

- **One palette for the whole paper, high contrast, and Ours stays blue.** Settled: PPO vermillion `#D55E00` dashed, attention baseline green `#009E73` dash-dot, Ours `#0F4D92` solid, identical legend order in every figure.
- **Fonts must look identical across figures, and the fix is width normalisation, not font size.** The user noticed axis labels of different sizes. Cause: PDFs saved at different native widths are scaled by different factors on the page. Save each figure, measure its width with PyMuPDF, rescale the canvas until the tight-cropped PDF is exactly 494 pt (`figure*`) or 242 pt (`figure`), and never override tick or title sizes per figure.
- **Multi-panel PDFs with short in-image panel labels (`Task / Vehicle`) and no overall in-image title.** The user asked whether to strip titles or split into LaTeX subfigures; the answer given and accepted was panel labels only.
- **Figure retention rule (user's decision): drop a figure only if Ours is the worst policy on it; keep it when Ours is best or second.** Under this rule all eight per-family disturbance figures stayed.
- **One figure per ablation family, each with its own paragraph**, not one combined grid (各种消融要单独画图和写文字). Upper row: mean error against time after the event at each level; lower row: the ranked quantities against the level. Add one summary figure for the smoothness axis across every condition.
- **Every combination must appear.** The user noticed one missing training-curve panel (TrackSpiral / BlueROV Heavy) and a suspected missing heat-map row within minutes. Assert the panel count in the plotting script.
- **Qualitative trajectory figures may be restricted to the vehicle on which the policies visibly separate**, stated as such in the body, while the quantitative figure keeps every combination.
- **Crop a photograph to its subject** (`trim=l b r t,clip`, values in px at 72 dpi for a JPEG without a dpi tag); the user asked for it when the board photo carried white space.

### Tables

- **Shade the best cell and add a `Best (of N)` row** to every per-combination table (`\cellcolor[HTML]{DCE9F5}` plus bold; `\usepackage{colortbl}`). The user asked how to make Ours' advantage visible at a glance; this was the accepted answer.
- **A study whose question is encoder-against-encoder compares only those two policies.** The user removed the current-state baseline from the disturbance table because that study asks whether the SSM reads the window better than attention. Apply the same restriction to that section's figures and text, rebuild the paired exclusions over the two policies, and state the scoping in Evaluation Setup ("compare the two policies that read the same window, so that any difference after an event is attributable to the encoder alone").
- **Drop a column on which Ours is marginally worse when the section's claim survives without it** (the second-difference RMS in the disturbance section, where attention was lower on 13 of 24 by hundredths). Keep the metric wherever Ours wins it.

### Data hygiene learned the hard way

- **Paired-seed exclusions are recomputed over the policies actually compared.** When a baseline is dropped, the union of flagged seeds changes; validate the flagging rule against the stored per-policy flags before trusting the recomputation.
- **A plot-data bundle must prove it reproduces the source.** The accepted bundle carried SHA-256 equality for copied curves and an exact-replay audit (every metric delta 0.0) for the trajectories; check both before drawing from it.
- **Missing data has a location, not a workaround.** When a curve was absent, the useful answer was the server path of the run whose log was never copied, not a substitute figure.
- **Hardware descriptions copy the previous paper.** The board model was not in the data; the user's instruction was to keep it consistent with the companion paper (Orin NX, JetPack 6.2, L4T 36.4.3). Red-marking it was accepted as the interim, consistency as the resolution.

### Consistency sweep before hand-off (learned on the same round)

- **Round from full precision, never from an already-rounded print-out.** Three per-level values in the disturbance paragraphs were off by one in the last digit because 4-dp values were re-rounded to 3 dp (0.29550 became 0.296). Print numbers for prose at the precision they will appear, straight from the JSON.
- **One symbol, one meaning, across the whole manuscript.** A control paper that also defines a state-space block collides on `C`, `D` (Coriolis/damping vs. SSM output/skip), `g` (restoring force vs. gate branch), `u` (throttle vs. SSM signal), `e` (tracking error, termination flag, body axes), `d` (token width vs. distance), `\ell` (block index, log-std, Huber loss) and `\phi` (critic parameters vs. an elapsed-time feature). Give the vehicle-model terms a subscript (`\mathbf{M}_{\mathrm{v}}`), keep the ML-standard letters for the block that the framework figure labels, and write features such as the elapsed fraction as the expression itself (`t/T_{\max}`).
- **Every quantitative statement about a figure is recomputed from the step data**, not read off the plot: "below 0.15 m for the first three seconds where the other two exceed it within the first" was true for one baseline and false for the other.
- **Two panels that look identical need a stated reason, not a redraw.** A helix reference whose descent over the horizon is 0.09 m is indistinguishable from a circle at panel scale; say so in the body when the reader will ask.

### Reference verification workflow that actually ran

- Scripted sweep, one record per entry: Crossref by DOI, else Crossref bibliographic query with title similarity above 0.9, else arXiv by id, else arXiv title search; GitHub API for repositories (repo exists and the cited version tag exists).
- Venues of conference papers: arXiv `comment` field first (many state "ICML 2022 camera ready" or "Published as a conference paper at ICLR 2025"), then the PMLR volume index page, the `papers.nips.cc` yearly listing, the `iclr.cc` accepted-papers page or `iclr.cc/archive`, and the AAAI library search. Semantic Scholar returns HTTP 429 after a handful of calls and DBLP serves a bot check; do not build the sweep on either.
- Normalise page ranges before comparing (`71-86` vs `71--86` produced three false mismatches); strip braces and accents from author families.
- Check the published version of every preprint: MarineGym's IROS record carried an eighth author absent from the arXiv v1 author list.
- Check every citing sentence against the record: three placements were wrong in a bibliography whose entries were all real (a terrain-mapping survey cited for a trajectory claim; a path-planning paper cited as "planning and control"; Isaac Gym cited as if the platform were built on it).
- Remove entries the text never cites.
- Report a per-entry table (source checked, field result, citation-context result) and a summary count; the user asks for the table by name.
