# Validation

Validate the claim you want to make. File integrity, successful import, runtime behavior, and visual acceptance are different results and should be reported separately.

This guide defines a review process. The starter kit itself contains no application test runner or CI pipeline, and publishing these docs does not rerun the historical map tests.

## Record the test context

Every meaningful check needs enough context to repeat it:

- Source repository, commit, and relevant paths.
- Derivative revision or content hash when changes are not committed.
- Authoring tool and runtime versions, including the exact product/fork, repository, and runtime commit when available.
- Environment, browser/device where relevant, and important settings.
- Date, tester, steps or actual command, expected result, and observed result.
- Evidence location and any missing inputs or blocked checks.

Use the [experiment template](../templates/experiment.md). If a version or setting was not recorded, say so and narrow the claim accordingly.

## Review in stages

| Stage | Question | Evidence to keep |
| --- | --- | --- |
| Source and rights | Can someone obtain and appropriately use these exact inputs? | Fixed source links, provenance, permission/license notes |
| File checks | Are the files intact and structurally valid? | Integrity results, schema/reference checks, logs |
| Authoring/import | Does the intended tool open or import the source correctly? | Tool/version, steps, warnings, screenshots |
| Runtime behavior | Does the behavior work in the intended client and situation? | Runtime/version, actions, observations, recording |
| Visual review | Does the result meet the stated visual criteria? | Reference, consistent views, reviewer decision |
| Reproduction | Can another creator obtain the same relevant result? | Independent reproduction notes and differences |

A pass at one stage does not imply a pass at later stages. Keep warnings and exclusions visible.

## Compatibility across implementations

State whether each test targets BAWES Universe, WorkAdventure, or another named fork. Record the source revision and relevant configuration rather than using a generic "WorkAdventure-compatible" label.

For a cross-compatible claim, repeat the affected import, behavior, and visual checks in each named target. Shared file formats do not by themselves establish support for particular properties, avatar contracts, rendering behavior, or integrations. Where only one target has been tested, mark the other target unverified and list the missing checks.

## Map checks

### Source and import

- Confirm the map format, tile dimensions, referenced assets, and required properties against the target runtime's actual contract.
- Check paths, image references, IDs, object properties, and required scripts using the source repository's supported tools.
- Keep archived originals unchanged. If an older source needs normalization for a newer schema, make a derivative and list the changes.
- Distinguish an importable map from a visual-only composition or offline render.

### Movement and collision

- Verify entry/spawn placement and an unobstructed route through the test area.
- Approach boundaries, corners, narrow passages, and doors from relevant directions.
- Check that visible floor and reachable floor agree with the design.
- Test collision separately from draw order. A foreground image can look correct while blocking the wrong space, or the reverse.
- Exercise portals and return paths if they are part of the change.

### Occlusion, shadows, and depth

- Capture the avatar in front of, behind, and beside the object being tested.
- Move through the transition and inspect for pops, cut-off body parts, halos, seams, or incorrect overlap.
- Check foreground masks at chairs, podiums, doorframes, and similar partial-cover objects.
- Inspect roof/glass treatment and above-avatar shadow masks where used.
- Compare the avatar scale, perspective, light direction, contact shadows, and material treatment with the reference.

An offline composition can demonstrate the intended appearance. Runtime depth claims need evidence from the actual rendering and movement behavior.

### Interaction, audio, and multiplayer

Run these checks when the proposed behavior depends on them:

- Required interactions and room/area behavior.
- Proximity conversations and transitions between relevant areas.
- Ambient sound, volume, looping, and deployment-specific loading.
- Multiple users in the same scene and relevant client/device differences.

Do not implement quiet ambience by unintentionally disabling conversation. Do not infer audible correctness from a file reference, or multiplayer correctness from a single-client screenshot. If the needed environment is unavailable, mark the check blocked or not run.

## Woka checks

The target runtime defines the contract. Verify it before export; this handbook does not prescribe unverified universal frame counts or dimensions.

- Confirm dimensions, frame layout/order, directions, timing, anchors, naming, and supported component/layer rules from the actual source.
- Inspect transparency, edges, stray pixels, frame bounds, and alignment.
- Review every required idle/walk frame and direction, including transitions.
- Check silhouette, palette, scale, and consistency across frames.
- If the runtime composes separate avatar parts, test relevant combinations for clipping and alignment.
- Import and view the asset in the intended runtime at its normal display scale.
- Test interaction with map occlusion or lighting when that is part of the claim.

A spritesheet preview alone does not establish in-client animation correctness.

## Visual acceptance

Before review, state what the result is meant to match and who will decide. Use equivalent scale, position, and lighting when comparing revisions so the comparison is meaningful.

Review at both normal gameplay scale and a useful close-up. Look for coherent perspective, readable depth, intentional lighting, clean edges, and a consistent relationship between the avatar and environment.

Record the decision as accepted, needs revision, rejected for the intended direction, or not reviewed. Include the reason. A technique can remain useful even when the larger composition is rejected.

## Report results precisely

Use a short table or list with one entry per check:

| Check | Result | Evidence or blocker |
| --- | --- | --- |
| Exact check and scope | Pass / Fail / Blocked / Not run | Link, recorded observation, or missing requirement |

Treat this row as a template, not a test result. Avoid summary claims such as “all tested” when only a subset was checked. Fresh test results should use the [evidence status](evidence-status.md) rules, including their stated environment and scope.

## Before promotion or publication

Confirm that required technical checks and visual review are complete, known defects are acceptable for the intended use, provenance is adequate, and the target destination is authorized. Verify the actual published revision after an authorized release.

An archive entry, a merged documentation change, or a successful build alone does not promote an asset into a live template catalog.

[Back to the kit](../README.md) · [Contribution checklist](../CONTRIBUTING.md)
