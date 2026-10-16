# Engineering and scoped implementation

Read for nontrivial implementation, refactoring, or architectural work.

## Before editing

1. Locate the exact file(s) and current working version. Inspect relevant implementation, existing tests, and uncommitted changes; never assume another demo is the target.
2. State the desired observable outcome, acceptance criteria, important invariants, and specifically what must stay unchanged. Distinguish requirements from optional improvements.
3. Draft a proportionate plan, noting assumptions and tradeoffs. Actively **challenge** it: seek failure cases, simpler alternatives, unintended consequences, and reasons the proposed approach might not work.
4. **Validate** material assumptions with code inspection, a small reproduction, or a targeted experiment. **Revise or restart** the plan when the evidence warrants it. Bound this process; do not let planning replace implementation.
5. **Execute** incrementally, then **verify** behavior and regressions against the original criteria.

For straightforward edits, compress these steps into a brief mental check followed by a focused change and verification.

## Change discipline

- Touch only the lines and adjacent documentation required for the requested change. Preserve unrelated behavior, UI, controls, layout, style, names, public interfaces, and implementation details.
- Refactor only when genuinely required for correct integration or to avoid immediate new technical debt; do not opportunistically improve other code.
- If an unrelated defect must be fixed, identify the additional change and why it was necessary rather than silently expanding scope.
- Prefer the existing project's conventions and simple implementation over a generic framework or abstraction.
- Keep comments and docs accurate about the **current behavior**; avoid comments that narrate old implementations or migration history.
- Preserve existing user changes and inspect the full diff for accidental edits. Don't discard uncommitted changes to obtain a cleaner baseline.
- If presenting edited source files directly in chat, supply complete pasteable files when practical rather than an isolated diff, unless the user requested a diff.

## Finishing

Report the files/line ranges changed, tests actually run and their outcomes, any relevant unchanged behavior checked, and remaining unknowns. Never present a proposed or simulated check as a completed test.
