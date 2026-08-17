# Legacy Plan Reconciliation Matrix

Audit an outdated plan, proposal, spec, or decision record against current evidence — without either
blindly reusing it or throwing it away. This skill produces a per-claim disposition matrix so anyone
picking up the work later can see exactly what's safe to build on, what needs rewriting, what's dead,
what needs a fresh fact-check, and what's genuinely still an open decision.

## What it does

Old planning documents rot at different speeds in different places. A problem statement might still be
completely valid two years later; a pricing table from the same document is stale within weeks; an
architecture description sits somewhere in between. Treating the whole document as one unit — "still
good" or "throw it out" — loses information either way.

This skill walks through a fixed procedure:

1. **Inventory** every claim or heading in the legacy document, independently re-derived from a full
   direct read (not copied from a prior summary), with a row-count check against any existing mechanical
   inventory.
2. **Map** each claim to current evidence — what's changed, cited to a specific source, never guessed.
3. **Assign one of five dispositions** to each claim:
   - **REUSE** — still true, carry it forward as-is.
   - **REVISE** — the reasoning holds, the specific content is stale and needs rewriting.
   - **REJECT** — factually superseded; don't reuse it, maybe cite it as history.
   - **VERIFY** — a live-checkable fact (a price, a version, a count) that hasn't been re-confirmed yet.
   - **DEFER-TO-EXECUTION** — its fate depends on a decision or task that hasn't happened yet; name that
     dependency explicitly.
4. **Route** each disposition to what happens next — reused into the new document, rewritten, dropped,
   sent to a live-check register, or handed to whoever owns the blocking decision.

Along the way it applies a few discipline checks that catch the most common ways this kind of audit goes
wrong quietly: a "hedge-free test" that catches dispositions dressed up as settled when they're not; a
parent/child consistency rule so a deferred section can't have non-deferred sub-claims hiding underneath
it; a rule that an unread comparison file is a reason to go read it, not a reason to punt; and an explicit
ban on the auditor certifying their own completeness without saying so.

The result is two documents: the **reconciliation matrix** itself, and a **live-check register** — a
separate list of every price, version number, vendor term, or fact that must be re-verified before reuse,
deliberately left unchecked at audit time so the audit doesn't quietly go stale itself while being
written.

## Installation

This is a portable Agent Skill following the `SKILL.md` convention. To use
it with Claude Code, copy this folder into your project's `.claude/skills/` directory:

```
your-project/.claude/skills/legacy-plan-reconciliation-matrix/
```

Any other agent runtime that supports the same convention (a `SKILL.md` file with YAML frontmatter plus
supporting reference material) can use this folder the same way — copy it into that runtime's equivalent
skills directory.

Once installed, an agent working in that project will pick up the skill automatically when a task matches
its description (e.g., "reconcile this old roadmap against what we've actually shipped," "audit this
proposal before we reuse any of it," "this design doc is from before the rewrite, what's still valid?").

## Worked example

See [`examples/synthetic-worked-example.md`](examples/synthetic-worked-example.md) for a full worked
excerpt — a fictional mobile-app launch plan reconciled against a fictional current feature audit. It
shows a REUSE row (an unchanged problem statement), a REVISE row (a platform claim that's now simply
wrong and needs rewriting), a REJECT row (a replaced architecture, kept only as history), a VERIFY row
(a pricing assumption that needs a fresh check), a DEFER row with a nested child row demonstrating the
parent/child consistency rule (a build-vs-partner decision that hasn't been made yet), and a split row
(a technical convention that's reusable, paired with a citation that needs separate verification).

All names, prices, and organizations in that example are synthetic and clearly labeled as such.

A blank, ready-to-fill template with the full document structure — matrix table, live-check register,
execution procedure, and evidence ledger — is in
[`references/matrix-template.md`](references/matrix-template.md).

## License

MIT. See [LICENSE](LICENSE).
