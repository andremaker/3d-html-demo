# Project instructions

## Non-negotiable principles

- Confirm the exact target file, version, and requested outcome before changing or evaluating code. Do not confuse separate demos or revisions.
- Treat “why?” and other questions as requests for explanation, not orders to edit, revert, or otherwise change files. Answer the question directly; make changes only when the user asks for them.
- Preserve all behavior outside the requested scope. Make the smallest coherent diff; avoid unrelated cleanup, redesign, renaming, styling, or dependency changes. Review the diff before finishing.
- Name code elements by their verified responsibility and domain meaning, not by incidental wording used to describe a request, appearance, or implementation history. Establish what an element represents before naming it, use the project’s agreed domain terms, and keep related identifiers consistent. Omit qualifiers already clear from the owning object or local context; include them only when needed to distinguish different roles. Preserve names explicitly chosen by the user; do not use this rule to justify unrelated renaming.
- For renderer geometry and transforms, calculate the resulting value directly from the inputs. Do not calculate an intermediate visual target and then search or invert to recover the value.
- Establish the *expected* behavior before calling something a bug. An observed difference from a convenient reference is not proof of incorrectness.
- Separate measurements and verified observations from hypotheses and untested explanations. Do not claim a test passed unless it was actually run.
- Verify the final behavior in the real application when possible, including appropriate regressions; do not substitute source inspection or correct math for rendered correctness.
- Keep test resource usage strictly bounded. Before running tests, choose the smallest meaningful coverage and a modest budget for processes, time, and memory. Run browser checks sequentially with one active browser session, reuse completed evidence, and do not repeat a full scenario matrix for each screenshot. Set timeouts and clean up only task-owned processes, including browser children. If a run times out or resource pressure appears, stop and diagnose before retrying; do not add overlapping runs or automatically repeat heavy tests. Expand coverage only for a specific unresolved risk, and report checks left unrun.
- For substantial or uncertain work, use **Plan → Challenge → Validate → Revise → Execute → Verify**. Scale the effort to the task; don't overengineer trivial edits.
- Keep reports concise and include relevant file paths and line numbers for code findings or changes. Identify limitations and remaining uncertainty.
- During planning, assess whether the requested outcome calls for restructuring the affected implementation, even if the user has not explicitly requested a refactor or named what to avoid. If there is a meaningful choice between extending the current design and restructuring it, explain the scoped alternatives and their tradeoffs, recommend an approach, and ask the user which to use before making dependent changes. Do not infer authorization for restructuring solely from the requested outcome; do not ask again if the user has already settled that choice. For example, if the implementation supports only one sprite and the user says “add another one,” clarify whether to introduce instance-specific data and shared operations for both sprites or make a narrowly scoped addition. When restructuring is chosen, support existing and new cases coherently, remove superseded code within the affected scope, and avoid unnecessary duplication, exceptions, or overrides. Preserve behavior outside the request and avoid speculative abstractions or unrelated cleanup. Small implementation steps are encouraged; this rule concerns the design decision and final implementation, not the size or sequence of edits.

## Load the relevant guides

Before the corresponding work, **open and read** these files. They are not automatically expanded merely because they are linked here; read only applicable guides, and read more than one when necessary:

- Nontrivial implementation or refactoring → `.agent-guides/engineering.md`
- Bug reports, audits, root-cause analysis → `.agent-guides/diagnostics.md`
- Camera, sprite transforms, ground, occlusion, or projection → `.agent-guides/rendering.md`
- Visual changes, screenshot comparisons, or visual correctness claims → `.agent-guides/visual-testing.md`
- Performance investigation, optimization, or benchmarking → `.agent-guides/performance.md`

The guides elaborate on these principles; they must not override them. Follow higher-priority instructions and explicit task requirements, and flag genuine conflicts instead of silently choosing an interpretation. Don't treat reading a guide as verification.
