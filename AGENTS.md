# legacy-plan-reconciliation-matrix

An agent skill that audits an outdated plan, spec or roadmap against current evidence and produces a per-claim disposition matrix.

## Using this in your project

- Use it when a plan, roadmap, design doc, proposal or decision record predates a major change and must not be reused, cited or built on until it is reconciled.
- Do not use it to write the new plan, run the work the old plan describes, or make the decisions it defers.
- Invoke: load `SKILL.md` (native skill) or paste `PROMPT.md` (chat), then name the legacy document and the current evidence to check it against.
- Follow the procedure in `SKILL.md`: baseline, inventory every claim from a full read, map to cited evidence, assign one disposition per claim, route, build the live-check register, tally.
- Dispositions: REUSE, REVISE, REJECT, VERIFY, DEFER-TO-EXECUTION. Name the evidence or the unmade dependency for every row.
- Write the matrix and the live-check register as new files in the project (for example `reconciliation-matrix.md`). Use `references/matrix-template.md` as the layout.
- Never edit or delete the legacy document. Never invent evidence or re-verify live facts from memory. State plainly what you did not check.
- Never certify your own completeness without saying so.
- Example output: `examples/synthetic-worked-example.md`.

## Working on this repo

- Setup: none. The repo is Markdown plus `install.sh`.
- Test: `bash tests/test_install.sh` (offline).
- Keep `SKILL.md` description at 300 characters or fewer and `PROMPT.md` at 6000 characters or fewer.
- Do not add real client data, names or prices to `examples/`.
