# Performance investigation and benchmarking

Read for performance reports, profiling, optimizations, or scaling claims. Also read `diagnostics.md` when attributing a slowdown to a cause; read `visual-testing.md` if the optimization changes rendering.

## Controlled measurements

1. Identify the exact target version, user-visible symptom, and environment (browser, viewport, device-pixel ratio, acceleration/software rendering, hardware if known).
2. Reproduce a baseline under repeatable conditions, including the actual problematic saved camera states. Ensure the test runs the intended code, not another demo.
3. Measure **frame times** (median, p95 or long frames, and variance) rather than FPS alone. Separate load/warm-up from steady state. Repeat runs and note noise or throttling.
4. Where possible, use browser profiling to distinguish JavaScript, layout, style recalculation, paint, rasterization, and GPU compositing. `performance.now()` around JS does not measure all renderer work.
5. Scale tests intentionally (for example 1, 10, 50, 100 sprites). Separate duplicated DOM copies sharing one pose from genuinely independent animated sprites.

## Isolate stages and interactions

Use controlled A/B runs with one variable changed at a time, followed by selective ablation of the full implementation. Useful rendering stages include:

- Background/ground alone.
- Main sprite(s), without ground projection.
- Extra ground-copy DOM elements with identity transforms.
- Ordinary affine transforms.
- Full projective transform without clipping (diagnostic only; may become singular and extremely expensive).
- Full transform with source-local clipping.
- Complete scene and its update loop.

Disable and restore individual stages without altering unrelated scene behavior. A stage improving performance when disabled **implicates that stage or its interaction**, but does not by itself prove a unique root cause. Inspect near-singular projective denominators, transformed bounds, clipping, canvas redraws, and large surfaces if evidence points there; don't assume any is guilty in advance.

## Optimization acceptance

- Preserve rendering correctness and unrelated behavior; test before/after screenshots and regression camera states.
- Make one targeted change at a time; benchmark comparable builds/configurations.
- Report before/after metrics with units, sample conditions, and limits. Headless or software-GPU timings are not predictions for hardware acceleration.
- Distinguish measured wins from hypotheses. If the bottleneck remains uncertain, recommend the smallest next discriminating experiment rather than a speculative rewrite.
