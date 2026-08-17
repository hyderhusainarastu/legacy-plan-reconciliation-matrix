# SYNTHETIC EXAMPLE — all names, figures, and organizations below are fictional

This is a shortened, illustrative reconciliation matrix produced by following the
`legacy-plan-reconciliation-matrix` skill. It is not a real audit of a real product, and none of the
figures, dates, or names correspond to any real organization. It exists to show the shape of the output.

---

# LEGACY_RECONCILIATION_MATRIX.md (example)

**Task / owner:** Legacy-Plan Auditor, per the FieldNotes program charter §4. **Date:** 2026-03-01.
**Scope:** planning artifact only — a scaffold with provisional or deferred dispositions.

**Primary source read in full this task:** `legacy/2025-Q4-launch-plan.md` (18 headings, dated
2025-10-01). Headings below were independently re-derived from a direct read and cross-checked against
the mechanical inventory in `evidence/P1_inventory.md` — all 18 headings match exactly.

**Companion evidence artifacts:** `evidence/current_feature_audit.md` (live capability status, refreshed
2026-02-20); `evidence/pricing_snapshot_2026-02.md` (current vendor pricing); `charter/SCOPE_DECISION.md`
(the still-open build-vs-partner scope choice referenced below).

---

## 1. Section-by-section matrix

| # | Locator | Heading / claim | Content summary | What has changed since baseline | Disposition |
|---|---|---|---|---|---|
| 1 | §1 | Problem statement | Frames FieldNotes as a tool for offline note capture during site visits, syncing when reconnected. | The current product brief (`evidence/current_feature_audit.md` §1) still frames the problem identically; no reframing has occurred since. | **PROVISIONAL: REUSE.** The problem statement is unchanged and independently confirmed current. |
| 2 | §2 | Target platform | States "iOS only, Android planned for a later phase." | The Android build shipped in 2026-01 per the current feature audit (§2, "Android GA, 2026-01-14") — this is now factually wrong, not merely dated. | **PROVISIONAL: REVISE.** The platform-coverage framing must be rewritten to reflect both platforms as shipped; the underlying "mobile-first, offline-first" design principle survives and should be carried forward explicitly. |
| 3 | §3 | Sync architecture | Describes a custom conflict-resolution protocol built in-house, with named file paths in the old `sync-engine/` package. | The current feature audit (§3) confirms the in-house protocol was replaced by a third-party CRDT library during the 2026-01 refactor; the named file paths no longer exist. | **PROVISIONAL: REJECT** as current-state architecture description. Retain only as a historical citation if a "project history" section is wanted; do not reuse any file path or protocol description verbatim. |
| 4 | §4 | Pricing tier structure | Proposes a $9/month single tier, citing "current App Store minimum commission as of Sept 2025." | Whether the App Store commission terms cited here still apply is a live-checkable fact, not yet re-confirmed this task. | **PROVISIONAL: VERIFY.** Route to the live-check register (item 1) before this figure is reused in any pricing section. |
| 5 | §5 | Partner-vs-build decision for sync backend | Recommends building the sync backend in-house rather than using a managed backend-as-a-service provider, based on a 2025 cost comparison. | `charter/SCOPE_DECISION.md` records this exact build-vs-partner question as still open pending a vendor RFP the team has not yet run. | **DEFER-TO-EXECUTION** (depends on: the build-vs-partner scope decision, `charter/SCOPE_DECISION.md`, not yet made — and the vendor RFP that decision itself depends on, not yet run). |
| 5a | §5.1 | Cost comparison table | Line-item comparison of in-house engineering cost vs. three named vendors' list pricing, dated Sept 2025. | This table is nested under the still-deferred build-vs-partner decision (row 5) — it cannot be independently disposed while its parent decision is open, per the parent/child consistency rule. Every vendor price in it is also individually stale (5+ months). | **DEFER-TO-EXECUTION** (depends on: row 5's resolution). Every dollar figure additionally requires its own live re-check (register items 2–4) before any reuse of even the table's structure. |
| 6 | §6 | Accessibility commitments | States a commitment to WCAG 2.1 AA compliance for all new screens, with a general rationale (regulatory + inclusion). | This is scope-independent good practice — true regardless of which build-vs-partner path is eventually chosen — and the current accessibility audit (`evidence/current_feature_audit.md` §7) confirms it is still the team's stated standard. | **PROVISIONAL: REUSE**, carried forward verbatim into the current accessibility section. |
| 7 | §7 | Analytics event schema | Proposes a specific event-naming convention (`screen.field.action`) for usage analytics, citing a comparator app's convention as precedent. | The event-naming *convention itself* is a scope-independent technical choice; whether the comparator citation is still the right precedent is unverified — the comparator's own current analytics approach was not checked this task. | **Split row.** Primary: **PROVISIONAL: REVISE** — the naming convention is reusable; rewrite the comparator citation against a fresh check of that app's current approach (unread-source rule: this is a verification gap, not a deferral ground, since no second dependency is named). Secondary: **VERIFY** the comparator citation specifically (register item 5). |

**Row count: 8 of 18 example headings shown** (this is a shortened illustrative excerpt, not a complete
18-row matrix).

**Disposition tally (this excerpt), recounted directly from the table above:** 6 `PROVISIONAL` rows (1, 2,
3, 4, 6, 7-primary) and 2 `DEFER-TO-EXECUTION` rows (5, 5a) = 8, matching "Row count: 8" above. Plus 2
items routed to the live-check register from rows 4 and 7 (register entries 1 and 5; rows 5.1's own
sub-facts add register entries 2–4, for 5 register items total — see Section 2).

---

## 2. Live-check register (excerpt)

**Do NOT check any of these now.**

| # | Legacy locator | Assertion that must be live-checked | Category |
|---|---|---|---|
| 1 | §4 | "Current App Store minimum commission as of Sept 2025" underlying the $9/month tier recommendation | Vendor term / price |
| 2 | §5.1 | Vendor A's list price for managed sync backend, Sept 2025 snapshot | Vendor pricing |
| 3 | §5.1 | Vendor B's list price for managed sync backend, Sept 2025 snapshot | Vendor pricing |
| 4 | §5.1 | Vendor C's list price for managed sync backend, Sept 2025 snapshot | Vendor pricing |
| 5 | §7 | Comparator app's current analytics event-naming convention | Software feature / precedent currency |

**Register count: 5 items (excerpt).**

---

## 3. Execution procedure (excerpt)

**Owner role.** This matrix remains owned by the Legacy-Plan Auditor through its final version; the
auditor does not resolve row 5 or 5a unilaterally — both close only when the build-vs-partner scope
decision in `charter/SCOPE_DECISION.md` is made and the vendor RFP it depends on has returned results,
transcribed back into this file with an exact locator into the RFP outcome document.

---

## Evidence ledger (excerpt)

```text
files_consulted:
  - legacy/2025-Q4-launch-plan.md — full file, read directly this task (18 headings)
    claim supported: all rows in §1

  - evidence/current_feature_audit.md — §1, §2, §3, §7
    claim supported: rows 1, 2, 3, 6

  - charter/SCOPE_DECISION.md — full file
    claim supported: rows 5, 5a

files_not_accessed:
  - comparator app's current public analytics documentation — not read this task
    affects: row 7's secondary VERIFY disposition

project_claims:
  - claim: "All 18 legacy headings have a row in the full matrix (not shown in this excerpt)."
    status: provisional — not independently reviewed in this synthetic excerpt
    local evidence locator: §1 row count line

external_sources: none — this example used only the named local synthetic files

conflicts_or_unknowns: none in this excerpt

handoff_notes: |
  This is a shortened excerpt for illustration. A real matrix built with this skill covers every
  heading in the legacy document, not a sample of them.
```
