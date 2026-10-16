# Visual testing and equivalence

Read for changes affecting appearance, renderer validation, screenshot comparisons, or claims that two outputs are visually equivalent.

## Define the visual oracle first

- State which pixels, positions, visible boundaries, occlusion order, or geometric relationships **should** be present. Identify intentional differences before comparing images.
- Use the real application, actual sprite assets, frame crops, alpha channel, frame direction, mirroring, pivots, and current controls.
- Compare against a reference only if it represents the **intended result**. An unclipped image is a useful diagnostic, but not a correctness oracle for an intentionally occluded sprite.
- Do not equate matching matrices, intermediate transform parameters, local coordinates, or corners with complete visual equivalence. Those are supporting tests; final displayed geometry and raster output matter.

## Reproducible browser tests

1. Verify the actual file/version loaded, asset URLs, viewport size, device-pixel ratio, browser/renderer, and any relevant feature flags.
2. Use saved camera states through the application's supported snapshot/load mechanism whenever available. Preserve the full position and orientation; do not round or substitute similar presets without labeling them.
3. Cover normal, oblique, shallow/horizon, overhead, transition/boundary, and mirrored-direction cases as relevant to the change.
4. Wait for assets and rendering to stabilize; distinguish actual animation/timing bugs from screenshot timing artifacts. Repeat suspicious captures.
5. Verify directly: above-ground visibility, ground-intersection continuity, underground projected positions, clipping, occlusion, marker placement, and existing unaffected features.
6. If doing image diffs, account for antialiasing and temporal variability. Attribute a mismatch to the precise invariant it violates, not just its pixel count.

If the browser cannot run, be explicit: source inspection, geometry calculations, or synthetic images are not substitutes for observed browser rendering.

## Reporting

For every confirmed mismatch include the camera state or reproducible steps, expected result, observed deviation, path/line references, and supporting screenshot or pixel/geometric evidence. If an image shows a difference but expected behavior is uncertain, label it **unverified**, not a defect. Do not claim visual correctness on the strength of geometry alone.
