# Reconcile a legacy plan against current evidence

Paste this into ChatGPT, Claude.ai, Gemini or a local model, then attach or paste the old document and the current evidence (shipped work, current data, decisions made since).

---

You are auditing a legacy document (plan, roadmap, spec, proposal or decision record). Do not write a new plan and do not make the decisions it defers. Produce a reconciliation matrix and a live-check register.

Rules
1. Read the whole legacy document directly. Do not rely on a prior summary.
2. Inventory every claim or heading as one row. State the row count. If a mechanical inventory exists, compare counts.
3. For each row, name the current evidence (file, section, data point) that supports the disposition. If you have no evidence for a row, say so. Never guess or use memory for current facts.
4. Give each row exactly one disposition:
   - REUSE: still true and load-bearing as written.
   - REVISE: the reasoning holds, the content (numbers, paths, examples, citations) is stale and must be rewritten.
   - REJECT: factually superseded under every plausible future. Do not reuse; it may be cited as history.
   - VERIFY: a checkable fact (price, version, count, whether something still exists) not yet re-confirmed. A gap in checking, not a gap in decision.
   - DEFER-TO-EXECUTION: depends on a decision or task not yet made or done. Name that dependency. Two open futures would give two different correct answers.
   You may prefix REUSE/REVISE/REJECT/VERIFY with PROVISIONAL when it is your best judgment but unconfirmed. Never prefix DEFER.
5. Hedge-free test: if a row's reasoning says "probably", "likely" or "might", it is not settled. Mark it PROVISIONAL, VERIFY or DEFER, not REUSE or REJECT.
6. Parent/child consistency: a deferred section must not contain non-deferred children that depend on the deferral. Re-check children of every DEFER row.
7. If a comparison file is unread, go and read it. Do not punt a row because you have not looked.
8. Split a row when one claim is partly reusable and partly needs checking, and say which part is which.
9. Route each row: REUSE goes into the new document, REVISE gets rewritten, REJECT is dropped or kept as history, VERIFY goes to the live-check register, DEFER goes to the owner of the blocking decision.

Output
A. Matrix table with columns: ID | Legacy claim (quote or short paraphrase) | Disposition | Evidence or dependency | Route.
B. Live-check register: every price, version, vendor term, count or fact to re-confirm before reuse, with who or what can confirm it. Leave them unchecked; do not fill them from memory.
C. Tally: count per disposition, and check that the counts sum to the inventory row count.
D. Self-audit: list what you did not read or could not check. Do not claim the audit is complete or independently reviewed.

If I send review findings later, treat them as a tracked revision: add a revision header, answer each finding by ID, fix or rebut it with reasons, and recompute the tally.
