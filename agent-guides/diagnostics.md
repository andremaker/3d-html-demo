# Diagnosis and evidence standards

Read for bug investigation, audits, disputed behavior, and root-cause analysis.

## Establish whether a defect exists

1. Identify the **intended observable behavior** from the user's request, the application contract, or a valid geometric/behavioral invariant.
2. Reproduce the reported observation in the **exact current target version**. Record the relevant input/state, environment, and steps. Keep other demos and older versions separate.
3. Compare expected and actual outcomes under controlled conditions. Verify that the reference is itself a valid correctness oracle.
4. Try to **disprove** the diagnosis. Look for intentional behavior, alternative causes, experimental artifacts, timing problems, incorrect test setup, and misleading metrics.
5. Only then label a finding a **confirmed defect**, **supported suspicion**, or **unverified observation**.

A screenshot difference alone is not a bug. A missing piece of an intentionally clipped sprite may be correct occlusion. An unclipped sprite is not automatically the expected appearance when part of the sprite should be underground.

## Identify a cause without guessing

- Separate symptom, triggering conditions, mechanism, and root cause. Do not promote correlation to causation.
- Use minimal reproductions, isolated toggles, controlled A/B comparisons, or targeted instrumentation where useful.
- Check whether changes affect the primary symptom **and** whether they break a working case.
- Distinguish analytic geometry checks from actual browser rendering, including rasterization, antialiasing, timing, compositing, and asset-loading behavior.
- Do not infer failure solely from a console message, screenshot, metric, or single flaky run without establishing its relevance.
- If findings conflict, investigate or report the uncertainty; do not force a convenient conclusion.

## Evidence in the report

For every substantive issue, include: the expected behavior; the observed violation; the reproducible condition; evidence or test method; relevant path and line numbers; and confidence/limitations. If no defect is demonstrated, explicitly say so. Do not recommend architectural changes based only on an unconfirmed diagnosis.
