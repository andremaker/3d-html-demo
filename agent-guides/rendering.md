# Renderer invariants and geometry

Read for work touching camera behavior, 3D sprite geometry, perspective correction, the ground, penetration, or occlusion.

## Preserve the user's geometry semantics

- The camera is **first-person and self-centered**: changing look direction rotates about the viewer's own eye/POV, never orbits an external point.
- Distinguish the viewer's **eye/POV** from the **screen plane and its center**. In requests about upright sprite orientation, "toward the camera" may specifically mean that the sprite's relevant Y/up direction points toward the *screen center*; simply compensating camera yaw is insufficient. Confirm the intended semantic from the task and existing behavior.
- Preserve the specified sprite pivots/foot anchors, frame selection, mirroring, perspective scaling, orientation continuity, and depth relationships unless the task explicitly changes them.
- Use one coherent transformation model. Avoid angle-sector special cases, discontinuous formulas, or arbitrary thresholds where a continuous geometric solution exists. Test boundaries, including multiples of 90° when relevant.

## Ground penetration and occlusion

- Some of the sprite is intentionally sunk beneath the ground. Keep the configured sink depth and intended effect unless asked to change them.
- Preserve all genuinely above-ground pixels. Render submerged pixels according to their intended ground-plane projection and visibility; verify the ground intersection, boundary continuity, correct layering, and absence of unintended duplicates or gaps.
- A separated or displaced underground copy is **not inherently wrong**. Assess physical projection and occlusion against the intended geometry, not by comparing it visually to an entirely unclipped upright sprite.
- Preserve the distinction between the sprite's ground marker and the reference prism marker. The sprite marker should appear on the ground beneath the projected submerged pixels where required; do not duplicate or inadvertently change the prism marker.
- Do not presume that the current ground is a CSS 3D plane: inspect the actual implementation. A screen-space canvas backdrop and a true world-space surface have different occlusion properties.

## Transform architecture

- When modifying the underground projection, derive correspondence from the **authoritative final composed sprite geometry**, including applicable transform hierarchy, origin, rotation order, correction, mirroring, and scales. Avoid independently rebuilding a second, subtly inconsistent model.
- Determine the submerged region from the final transformed sprite's relation to the ground rather than assumptions about the current correction formula.
- Keep the projection insensitive to future changes in planar sprite transforms when feasible; do not introduce a general-purpose matrix framework merely to satisfy this goal.
- This guarantee applies to **planar projective** sprite geometry; genuinely nonplanar deformation would require separate handling.
- Don't mandate a particular rendering technology (CSS, Canvas, WebGL) without a task-specific reason and evidence.

Before declaring geometry correct, validate world/screen positions and the actual composited output at representative, extreme, and transitional viewpoints. Follow `visual-testing.md` when the claim is visual.
