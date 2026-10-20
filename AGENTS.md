# Project instructions

## Non-negotiable principles

- Confirm the exact target file, version, and requested outcome before changing or evaluating code. Do not confuse separate demos or revisions.
- Treat “why?” and other questions as requests for explanation, not orders to edit, revert, or otherwise change files. Answer the question directly; make changes only when the user asks for them.
- Preserve all behavior outside the requested scope. Make the smallest coherent diff; avoid unrelated cleanup, redesign, renaming, styling, or dependency changes. Review the diff before finishing.
- For renderer geometry and transforms, calculate the resulting value directly from the inputs. Do not calculate an intermediate visual target and then search or invert to recover the value.
- Establish the *expected* behavior before calling something a bug. An observed difference from a convenient reference is not proof of incorrectness.
- Separate measurements and verified observations from hypotheses and untested explanations. Do not claim a test passed unless it was actually run.
- Verify the final behavior in the real application when possible, including appropriate regressions; do not substitute source inspection or correct math for rendered correctness.
- For substantial or uncertain work, use **Plan → Challenge → Validate → Revise → Execute → Verify**. Scale the effort to the task; don't overengineer trivial edits.
- Keep reports concise and include relevant file paths and line numbers for code findings or changes. Identify limitations and remaining uncertainty.

## Load the relevant guides

Before the corresponding work, **open and read** these files. They are not automatically expanded merely because they are linked here; read only applicable guides, and read more than one when necessary:

- Nontrivial implementation or refactoring → `.agent-guides/engineering.md`
- Bug reports, audits, root-cause analysis → `.agent-guides/diagnostics.md`
- Camera, sprite transforms, ground, occlusion, or projection → `.agent-guides/rendering.md`
- Visual changes, screenshot comparisons, or visual correctness claims → `.agent-guides/visual-testing.md`
- Performance investigation, optimization, or benchmarking → `.agent-guides/performance.md`

The guides elaborate on these principles; they must not override them. Follow higher-priority instructions and explicit task requirements, and flag genuine conflicts instead of silently choosing an interpretation. Don't treat reading a guide as verification.
