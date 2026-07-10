---
name: review-response
description: Drafts point-by-point rebuttal/response-to-reviewers letters for academic journal manuscripts (CACAIE, Elsevier, IEEE, etc.), in the user's established style distilled from multiple real rebuttals. Use whenever the user is writing or revising a response-to-reviewers document — a `review_response*.tex` (reviewresponse class), a CACAIE "Conscientious Reviewer form" Word file, or any "reply to comment / rebuttal / 审稿回复" task. Especially: "write the response to reviewer X", "rebut this comment", "仿照这个套路回复", "draft the rebuttal for these comments", or filling placeholder responses with real ones tied to the actual paper.
---

# Review-Response (Rebuttal) Skill

Encodes the user's house style for response-to-reviewers letters, distilled from five real rebuttals
(WSVAD/Mamba VAD, LocoMamba, SSD-Mamba2 locomotion, quadrotor imitation learning, energy-aware
manipulation RL — all for civil-infrastructure venues, mostly CACAIE / Advanced Engineering Informatics).

**Golden rule 0 — SAFETY ABOVE ALL, FOR EVERY CHANGE (the user's standing, non-negotiable requirement).**
No matter what is being edited — a blue manuscript span, black reply prose, a caption, a table cell, a
contribution heading, a single softened word — it must be **safe, non-overclaiming, and impossible for the
reviewer to re-question.** Before writing or keeping ANY sentence, ask: "can a hostile reviewer attack this
with the paper's own tables?" If yes, weaken it to exactly what the data uniformly supports, or omit it.
The user would rather say less, or nothing, than be re-challenged ("可以不写也不要被质疑"). This applies
beyond the blue text: when you blue a whole sentence (per the one-word→whole-sentence rule), re-check every
pre-existing claim it now re-highlights against the actual cells (every terrain, every metric, every
baseline) and fix latent overclaims (e.g. a blanket "fewer collisions / greater distances" that fails
against a near-stationary or single-terrain baseline) BEFORE bluing it. Reply prose is held to the same
bar: never let the black exposition assert more than the tables show, and never volunteer a self-incriminating
concession the reviewer did not already have. Golden rules 1–4 below are the mechanics; this rule is the
constraint they all serve. When the two conflict, safety wins.

**Golden rule: the response must address THIS paper.** The single most common failure is pasting
boilerplate from a different paper (wrong method names, wrong datasets, wrong modules). Before drafting,
read the actual manuscript (`.tex`) and the actual reviewer comments, and ground every sentence in the
real method, datasets, tables, equations, and section numbers. Never invent results — if you state a new
number/table, flag to the user that the value must be filled from real experiments.

**Golden rule 2 — DUAL BLUE + SYNC (mandatory, never skip).** Every revision has TWO sides that must
stay in lockstep:
1. **In the response letter**, the quoted "revised text / new table / new caption" is marked blue
   (`\textcolor{blue}{...}` or `{\color{blue} ... }`).
2. **In the manuscript itself** (`cas-dc-template.tex` or equivalent) the SAME edit must actually be made
   AND wrapped in `\textcolor{blue}{...}` / `{\color{blue} ... }` so the editor sees the change highlighted
   in the revised PDF.
A reply that promises a change but does not also edit-and-blue the manuscript is INCOMPLETE. The blue text
shown in the letter and the blue text inserted in the paper must be identical (or trivially consistent).
The manuscript already loads `xcolor`, so `\textcolor{blue}{}` works directly; for multi-line/blocks use
`{\color{blue} ... }`. After a revision round is accepted, the user typically removes the blue (reverts to
black) — so keep edits cleanly wrapped, not hand-recolored mid-sentence.
**Floats are special — put the color INSIDE the float.** A `{\color{blue} ... }` placed OUTSIDE
`\begin{table}`/`\begin{figure}` does NOT colour the float: the float's body is deferred and typeset after
the colour group has closed, so it prints black. Put `{\color{blue}` *after* `\begin{table}\centering`,
wrap the `tabular`/`includegraphics` and any notes, and close `}` *before* `\end{table}`.
**The caption needs its own colour:** a surrounding `{\color{blue}}` often does NOT colour `\caption`
text (the class's `\@makecaption` resets it), so write `\caption{\textcolor{blue}{...}}` explicitly —
captions of any modified figure/table must be blue too. (Rule of thumb: every modified figure/table,
caption included, must end up actually blue in the rendered PDF — verify, don't assume the wrapper worked.)

**Golden rule 2a — BLUE-SET EQUALITY (the hard invariant).** Treat the blue text as a set. The set of all
blue spans in the response letter must EQUAL the set of all blue spans in the manuscript — **no more, no
less**, for every comment. Concretely:
- **Verbatim, not paraphrased.** When the letter quotes "the revised text reads as follows", that quote
  must be the *exact same words* as the blue span in the manuscript. Do not condense, summarise, expand,
  truncate, or reorder. (Cross-references are the only allowed difference: the manuscript's
  `\eqref{eq:x}`/`\ref{...}`/`\cite{...}` may render as plain `Equation~(6)` / `Table~3` / author–year in
  the standalone letter — same *rendered* text, so still "trivially consistent".)
- **One-word changes — blue the WHOLE sentence (user preference), identically on both sides.** Even if
  only a single word changed (e.g. `actionable interpretability`→`interpretability`), mark the ENTIRE
  sentence containing it in blue, and do so the SAME way in the manuscript and in the letter's quote, so
  the change is shown in context. Keep an unchanged trailing `\cite{}` outside the blue. The equality
  invariant still holds: whatever is blue in the letter is blue identically in the manuscript, and never
  blue a span in one file only. (Caveat: bluing a whole sentence re-highlights any pre-existing claims it
  contains, so re-run the Golden rule 3 pre-insertion check on the full sentence.)
- **No orphan blue on either side.** Every blue edit in the manuscript must be shown (verbatim) somewhere
  in the letter, and the letter must not contain any blue that is not blue in the manuscript. A blue table
  row, std value, hyperparameter, or softened word that exists in one file but not the other is a defect.
  *Sole exception:* the color-name word "blue" typeset as `\textcolor{blue}{blue}` inside a lead-in
  ("marked in \textcolor{blue}{blue} as follows:") is a typographic label, not a manuscript quote, and is
  exempt from this equality check — same convention as `cover_letter.tex`.
- **Practical check.** After editing, extract every `\textcolor{blue}{...}` / `{\color{blue} ...}` span
  from both files and diff the two sets; they must coincide. Fix any span that appears in one set only, or
  that differs in wording. A common failure is the letter showing a *shortened* or *prettier* version of
  the manuscript blue — that still counts as a mismatch.
- **Direction of fix.** If the letter's quote is shorter/longer than the manuscript blue, decide which
  wording is the intended final text, then make BOTH sides exactly that. Don't leave them merely "close".

**Golden rule 3 — DEFENSIBLE BLUE (every added sentence must survive a hostile reviewer).** The blue text
is what the reviewer scrutinises most; it must be the *least* attackable prose in the paper, not the most.
- **No claim beyond the evidence.** Before writing a blue sentence that asserts a fact about the
  experiments (e.g., "the two methods differ only in the temporal module", "X is the more influential of
  the two", "removing both is most harmful", "the gain comes from Y"), CHECK it against the actual
  tables/data/config. If the data is mixed or you cannot verify it from the manuscript, do NOT assert it —
  state only what the numbers unambiguously support (e.g., "the full model outperforms all reduced variants
  on every metric"), or flag the factual claim to the user for confirmation. A confidently wrong blue
  sentence is worse than no sentence: it hands the reviewer a new, sharper target.
- **Read the table before describing it.** "Most/least", "more influential", "monotonic", "peaks at",
  "insensitive" are quantitative claims — verify each against every cell, both datasets, both metrics.
  Ranking/superlative claims fail most often because one metric/dataset contradicts them.
- **No editorialising, defensive codas, or certainty-disclaimers.** Cut sentences like "we regard this as
  a present limitation rather than a failure mode unique to our design" or "we offer these as plausible
  contributing factors rather than a definitive cause" — they add no evidence, sound defensive, and invite
  "why mention it?". Tentativeness is already carried by hedged wording inside the explanation ("a likely
  reason", "plausibly", "may"); do NOT also append a separate disclaimer sentence saying the explanation is
  not definitive. Explain the mechanism (grounded in real components) with hedged verbs, and stop.
- **Prefer hedged, mechanism-anchored wording** ("consistent with", "observed on all three datasets")
  over bare assertions, but never use hedging to smuggle in an unsupported claim.
- **When in doubt, ask, don't invent.** Experimental-setup facts (what was held fixed, #seeds, α, which
  config is authoritative) are knowable only to the author — confirm them rather than guessing.
- **Pre-insertion check — run before EVERY blue span (the user's hard requirement).** Treat each blue
  span as the first thing a hostile reviewer will attack. Before inserting it, confirm all four: (i) it is
  *correct* and literally supported by a specific figure/table/equation/number that already exists in the
  manuscript (name which one to yourself; read the actual cells/figure, do not rely on memory); (ii) it
  does **not overclaim** beyond that evidence (no jitter / energy / smoothness / efficiency / SOTA /
  causal-mechanism wording unless a metric in the paper actually shows it; no "first"/"principled"/
  "guarantee"); (iii) it opens **no new hook** the reviewer can re-attack or use to escalate; (iv) any
  experimental-setup fact it depends on has been confirmed with the user, not guessed. If a span fails any
  test, weaken it to exactly what the data unambiguously supports, or drop it. Re-run this check whenever a
  one-word edit is widened to a whole-sentence blue (§Golden rule 2a), because bluing the whole sentence
  re-highlights pre-existing claims in it — verify those are defensible too, or fix/soften them. A
  confidently wrong blue sentence is worse than no sentence.

**Golden rule 4 — TWO REGISTERS: the response prose EXPLAINS in detail; the blue quote is the concise
INSERT.** This is how every reference rebuttal is built (e.g., the SSD-Mamba2 letter: several paragraphs of
detailed reasoning, then a short "the revised text reads as follows … in blue" snippet). Each reply has two
distinct registers that must NOT be identical:
- **The response prose** (black body of the reply) is the *fuller, more specific* exposition — it spells
  out the mechanism, the reasoning, the experimental protocol, or the numbers in more depth, to persuade
  the reviewer. This is where detail lives.
- **The blue quote** is the *trimmed, paper-ready* sentence(s)/table that is actually inserted into the
  manuscript and carried in the revised PDF. It stays concise.
- **Do not let the prose paragraph be a near-copy of the blue quote.** If they are word-for-word the same,
  the reply is under-developed: expand the prose into a genuine explanation and keep the blue concise.
- **The prose must remain bounded by the blue / manuscript (Golden rule 3 still holds).** It elaborates the
  *same* points in more depth — it does NOT overclaim and does NOT introduce a substantive claim that is
  absent from the blue/manuscript. Legitimate elaboration = explaining *how/why* a mechanism the blue
  already names operates (e.g., what the sparsity/smoothness losses each penalise, how top-$K$ MIL gates
  supervision), drawn from the method's own definitions; illegitimate = a new cause, a new result, or a
  stronger claim than the paper supports. Keep it hedged ("a likely reason", "plausibly", "may").

---

## 0. Two output formats

**(a) `.tex` — `reviewresponse` document class.** Structure:
```
\reviewer
\begin{generalcomment} ... reviewer's overall summary ... \end{generalcomment}
\begin{revresponse}[One-line italic lead, optional] ... overview reply ... \end{revresponse}
\begin{revcomment} ... reviewer comment 1 ... \end{revcomment}
\begin{revresponse} ... reply 1 ... \end{revresponse}
...
```
New text destined for the manuscript is wrapped in `\textcolor{blue}{...}` (inline) or
`{\color{blue} ... }` (blocks, incl. tables/figures). Repeat each `\reviewer` block per reviewer.

**(b) `.docx` — CACAIE "Conscientious Reviewer form."** The reviewer's text is followed by a line
`Response:` then the reply. After the prose reply, **re-paste the exact sentence(s) to be inserted into
the manuscript** as a standalone paragraph (this represents the blue-highlighted edit). Leave the form's
checkboxes/Yes-No grid untouched; only add `Response:` blocks under summary fields and under each
numbered specific comment.

Match whichever format the target file already uses.

---

## 1. The six-beat reply template (use for almost every comment)

1. **Thank + validate.** "We sincerely thank you for this insightful / constructive / valuable
   comment…" (second person — see §3) Name what is good about the comment.
2. **Agree / concede (and apologize if it's a real defect).** "We fully agree that…" / "We apologize for
   this oversight…" **Never argue defensively.** Concede the point, then reframe. **Reserve "fully agree"
   for genuine defects and factual/cosmetic points; never "fully agree" with (or even echo) a criticism of
   the work's core value (novelty, significance, "just a combination of existing parts").** Restating "the
   method is not new" or "it is a combination of existing modules", even to refute it, foregrounds the
   weakness and hands the reviewer a quotable admission. There, concede only the concrete harmless
   sub-point (e.g., soften or remove "first") and pivot to strengths (§2, §3).
3. **Clarify intent & rationale.** Explain what was meant / why the design is as it is. Demote genuine
   mistakes to "this was not stated clearly enough" rather than "we were wrong."
4. **State the concrete change.** Name it precisely: "we have added Section~X.X / Table~Y / Eq.~(Z)",
   "we revised the caption / title / wording", "we added a future-work statement in the Conclusion."
5. **Show the artifact — with a VARIED lead-in.** Introduce the blue quote with a one-line lead-in
   *tailored to what changed and where*, then paste the revised text / new table / subsection / caption,
   **marked in blue**, with explicit Section/Table/Equation numbers. Do **not** reuse one identical
   lead-in sentence for every comment (the #1 monotony tell — the user explicitly objects to repeating
   the same "The revised sentences have been added and marked in blue as follows:" each time). Vary it to
   name the specific edit, LocoMamba-style:
   - "The revised sentences have been added and marked in \textcolor{blue}{blue} as follows:"
   - "Accordingly, we have added a short note in the Conclusion, marked in \textcolor{blue}{blue} as follows:"
   - "We have added a concise summary of this ablation in the revised manuscript, marked in \textcolor{blue}{blue} as follows:"
   - "The newly added clarification has been highlighted in \textcolor{blue}{blue} as follows:"
   - "The following sentence has been added in the revised manuscript, in \textcolor{blue}{blue}:"
   The word **blue** inside the lead-in is itself typeset blue (`\textcolor{blue}{blue}`), exactly as in
   the reference letters — the lead-in line is black except for that one blue word.
6. **STOP at the blue artifact — no closing thanks.** The reply normally ENDS at the blue-marked
   inserted text (beat 5). Following the LocoMamba house format, do **not** append an "Again, we thank
   you for this comment… we hope this adequately addresses your concern" coda after the blue — it is
   redundant filler. The opening thank-you (beat 1) already carries the courtesy. The single warm
   closing line belongs only in the reviewer-level **overview** reply (§3), not after every item.
   *Exception:* a reply with NO manuscript edit — a pure clarification/question answer or a graceful "we
   keep the design" decline (§2) — has no blue to end on; it ends naturally on the explanation and may
   carry one brief closing gratitude. The "no coda" rule targets only replies that DO insert blue.

Keep beats 1–2 short; spend the length on 3–5; when there is a blue insert, let it be the last thing in
the reply. Short cosmetic fixes can compress 1–5 into 2–3 sentences, still ending on the blue edit.

---

## 2. Strategy by comment type (the core decision table)

| Comment type | How to respond |
|---|---|
| **Cosmetic** (punctuation, figure caption, stray symbol like a `†`, naming inconsistency, citation format, missing α/hyperparameter value) | Just do it. Paste the corrected text in blue, brief thanks. Don't over-explain. |
| **"Add an experiment / table"** (efficiency comparison, parameter breakdown, ablation, sensitivity, statistical variance over runs) | **Do it.** Add a new Section + a real table, plus 1–2 paragraphs of interpretation. Recurring framing: *"the gains are not from a larger model / more FLOPs, but from the proposed mechanism."* Flag that numbers must come from real runs. |
| **"Comparison is unfair"** (only swap the module, keep the rest identical) | Emphasize a **controlled comparison**: same encoders, same training protocol, same hyperparameters/epochs, only the target module varies; attach a parameter/resource table showing comparable scale. |
| **"Just a combination of existing parts / 'first' is overstated"** | Do the one harmless concrete thing (soften or **remove** "first"), then stop dwelling on the weakness. **Do NOT echo or concede the novelty criticism** (no "we acknowledge the components are established / it is not fundamentally new / a mere assembly"); restating it foregrounds it. Instead pivot hard to the *substance*: the purpose-built mechanisms, how the parts are co-designed to solve the problem, the measured gains, and what the framework delivers that prior methods do not (positive differentiation grounded in your comparison table). Push strengths at length; name the alleged weakness as little as possible. |
| **"Need real-world / hardware / streaming validation"** | **Scope defense + future work.** Honestly state it is beyond the current scope (resource/hardware constraints), defend the value of the controlled/simulation/benchmark study, then add a blue future-work sentence in the Conclusion. |
| **"Language too strong / term misused"** (`principled`, `first framework`, `deployment-oriented`, "stability analysis" when there is none) | Concede and **down-tone**: replace with measured wording (e.g., "empirical robustness", "training stability", "competitive/efficient"). Distinguish empirical from formal/theoretical claims. Sweep all of Abstract/Intro/Conclusion for the same word. |
| **"Theory rests on strong assumptions / propositions are trivial"** | Acknowledge the assumptions are idealized; argue they define the regime / give intuition; where possible, connect each result to a concrete design choice; soften any over-claimed theorem language; offer to move marginal results to a remark. |
| **Defensible design you want to keep** (e.g., "merge the contributions", "use a different module") | Validate fully, explain why the current choice is retained (consistency with RQ structure / scope), and **promise to adopt the suggestion in future work** — decline gracefully, never bluntly. Usually has **no blue edit**: it justifies and ends on a brief gratitude. |
| **Pure clarification / question** (notation, "where is $X$ used?", "does $s_t$ mean $o_t$?") | Answer directly and precisely; if it was merely unclear, fix the wording. Often needs **no manuscript change** — explain and stop, no blue. Add a blue edit only if you actually changed the paper. |
| **CACAIE-specific asks** | Cite a few CACAIE papers, give full author lists in references, remove punctuation after equations, write out hyperparameter/schedule values explicitly for reproducibility. |

---

## 3. Tone & phrasing conventions

- **Address the reviewer in the second person ("you/your"), not the third person ("the reviewer").**
  House style speaks *to* the reviewer: "We sincerely thank **you** for…", "Following **your** suggestion…",
  "Again, we thank **you** for this comment." Do NOT write "We thank the reviewer / the reviewer's
  suggestion" in the replies. (Exception: when a reply to the *editor* refers to the reviewers as a group,
  "the reviewers" stays third-person and plural.) When sweeping a draft, protect the plural "the reviewers"
  before converting singular "the reviewer"→"you" / "the reviewer's"→"your".
- **Deferential, never combative.** Even when retaining the original design, open with agreement.
- **High-frequency openers:** `We sincerely thank you for this insightful/constructive/valuable/
  thoughtful comment`; `We fully agree that…`; `We apologize for…`; `…highlighted in blue for ease of
  reference.`
- **Do NOT close each reply with thanks (LocoMamba format).** A per-comment reply that makes a manuscript
  edit ENDS on its blue-marked edit — no "Again, we thank you for this comment / we hope this addresses
  your concern" coda after the blue. Repeating "again thanks…" on every item is redundant filler the user
  explicitly does not want. The single warm closing line belongs only in the reviewer-level **overview**
  reply (and in no-blue clarification/decline replies, which have no blue to end on — see below).
- **Vary the lead-in to the blue quote (see §1 beat 5).** Tailor each lead-in to the specific edit; never
  paste the same "marked in blue as follows" sentence verbatim for every comment. The word "blue" in that
  lead-in is itself typeset blue: `marked in \textcolor{blue}{blue} as follows:`.
- **Group all blue edits at the END of each reply, with NO prose between them (user preference).** Write
  the full explanatory prose first; then one lead-in sentence that names where each edit goes (e.g. "in the
  Introduction, Section~5.6, and the Conclusion"); then the blue quotes back-to-back, ordered by order of
  appearance in the manuscript (or the order discussed in the prose). Do NOT interleave prose paragraphs
  between the individual blue quotes. Do NOT prefix each quote with a bold location label like
  `\textbf{Introduction.}` — the user finds these unnecessary; the locations are already named in the
  lead-in. (If a locator ever is kept, it too must be blue.)
- **NO inline sub-headings / labelled-list style ANYWHERE in a reply — this also covers the black PROSE,
  not only the blue quotes (hard user requirement).** Do NOT open paragraphs with `\emph{The scientific
  question.}`, `\textbf{Core advancement.}`, `\emph{Main contributions.}`, `\paragraph{...}`, bullet/`\item`
  lists, or any run-in bold/italic "topic label." Even when the user asks for a reply that answers several
  named points in order (e.g. "scientific question + core advancement + contributions"), write it as
  **flowing connected prose**: carry the reader from one point to the next with natural transition phrases
  ("The scientific question we set out to answer …", "The core advancement relative to prior work follows
  from …", "On the main contributions and their relative weight, …"), never with a labelled heading. The
  beats must be discernible from the prose itself, not from typographic labels. (The user has flagged this
  repeatedly; treat any `\emph{Label.}`/`\textbf{Label.}` run-in at a paragraph start as a defect.)
- **Cross-reference numbers must match the manuscript — HARDCODE them in the letter, never `\ref`.** Any
  Section / Table / Figure / Equation number cited in the letter must equal the *actual* number in the
  revised manuscript. The response letter is a SEPARATE document: a `\ref{...}` (and `\setcounter` tricks)
  in the letter resolves to the LETTER's own local numbering, NOT the manuscript's, so it silently prints
  the wrong number. Therefore, in the letter, **write the verified manuscript number as plain text**
  (`Table~9`, `Section~5.4`, `Eq.~(26)`) — do not use `\ref`, and do not try to fix it with `\setcounter`.
  To get the real number, count the floats in `cas-dc-template.tex` in source order (figures and tables
  have separate counters) and confirm before writing it. A reproduced table/figure shown in the letter for
  the reviewer's convenience should be **unnumbered** (no `\caption`; use a bold blue title line such as
  "Table~9: ...") so it cannot collide with or contradict the cited number. (This exact mistake — letter
  `\ref` rendering 1/2/3 instead of the paper's 9/10/1 — has happened; do not repeat it.)
- **Box the cited numbers in the letter, like the paper.** The manuscript boxes `\ref` links via hyperref
  (a coloured border). The letter uses hardcoded plain numbers, so wrap each cited figure/table NUMBER in
  a matching box, e.g. define `\newcommand{\reftag}[1]{{\setlength{\fboxsep}{1pt}\setlength{\fboxrule}{0.6pt}\fcolorbox{red}{white}{#1}}}`
  and write `Table~\reftag{9}` (box only the number, not the word "Table"; a table's own caption title is
  not boxed). Apply this in both the prose and the blue spans of the letter.
- **Mirror citations.** If a blue span references the paper (a `\ref` to a table/figure/equation/section, or
  a `\cite`), the letter's copy of that span must show the SAME reference/citation with the SAME (hardcoded,
  verified) number — never drop a citation that is present in the manuscript blue.
- **Re-paste tables/figures in EVERY reply that uses them (repetition is allowed and required).** Each
  per-comment reply must be self-contained: when a reply argues from a manuscript table/figure, reproduce
  the WHOLE blue table/figure inside that reply's collection, even if the same table already appears under
  another comment. Do not shrink it to a bare "see Table~N". The same table may (and should) be re-pasted
  under several comments (R1.2, R1.3, R2.x, …); the hardcoded number stays identical to the manuscript each
  time.
- **Figure/table edits get a colored mark.** When an edit is a whole figure or table (where inline
  `\textcolor{blue}{}` on prose does not show the change), make it unmistakably blue in the revised PDF:
  put `{\color{blue}` *inside* the float (after `\centering`), wrap the body, and give the caption its own
  `\caption{\textcolor{blue}{...}}` (a surrounding colour group does not reliably colour a caption). Show
  the same artifact, blue, in the letter.
- **Reproduce the FULL artifact in the letter, never a caption stub — and show EVERY regenerated figure
  when figure quality is attacked.** When a blue span involves a table/figure, bring the ENTIRE artifact
  over verbatim (the whole `tabular` / the `\includegraphics` image) in the same float format as the
  manuscript, set the figure counter so the reproduced number matches (`\setcounter{figure}{N-1}` →
  "Figure N"), and never paste only the caption or a hand-typed pseudo-caption. When a comment criticises
  the figures wholesale (e.g. "all figures look template-generated / unclear"), the collection for THAT
  comment must reproduce *every* regenerated figure in the paper (1…N) in source order, not just the two or
  three most relevant — the breadth is the rebuttal. Each reproduced caption keeps the manuscript's exact
  text AND colour (a figure whose paper caption is black stays black in the letter; only blue-captioned
  ones are blue), preserving blue-set equality while still displaying the regenerated image as evidence.
- **Captions stay short; explanations live in the body (both files).** Keep every figure/table caption to
  a terse label. Move anything explanatory — column/symbol definitions ("``Param'': total parameters"),
  methodology notes ("scores fixed, only $q$ varied"), data-sourcing ("quoted from the original papers"),
  per-panel breakdowns ("each panel shows, top to bottom, …") — into the nearby body paragraph that first
  references the float, keeping the moved text the same colour (blue stays blue, so it remains a tracked
  revision). When you shorten a manuscript caption you MUST (i) add the removed explanation as a body
  sentence at the float's first reference, and (ii) mirror BOTH changes in every letter reproduction of
  that artifact (shortened caption + the reproduced body sentence) so Golden rule 2a still holds.
- **No swap/replacement language in BLUE (novelty-framing).** In manuscript blue text (and any letter quote
  of it), never frame the method with substitution wording — `replace`, `rather than`, `instead of`,
  `other than`, `substituted for X`. It reads as a cheap drop-in swap and concedes the "just swapped the
  encoder" criticism. Phrase positively and mechanism-first: state what the method *does* ("the selective
  state-space encoder attains linear-time sequence modeling that reduces latency…", "realises X directly
  within a linear-time recurrence"), not what it swaps out. Black reply prose may still explain the contrast
  for the reviewer (it is not in the paper), but keep the paper's blue positive. Leave pre-existing *black*
  manuscript sentences alone unless asked — the rule targets blue.
- **Most replies land on a visible change — but not all.** A reply that triggers a manuscript edit ends on
  its concrete, numbered, blue-marked artifact, and ends THERE. But pure clarifications/questions (notation,
  "where is X used?") and graceful "we keep the design" declines (§2) legitimately have NO blue edit —
  answer or justify, and stop; do NOT manufacture a blue change just to have one. These no-blue replies end
  naturally on the explanation and may carry one brief closing gratitude. "We agree" with no artifact is
  fine *only* for these no-edit cases; for everything else it is not enough.
- **On substantive challenges, be thorough — but length must stay inside the blue/paper.** For comments
  attacking novelty, theory, or fairness, a fuller multi-paragraph reply (spell out the mechanism, why the
  pieces interlock, the protocol, pointers to the relevant tables/sections) signals diligence and makes a
  reviewer less inclined to re-argue every line — this is a deliberate, legitimate tactic the user wants.
  But it is bounded by Golden rule 3: every added sentence stays within the scope of the blue edit and what
  the paper actually shows. Elaborate the *same* points in more depth; never introduce a new claim, a
  stronger claim, or anything absent from the blue/manuscript, and never invent numbers. **Long and
  grounded, never long and loose** — verbosity that overclaims hands the reviewer more targets, not fewer.
- **In blue/manuscript edits, name the concrete subject.** Write "the proposed framework / module /
  transformation", not vague self-references like "the present work" or "this work". When the user flags
  one instance, sweep both the manuscript and the letter (and keep the blue spans identical).
- **Re-revision rounds are lighter:** if the file is a 2nd-round/ReReview, replies are shorter —
  "thank you for the positive assessment + we addressed items (a)–(c)."
- **One reviewer at a time.** Open each reviewer with a warm "overview" reply to their general comment
  before the per-comment replies. **Default to a short, generic two-paragraph thanks** (this user's
  preference): (1) thank them for the careful reading and the clear/accurate summary of the framework;
  (2) thank them for the valuable, constructive comments that helped improve the manuscript, say the paper
  was revised accordingly with changes in blue, that you respond point-by-point below, and that you hope it
  now addresses their concerns, closing with thanks again. Keep it generic — do not list the framework
  components and do not preview the criticisms.
  - **Never enumerate/preview the reviewer's CRITICISMS** ("your comments concern novelty, the theory,
    fairness, and claim strength…") — that belongs in the per-comment replies and pre-commits your framing.
  - The reference letters sometimes also *echo the reviewer's summary of the work* (naming the framework
    elements) as recognition; that is an acceptable alternative, but this user preferred the leaner generic
    form — offer/echo only if asked.
  - Phrase any acknowledgement as thanking for the *accurate summary*, never as "we appreciate your clear
    understanding of …" (reads as grading the reviewer). If the general comment is a neutral paper summary
    with no praise, say "accurate summary", not "positive summary".

---

## 4. Anti-patterns (do NOT do)

- ❌ Reusing another paper's content — wrong method/dataset/module names. (This is the #1 real-world error;
  e.g., a VAD paper's rebuttal accidentally talking about quadruped PPO reward functions.) Read the real
  paper first.
- ❌ Fabricating experimental numbers and presenting them as done. State clearly when a table is a template
  awaiting real values.
- ❌ Arguing with or dismissing the reviewer.
- ❌ Promising a change in the letter but not showing the blue-marked text.
- ❌ Leaving the superlative ("first", "principled") in the paper after conceding it in the letter — sweep
  the manuscript too.
- ❌ **Loaded words that invite a fresh challenge — 慎用, not banned.** Beyond `first`/`principled`, treat
  `guarantee(d)`, `provable/provably`, `justifies` (circular or reversed-causality: "property X justifies the
  choice that *produces* X"), `corroborated`, hollow `standard`, `deployment-oriented/-ready`, and blanket
  robustness phrasings (`irrespective of class imbalance` → tie to the `ratio` and the regime) as words to
  use with caution (see the academic-paper-writing "Words to use with caution" list). Keep one only if it
  passes all four tests: it does **not** overclaim; it is **not 无中生有** (never cite a Proposition/Theorem/
  equation/number/wording that is not in the *current* manuscript — e.g. do not claim "principled
  justification → a formal justification" if no such phrase exists, or reference a Proposition 5 when only
  three exist); it is literally true as stated (qualify expectation-level/linearised results with "to first
  order"); and it gives the reviewer **no hook to re-open the concern or open a new, extended one**. Keep a
  word only when it *lowers* the claim (e.g. `standard` admitting a result is textbook). Consistency: if the
  reply disavows a framing ("not meant to provide guarantees"), the manuscript must not use that word either,
  and any letter passage quoting a reworded manuscript phrase must be re-synced (Golden rule 2a).
- ❌ Generic AI filler ("comprehensive", "robust", "novel") used as empty praise of one's own work.
- ❌ **Closing every reply with a thank-you coda.** "Again, we thank you for this comment… we hope this
  adequately addresses your concern" after the blue insert is redundant filler — end the reply ON the blue
  artifact (LocoMamba format). One warm closer in the overview reply is enough.
- ❌ **Reusing the identical "marked in blue as follows:" lead-in for every comment.** Vary it per edit
  (§1 beat 5); a copy-pasted lead-in reads as template-filling.
- ❌ **Em-dash between clauses / em-dash sandwiches (`X --- Y --- Z`)** anywhere in the letter or in
  manuscript prose and captions. Strong AI tell; use commas, parentheses, a colon, or split into separate
  sentences. (`--` en-dashes in compounds like `vision--language` are correct; the offender is `---`.)
- ❌ **Echoing or conceding a core-value criticism.** Do not restate "the work is just a combination / not
  novel / a mere assembly of existing modules" even to refute it; repeating the reviewer's framing
  foregrounds the weakness. Address the concrete actionable ask, then emphasise strengths and differentiate
  positively without naming the alleged defect. (See §1 beat 2 and the §2 "just a combination" row.)
- ❌ **Stuffing definitions/methodology/sourcing into a caption.** Long, explanation-laden captions read as
  cluttered; the caption names the artifact, the body explains it. Move the explanation to the body (same
  colour) and sync every letter copy.
- ❌ **Framing the contribution as a swap in blue.** No `replace`/`rather than`/`instead of` in
  manuscript blue — state what the method does, positively (see §3).
- ❌ **Reproducing only a caption (or a pseudo-caption) instead of the full figure/table**, or showing only
  a subset of figures when the reviewer attacked the figures as a whole. Bring the entire artifact, and all
  regenerated figures, into that comment's collection.
- ❌ **Announcing a non-change.** NEVER write "we do not modify X", "the Conclusion is left unchanged",
  "no changes were made to Y", or similar. A rebuttal describes only what you *did* change; stating what
  you did *not* touch is pointless, draws the reviewer's eye to a non-action, and reads as a guilty
  over-explanation (此地无银三百两 — a clumsy denial that advertises the very thing it disclaims). If a
  section/table is unchanged, simply say nothing about it. Likewise, do not justify *where* you placed an
  edit by contrasting it with where you didn't ("added to the discussion only, not the conclusion") — just
  state where it was added and stop.

---

## 5. Workflow when invoked

1. Identify the target response file and its format (`.tex` reviewresponse vs `.docx` CACAIE form).
2. Read the actual manuscript and the actual reviewer comments. Map each comment to its real referent
   (which table/figure/equation/section it concerns).
3. Classify each comment via the table in §2 and pick the strategy.
4. Draft each reply with the six-beat template (§1), grounded in the real paper.
5. For any "add experiment/table" comment, either (a) use real numbers the user provides, or (b) build the
   structure and explicitly flag the placeholders for the user to fill.
6. **For EVERY comment that implies a manuscript change, perform BOTH edits (Golden rule 2):** put the
   blue-marked text in the letter AND actually insert the same `\textcolor{blue}{}`-wrapped text into
   `cas-dc-template.tex`. Do not stop at the letter. Sweep the manuscript for other instances of the same
   issue (e.g., a softened "first"/"principled" must be fixed everywhere it appears).
7. After drafting, do a sync check: for each reply that claims an edit, confirm the corresponding blue edit
   exists in the manuscript and the wording matches the letter.

Related: see the `academic-paper-writing` skill for the manuscript-side prose/claim discipline that the
blue-marked edits must follow.
