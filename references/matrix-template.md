# Reconciliation matrix — blank template

Copy this structure when starting a new reconciliation. Replace every bracketed placeholder. Delete
sections that don't apply (e.g., the secondary-document subsection if there's only one legacy file).

---

# LEGACY_RECONCILIATION_MATRIX.md

**Task / owner:** [who is producing this matrix, and under what mandate]. **Date:** [today's date].
**Scope:** planning/audit artifact only — this matrix is a **scaffold** with provisional or deferred
dispositions, not a final reconciliation. Final dispositions on every deferred row belong to
[whichever downstream process your context uses].

**Revision:** [N] — [date], [reason: initial draft, or independent-review findings addressed — name the
review artifact and finding IDs if this is a revision].

**Primary source(s) read in full this task:** [path/name], ([N] lines/units, dated [baseline]).
Headings/claims below were independently re-derived from this direct read and cross-checked against
[any existing mechanical inventory] — [state whether all units match, and how many].

**Companion evidence artifacts this matrix draws on, not re-derives:** [list each, one line on what
current-state fact each one supplies].

---

## 0. How to read this matrix

Per [governing mandate], the legacy document predates [name the material changes: a strategy pivot, a
completed build phase, a reversed decision, new data]. **Every row below is dated relative to
[baseline].**

A disposition of `REUSE / REVISE / REJECT / DEFER-TO-EXECUTION / VERIFY` appears only where the row's
fate does not depend on an unmade decision — each such row is marked `PROVISIONAL` with its rationale.
Every row whose fate turns on [name the still-open decisions/tasks] reads
`DEFER-TO-EXECUTION (depends on: …)` with the specific dependency named.

**Hedge-free test.** If a PROVISIONAL row's rationale needs a qualifier like "nearly," "likely," or "in
most cases" to claim decision-independence, that row is not decision-independent and must read
`DEFER-TO-EXECUTION` instead.

**Unread-comparison-source rule.** An unread comparison source is never by itself sufficient ground for
`DEFER-TO-EXECUTION` — it's a verification gap, closed by reading it, not a decision gap. It becomes a
genuine deferral ground only when compounded by a second, independent, not-yet-resolved dependency.

---

## 1. Section-by-section matrix

### 1.1 `[legacy document name]` ([N] headings/claims)

| # | Locator | Heading / claim | Content summary | What has changed since baseline | Disposition |
|---|---|---|---|---|---|
| 1 | [line/§] | [heading] | [summary] | [cite current evidence, or "not checked this pass"] | **PROVISIONAL: [REUSE/REVISE/REJECT/VERIFY]** or **DEFER-TO-EXECUTION (depends on: …)** — [rationale] |

**Row count: [N] of [N] legacy headings have a row above**, matching [the independent mechanical count].

**Disposition tally:** [N] `PROVISIONAL` rows — [list row #s] — and [N] `DEFER-TO-EXECUTION` rows —
[list row #s]. [N] + [N] = [total], matching the row count above exactly.

### 1.2 `[secondary legacy document]` ([N] headings, secondary document)

[Same structure, if applicable. Note explicitly what this document is evidence *for* — e.g., "this file
is the legacy proposal's own cited evidence base," not a second independent claim set — if that's the
relationship.]

---

## 2. Live-check register — legacy assertions requiring re-verification at execution

**Do NOT check any of these now.** This register only records what must be re-verified, with its exact
legacy locator, before any reuse.

| # | Legacy locator | Assertion that must be live-checked | Category |
|---|---|---|---|
| 1 | [line/§] | [exact assertion] | price / version / headcount / vendor term / venue rule / literature-currency / other |

**Register count: [N] items.**

---

## 3. Execution procedure for completing this matrix

**Owner role.** This matrix remains owned by [the auditor role] through its final version; the auditor
does not resolve any `DEFER-TO-EXECUTION` row unilaterally. Each deferred row's disposition is resolved
by the specific dependent role/task named in that row's rationale, and the auditor then transcribes that
resolution back into this file with the resolving artifact's own locator.

**Inputs required before a `DEFER-TO-EXECUTION` row can be resolved:**
1. [Decision 1] — a [who]-facing decision.
2. [Decision 2] — [what it determines].
3. The relevant dependent role's own completed, [independently-reviewed, if applicable] output artifact.
4. A fresh, dated re-check of every applicable live-check register item that bears on the row being
   resolved.

**Acceptance test for a resolved row.** A `DEFER-TO-EXECUTION` row may be closed only when: (a) the named
dependent role has issued its own artifact with its own evidence; (b) [if applicable] an independent
reviewer has returned a fresh qualifying verdict on that artifact; and (c) the auditor transcribes the
resulting disposition into this file with an exact locator into the resolving artifact, not a restatement
from memory.

---

## Evidence ledger

```text
files_consulted:
  - [path] — [what was read] — claim supported: [rows/sections]

files_not_accessed:
  - [path] — [why not read] — [which rows this affects]

project_claims:
  - claim: "[a specific, checkable claim this matrix makes about itself]"
    status: [implemented_verified | provisional | open] — [never self-certified without saying so]
    local evidence locator: [exact section/row]

external_sources: [list, or "none"]

conflicts_or_unknowns:
  - conflict: [description]
    governing rule or unresolved status: [how handled]

handoff_notes: |
  [Plain-language summary: disposition tally, split rows, corrections from independent review with
  finding IDs, suggested resolution order for deferred rows.]
```
