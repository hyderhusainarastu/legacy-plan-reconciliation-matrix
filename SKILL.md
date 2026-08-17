---
name: legacy-plan-reconciliation-matrix
description: Audits an outdated plan, proposal, spec, or decision set against current evidence by building a per-claim REUSE / REVISE / REJECT / DEFER-TO-EXECUTION / VERIFY disposition matrix, plus a live-check register for facts that must be re-confirmed before reuse. Invoke when a document (a plan, roadmap, design doc, proposal, or prior decision record) predates significant changes — new evidence, completed work, reversed decisions, shifted scope, or the passage of enough time that prices, versions, or facts may have moved — and its content must not be reused, cited, or built upon until it has been rigorously and auditably reconciled against the present state.
---

# Legacy Plan Reconciliation Matrix

## Purpose

A legacy document (a plan, proposal, design spec, roadmap, or prior decision record) was written against
a snapshot of the world. Time has passed. Some of it is still true. Some of it is now wrong. Some of it
can't be judged yet because a decision it depends on hasn't been made. Reusing the document wholesale
risks carrying forward stale facts; rejecting it wholesale wastes sound reasoning that still holds.

This skill produces an auditable **reconciliation matrix**: one disposition per claim in the legacy
document, each disposition backed by a named piece of current evidence or a named unmade dependency —
never a guess, never a blanket judgment, never a disposition the auditor invented from memory.

The output is not a final decision on every open question. It is a rigorous **triage**: what is safe to
carry forward now, what must be rewritten, what must be discarded, what must be fact-checked before
reuse, and what genuinely cannot be settled until someone else makes a decision or does further work —
with that dependency named explicitly, not hand-waved.

## When to use this

Use this skill whenever an agent (or a human) is about to reuse, cite, or build on a document that:

- was written before a material change (a strategy pivot, a completed build phase, a reversed decision,
  a new dataset, a policy change, a product relaunch), or
- contains time-sensitive facts (prices, vendor terms, model/library versions, headcounts, test counts,
  legal/licensing terms) that may have drifted since it was written, or
- is being handed to a new owner who needs to know what in it is still trustworthy versus what needs a
  fresh look.

Do **not** use this skill to write the new plan itself, run the studies/roadmap items it describes, or
make the strategic decisions it defers — those are downstream work this skill deliberately routes to
someone else. This skill's job stops at producing the matrix and the live-check register.

## Core taxonomy: five dispositions

Every row in the matrix receives exactly one **primary** disposition (a row may also carry a documented
split — see "Split rows" below):

| Disposition | Meaning | Test |
|---|---|---|
| **REUSE** | The claim is still true and still load-bearing as written (or with only cosmetic adaptation). | Nothing about it has changed, and nothing about it depends on an unmade decision. |
| **REVISE** | The underlying reasoning, structure, or methodology is still sound, but the specific content (numbers, examples, file paths, citations, framing) is stale and must be rewritten against current sources. | The *shape* survives; the *content* does not. |
| **REJECT** | The claim is factually superseded or wrong as current-state evidence. Do not reuse it, even as a starting point. It may still be cited as a historical data point (e.g., in a "prior iteration" or project-history section) if the target document wants one. | Every plausible future path makes this claim false or obsolete — the staleness is unconditional. |
| **VERIFY** | The claim is a live-checkable factual question (a price, a version number, a count, whether something still exists) that can be *asked* right now without waiting on any decision, but whose *answer* has not been re-confirmed and must be before reuse. | It is a verification gap, not a decision gap — someone just has to go look. |
| **DEFER-TO-EXECUTION** | The claim's fate genuinely cannot be judged yet because it depends on a decision (a scope choice, a strategic direction, a policy call) or a downstream task that has not yet happened. | Two different, still-open future paths would give this claim two different correct dispositions. |

A `PROVISIONAL` qualifier may prefix REUSE / REVISE / REJECT / VERIFY to signal "this is my best current
judgment, not yet independently confirmed" — see Step 4. `DEFER-TO-EXECUTION` never takes `PROVISIONAL`;
by definition it isn't a judgment yet.

## Procedure

Work through these steps in order. Do not skip the inventory step to save time — an incomplete inventory
invalidates every disposition built on top of it.

### Step 1 — Establish the baseline

Identify:
- The legacy document(s) to be reconciled, and the date (or version, or event) they were written against.
  State this baseline explicitly at the top of the matrix: *"Every row below is dated relative to
  [baseline]."*
- The **companion evidence artifacts** you will map claims against — the current state-of-the-world
  documents (a current feature/status audit, a current metrics report, a current decision log, a current
  requirements doc). Name them; do not re-derive their content from scratch inside this matrix, cite them.
- The **governing authority** for this reconciliation — whatever charter, brief, or mandate assigns who
  owns this audit and who owns resolving deferred items. If none exists, state that explicitly rather than
  inventing one.

### Step 2 — Inventory every legacy claim

Read the legacy document **in full**, directly, yourself. Do not rely on a prior summary or inventory of
it without independently re-deriving the heading/claim list and cross-checking the two match exactly.

For each structural unit (heading, numbered decision, named claim — whatever the document's own structure
is), create one row with:

- **Locator** — the exact line number, section number, or other anchor a future reader can jump to.
- **Heading / claim** — the unit's own name or one-line statement.
- **Content summary** — what it actually asserts, in your own words, tight enough to audit against.
- (left blank for now) what has changed, and disposition — filled in Steps 3–4.

**Row-count discipline.** State the total row count and confirm it against any independent mechanical
count available (a `grep`/count of headings, a prior inventory document). If they don't match, find the
missing or extra row before proceeding — a silently incomplete inventory is the single most common way
this kind of audit fails quietly.

If the legacy material spans more than one document (e.g., a main proposal plus an appendix or a cited
audit file), give each its own numbered subsection of the matrix, and note explicitly which document each
serves as evidence *for* (e.g., "this file is the legacy proposal's own cited evidence base, not a second
independent claim set").

A blank template with this full row/register/ledger structure is at `references/matrix-template.md`; a
worked example applying it end-to-end (with synthetic data) is at `examples/synthetic-worked-example.md`.

### Step 3 — Map each claim to current evidence

For every row, write **what has changed since the baseline**, citing:
- specific companion evidence artifacts (by name and section/locator), and/or
- a direct fact you independently confirmed, and/or
- an explicit note that a needed comparison source was **not** read this pass (see the unread-source rule
  below) — never silently guess what an unread source would say.

Keep this column evidence-grounded. "This seems outdated" is not a mapping; "the current feature-status
audit (§4) independently re-verifies this capability as implemented, superseding this table's status
cell" is.

### Step 4 — Assign the disposition

Apply the taxonomy from above. Three tests keep this step honest:

**The hedge-free test (for every `PROVISIONAL` row).** If the rationale for a non-deferred disposition
needs a qualifier like "nearly every," "likely," "in most cases," or "generally" to claim
decision-independence, it is **not** decision-independent. Re-classify it as `DEFER-TO-EXECUTION` instead.
A row that needs a hedge to sound settled is conceding the thing it's trying to deny.

**Parent/child consistency.** If an umbrella row (a section heading covering several sub-claims) is
correctly deferred because its fate depends on an unmade decision, no child row underneath it may claim a
non-deferred disposition on the *same* ground the parent is deferred on. A sub-claim cannot be
decision-independent when the section containing it is not. (It *can* still be independently REUSE'd or
VERIFY'd if it turns on a genuinely separate, already-decidable question — see split rows below — but the
rationale must name that separate question, not silently inherit the parent's undecided one.)

**The unread-comparison-source rule.** An unread comparison source (a current document you didn't have
time to read this pass, that the claim should ideally be checked against) is, **by itself**, never
sufficient grounds for `DEFER-TO-EXECUTION`. It is a verification gap — closed by reading the file, not by
waiting for someone else's decision. It only becomes a genuine deferral ground when it is *compounded* by
a second, independent, not-yet-resolved dependency (an unmade decision or a not-yet-run downstream task)
that the row cannot be disposed without, even with the file read. When you defer a row partly on this
ground, name the second dependency explicitly — "depends on X, with the unread file as a compounding,
not primary, reason" — and when a row has no such second dependency, keep it at its evidence-based
disposition with the unread file named as a precondition to check, not a reason to stall.

**Split rows.** A single legacy claim sometimes bundles two genuinely separable questions — e.g., "is this
citation/fact still current" (a VERIFY question) versus "should this content be kept at all" (a
DEFER question, because retention depends on an unmade scope choice). When that happens, give the row
**both** dispositions explicitly, pick one as primary for tallying purposes, and flag in the rationale
that it's split so a future editor doesn't read the primary disposition as an unqualified verdict on the
whole row.

### Step 5 — Route each disposition

Each disposition implies a different next action. State the routing explicitly per row, not just the
label:

- **REUSE** → adapt directly into the new deliverable; cite which structural slot in the target it now
  fills.
- **REVISE** → carry the reusable reasoning/structure forward explicitly in the rationale (so the next
  editor knows *what* to keep), and name what specific content must be rewritten and against which current
  source.
- **REJECT** → exclude from any current-state use. If a "history of this project" or "prior iteration"
  section exists in the target, it may be cited there as a dated snapshot — say so if relevant, otherwise
  say it should simply be dropped.
- **VERIFY** → add it to the **live-check register** (Step 6). Do not resolve it inline in the matrix.
- **DEFER-TO-EXECUTION** → name the *specific* decision, role, or downstream task the row's resolution
  depends on. "Depends on: [the scope decision]" is not enough — say which decision, citing where it is
  tracked if it's already logged somewhere.

### Step 6 — Build the live-check register

Collect every `VERIFY` item (and every individually re-checkable sub-fact inside a `REJECT`ed or
`REVISE`d row — e.g., each cell of a superseded status table, not just the table as a whole) into a
separate register:

| # | Legacy locator | Assertion to verify | Category |
|---|---|---|---|
| 1 | (line/section) | (the exact claim, quoted or closely paraphrased) | price / version / headcount / vendor term / venue rule / literature-currency / other |

**Do not check any of these items now.** The register's job is only to record what must be re-verified,
with an exact locator, before anyone reuses it — checking them is downstream work for whoever executes the
next stage, and doing it here would blur the line between "this audit's job" and "the next stage's job."
If the calling context sets a minimum register size, confirm the count meets it before finishing.

### Step 7 — Tally and self-audit discipline

At the end of the matrix, state the disposition tally (count of REUSE, REVISE, REJECT, VERIFY,
DEFER-TO-EXECUTION rows, summing to the total row count from Step 2). **Recount it directly from the
table itself, every time** — never carry forward an earlier draft's tally by hand. Copying a stale count
forward is the single most common self-inflicted defect in this kind of audit: a row gets re-dispositioned
partway through drafting and the summary sentence doesn't get updated to match.

**Never self-certify this audit as complete or correct.** A worker producing this matrix marking their
own partition tally, taxonomy application, or completeness claim as independently verified — on their own
authority — is exactly the failure mode this skill exists to prevent one level up. If an independent
review process exists in your context, route the completeness claim through it and attribute verification
to that review, not to your own re-reading of your own table. If no independent review is available in
your context, say so plainly in the output rather than implying one occurred.

### Step 8 — Handle independent-review findings as a tracked revision

If an independent reviewer returns findings against a completed matrix (a blocking defect, or
non-blocking suggestions), do not silently edit the matrix. Instead:

1. Add a **revision header** at the top of the document naming the revision number, date, and the review
   artifact/finding IDs that prompted it.
2. For each finding, either fix it and say what changed and why (with the exact finding ID), or state
   explicitly why it's not being changed (an author's-discretion call, with reasoning). Never mark a
   blocking finding as resolved without actually changing the row it targets.
3. Re-run Step 7's tally after every revision — a fix to one row's disposition changes the count.

This keeps the matrix's own revision history as auditable as the claims inside it.

### Step 9 — Write the execution/resolution procedure

Close the matrix with a short procedure section covering:

- **Ownership**: who owns the matrix through its final version, and the rule that the auditor does not
  unilaterally resolve `DEFER-TO-EXECUTION` rows — each is resolved by whichever role or task its own
  rationale named as the dependency.
- **Inputs required before any deferred row can close**: the specific unmade decisions and not-yet-run
  tasks named across the matrix, listed once, deduplicated.
- **Acceptance test for closing a deferred row**: (a) the named dependent role/task has produced its own
  artifact with its own evidence; (b) if your context has an independent-review gate, that gate has
  returned a qualifying verdict on that artifact; (c) the auditor transcribes the resulting disposition
  back into this matrix with an exact locator into the resolving artifact — never a restatement from
  memory of what someone said.
- **Resolution order**: note that upstream, gating decisions (ones several other rows depend on) should be
  resolved before the rows nested under them — resolving out of order wastes work when the upstream
  decision changes the answer.

### Step 10 — Evidence ledger

Close with a structured ledger (adapt the exact schema to whatever convention your context uses; if none
exists, use this one):

```text
files_consulted:
  - <path/artifact> — <what you read, in full or in part> — claim supported: <which matrix rows/sections>

files_not_accessed:
  - <path/artifact> — <why it wasn't read> — <which rows this affects and how, per the unread-source rule>

project_claims:
  - claim: "<a specific, checkable claim this matrix makes about itself, e.g. row-count completeness>"
    status: <implemented_verified | provisional | open>  — never self-certified without saying so
    local evidence locator: <exact section/row>

external_sources: <any outside sources consulted, or "none — this task used only the named local sources">

conflicts_or_unknowns:
  - conflict: <anything you could not resolve>
    governing rule or unresolved status: <how it's handled — resolved, or open and by what rule>

handoff_notes: |
  Plain-language summary for whoever picks this up next: the disposition tally, which rows are split,
  which corrections came from an independent review (with finding IDs) versus your own drafting, and the
  suggested resolution order for the deferred rows.
```

See `references/matrix-template.md` for a fillable blank of this full structure (rows, live-check
register, and ledger), and `examples/synthetic-worked-example.md` for a complete worked instance built on
synthetic data.

## Common failure modes to avoid

- **Guessing instead of citing.** Every "what has changed" cell and every disposition rationale must point
  to a named source or an explicit "not checked this pass" — never an unsourced impression.
- **Confusing a verification gap with a decision gap.** Don't defer something you could just go check.
- **Hedged PROVISIONAL rows.** Run the hedge-free test on every non-deferred disposition before finalizing.
- **Parent/child inconsistency.** A deferred section cannot contain a non-deferred sub-claim on the same
  undecided ground.
- **Stale hand-carried tallies.** Recount from the table, not from memory of the last draft.
- **Self-certifying your own completeness.** Say plainly whether independent review happened; never imply
  it did when it didn't.
- **Resolving a deferred row from memory.** A deferred row closes only against a named artifact with its
  own locator — never against "I recall the team decided X."
- **Treating a live-check item as already checked.** The register exists precisely so nobody skips the
  re-verification step by assuming a number is "probably still right."
