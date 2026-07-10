---
name: academic-paper-writing
description: Style and quality rules for drafting, revising, or polishing academic journal papers (Elsevier, IEEE, ACM, etc.) in any field. Encodes the user's writing preferences distilled from extensive iterative revision feedback. Use whenever the user is working on a `.tex` (or similar) manuscript — especially when they ask to write/rewrite/tighten Abstract, Introduction, Related Work, Methodology, Experiments, or Conclusion, when they ask to "match the style of [a reference paper they supply]", or when they ask for revision passes on prose, claims, equations, figures, or tables.
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

**Audit checklist before submitting**:
- [ ] Each bullet makes exactly one substantive claim.
- [ ] No bullet ends with "bridging the gap", "shedding light on", "paving the way", or similar filler.
- [ ] No bullet contains specific numerical values.
- [ ] No bullet duplicates a claim made in another bullet.
- [ ] Each theoretical claim corresponds to a `\begin{proposition}` (not `\begin{remark}`) in the body.
- [ ] Each "first-claim" is hedged with "to the best of our knowledge".

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
- **Captions: 1–2 sentences max** in the reference style. No trailing "(a)…; (b)…; (c)…. The scene contains X classes captured over..." fluff. Further caption hygiene rules:
  - **No formula-style cross notation** (`Benchmark $\times$ baseline heat-map`, `Method $\times$ Dataset matrix`). It reads as computational/non-academic. Use academic prose instead: `Heat-map of overall accuracy across the [N] baselines and the [M] benchmarks.`
  - **No result claims in captions.** Sentences like `MFM (red) defines the Pareto frontier of every panel.` are editorial conclusions and belong in the body. The caption should describe *what is shown*, not what to conclude from it.
  - **No re-definition of abbreviations that are already defined in the body.** Once OA / AA / Cohen's $\kappa$ etc. are defined in the Evaluation Setup, downstream tables and figures use the abbreviations directly. Don't re-spell `overall accuracy (OA)` in every table caption.
  - **No back-pointers that are already implicit.** `Class definitions are listed in Table~\ref{...}` at the tail of a dataset-figure caption is filler — the reader will find it. Drop unless the pointer is non-obvious (e.g., a definition is two sections away).
  - **Prefer "Overview" over "Overall architecture"** for the framework figure (matches the reference papers; shorter, less generic).
  - **Use "Grouped bar chart of …" / "Heat-map of …" / "Radar of …"** as the noun phrase head, not the truncated "Overall accuracy bar across …" which sounds incomplete.
  - **For column-meaning notes in long efficiency tables**, list inline as `\``Params''`: ...; ``FLOPs''`: ...; ``Size''`: ...` rather than as full sentences (`\``Params'' is the total parameter count, \``FLOPs'' is per single-sample forward pass, ...`). Reads as a glossary, takes a third of the space.
- **Verify referenced figure files exist on disk** before adding `\includegraphics{path}`.
- **Footnotes in the abstract are unreliable in Elsevier `cas-dc`/`cas-sc`.** A `\footnote{}` placed in the abstract often does not render. To surface a code repository and a demo video, put them as plain inline `\url{}`s in the last sentence of the abstract ("Source code is available at \url{...} and a demonstration video at \url{...}.") rather than as a footnote. `hyperref` is already loaded by `cas-dc`, so the URLs hyperlink without extra preamble.
- **Avoid inline math that cannot line-break.** A long inline expression with an unbreakable subscript (e.g., `$\{S_c\}_{c\in\mathcal{C}\setminus\{\mathrm{Normal}\}}$`) pushes past the column edge because LaTeX will not break inside `\setminus\{...\}`. Either promote it to a display equation, or rephrase in words ("the $C-1$ non-normal classes of $\mathcal{C}$"). Sweep with a regex for inline `$...$` longer than ~60 chars.

### Tables

- **`table*` for wide tables** (per-class results, efficiency tables). Placement specifier follows the same user-preference rule as figures (see Figures above): either strip all, or put `[t]` on all — match whatever the user chose for the document.
- **No vertical lines (`|`).** Use `lcccc...` not `|l|c|c|c|c|`.
- **Minimal `\hline`**: top, after header, before summary/aggregate rows, bottom. No `\hline` between every data row.
- **Top-3 cell coloring** for per-class accuracy tables: `\cellcolor[HTML]{F4A7A7}` (1st red), `F9CDA0` (2nd orange), `FFF3A3` (3rd yellow). This matches a common Elsevier convention.
- **Efficiency / comparison tables**: 2 rows per condition (baseline + Ours), use `\multirow{2}{*}{Condition}`.

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

Before adding any `\cite{key}`:
1. **Verify the key exists in the bib file.**
2. **Spot-check suspicious entries**: future year, "in press", "and others" in author list, vague journal — web-search to confirm the paper actually exists.
3. If a cited paper turns out not to exist, **remove the cite or replace with a real one**.
4. Never invent a citation just to support a claim. If no real cite supports the claim, soften the claim or remove it.
5. When the bib file has a comment like "all references verified via web search", still spot-check the most recent ones — those are most likely to be hallucinated.

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
- **When the user gives short corrective feedback** (e.g., "don't use `---` between sentences", "缩写", "no replacement"): interpret broadly and sweep the entire document, not just the cited location.
- **When the user says "push"**: skip TodoWrite (single-step task), check divergence, commit only intentional source changes, push (with git workflow tips below if applicable).
- **Always check that what the contribution claims, the body actually proves.** Especially: don't list a remark or informal observation as a "result" or "theorem".
- **When renaming a section or label**: sweep all `\ref{}` and prose mentions for stale references.
- **When deleting unused content** (datasets, methods, ablations the paper doesn't actually use): delete the table, the figure, AND the supporting preamble (color definitions, custom macros). Don't leave half-removed artefacts.

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

---

## Git / Overleaf workflow tips (if user uses Overleaf)

- **Don't commit build artifacts** (`.aux`, `.log`, `.synctex`, `.pdf`). Only the source files (`.tex`, `.bib`, figures, tables).
- **Don't commit tooling state** (`.claude/`, `.vscode/`, etc.) unless explicitly asked.
- **Overleaf disallows `--force` push.** When divergence happens: `pull --rebase`. Conflict resolution heuristic: prefer the remote side for author/metadata changes (the human editing on Overleaf web is the source of truth for those), prefer the local side for content rewrites (the local working copy is the source of truth for those).
- **HTTP/2 stream-reset errors on push** are common with Overleaf on Windows. Use HTTP/1.1 to avoid them: `git -c http.version=HTTP/1.1 -c http.postBuffer=524288000 push origin master`.
- **Never force-push without explicit user confirmation** — co-author / author-list changes on the Overleaf web side are easy to wipe out by force-push.

---

## Quick start prompt (paste at the start of a new session for a different paper)

> I'm writing an academic journal paper and want you to follow my established style preferences. Please load `~/.claude/skills/academic-paper-writing/SKILL.md` and apply it. I will supply one or more reference papers (likely named `imitate.tex` or similar) — before writing or rewriting any section, read those references and match their sentence patterns. Don't invent content — imitate the reference. Don't overclaim — verify every number against the data tables and check borderline cases. Don't use em-dashes between sentences. Frame the method as an innovation, not a "replacement". Use 3 highlights, 3–4 contributions (abstract claims, no specific numbers), and 3–4 research questions. Always verify that what the contributions claim is actually proven in the body (proposition vs. remark distinction matters). When I say "push", just commit the source files and push — don't include build artefacts.
