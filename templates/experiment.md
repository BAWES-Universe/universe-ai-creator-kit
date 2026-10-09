# Experiment: `<concrete question or outcome>`

Copy this file into a named contribution and replace the placeholders. Delete irrelevant prompts, but keep missing evidence explicit. This is a template, not a completed test report.

## Summary

- **Date / author:** `<date, creator>`
- **Question:** `<one thing this experiment should establish>`
- **Scope:** `<map, Woka, tile/module, art, lighting, tooling, or validation>`
- **Evidence label:** `<Verified in the stated environment / Historical or reported / Experimental / Unverified>`
- **Outcome:** `<Accepted for the stated purpose / Needs revision / Rejected for the intended direction / Preserved as reference / Not reviewed>`
- **One-sentence result:** `<what actually happened, including the most important limit>`

## Sources and rights

| Input | Exact repository/revision or content hash | Source path/link | Rights and allowed use |
|---|---|---|---|
| Parent experiment or candidate | `<identity>` | `<link>` | `<license/permission or unresolved>` |
| Source art / texture / avatar | `<identity>` | `<link>` | `<rights>` |
| Runtime / authoring code | `<identity>` | `<link>` | `<license>` |

- **Source availability:** `<what another creator can obtain; private access requirements>`
- **Historical source, if applicable:** `<descriptive briefing/report label and date, without private chat exports>`
- **Preserved original:** `<unchanged snapshot and derivative relationship>`
- **Redistribution limits:** `<assets excluded, attribution required, or permission still needed>`

Do not include credentials, personal filesystem paths, private conversation links, or private attachment identifiers in a published record. Use authorized source links or descriptive provenance instead.

## Target and setup

- **Product/fork and engine commit:** `<exact target; other targets remain unverified>`
- **Authoring tools and versions:** `<including relevant plugins/models where used>`
- **Environment:** `<OS, browser/device, renderer, CPU/GPU and material settings as relevant>`
- **Asset contract:** `<dimensions, frame order/timing, tile size, alpha, anchors or layer conventions verified from the target>`
- **Source of that contract:** `<pinned code or test>`
- **Dependencies and access:** `<what is needed to repeat this>`

## Reference and acceptance criteria

- **Visual reference:** `<specific source and qualities to retain; reference does not imply reuse rights>`
- **Technical criteria:** `<observable conditions, including positive assertions>`
- **Visual criteria:** `<native-scale silhouette, composition, lighting, materials, proportions, animation>`
- **Runtime criteria:** `<routes, collision, reveal states, animation, interactions, multiplayer/device scope>`
- **Reviewer and decision checkpoint:** `<who decides what; current task-specific agreement>`
- **Out of scope:** `<explicit exclusions>`

## Method actually used

1. `<Input and action, including real command or manual operation>`
2. `<Transformation, exact settings and intermediate output>`
3. `<Final output and how it was checked>`

For generated art, record the model/tool version if available, complete relevant prompt/settings, references, seed if exposed, and candidate selection. If unavailable, write `not recorded`. For conversion, record matting, crop, scale, resampling and palette operations. For maps, separate physical footprints from visible pixels and document reveal/layer behavior.

Only list commands that exist and were actually used. Name the repository root or working directory relative to the source checkout. Do not invent an install/run command to make an incomplete method look reproducible.

## Outputs

| Artifact | Path/link and exact identity | What it is | What it does not prove |
|---|---|---|---|
| Editable source | `<link/hash>` | `<source type>` | `<limits>` |
| Final export | `<link/hash>` | `<TMJ, PNG, etc.>` | `<limits>` |
| Preview / evidence | `<link/hash>` | `<source crop, offline composite, harness capture, full client, multiplayer>` | `<limits>` |

## Checks and observations

| Check | Expected | Observed | Pass / Fail / Blocked / Not run | Evidence |
|---|---|---|---|---|
| Exact file/contract assertions | `<positive criteria>` | `<observation>` | `<status>` | `<link>` |
| Import/build in named target | `<criteria>` | `<observation>` | `<status>` | `<link>` |
| Relevant runtime behavior | `<criteria>` | `<observation>` | `<status>` | `<link>` |
| Native-scale visual review | `<criteria>` | `<observation>` | `<status>` | `<link>` |
| Independent reproduction | `<criteria>` | `<observation>` | `<status>` | `<link>` |

Add only relevant feature rows. For a map, consider collision versus foreground; shade on the avatar; glass; chair/lectern masks; roof enter/leave with persistent collision; audio versus conversation; portals and returns. For a Woka, consider all required populated cells, directions, idle/walk, anchors, consistency, matte/fringes and identity props.

If using a score, state its definition, implementation revision, exact evaluated inputs and class balance. For collision classification, report missed obstacles, false blockers and route failures alongside aggregate agreement. Keep incomparable historical numbers separate.

## Failure analysis and decision

- **Observable failure or remaining gap:** `<specific symptom and evidence>`
- **Demonstrated cause:** `<only what was established; otherwise not established>`
- **Hypotheses:** `<plausible causes still needing a test>`
- **What improved:** `<bounded result>`
- **Reviewer decision and date:** `<decision, purpose and reason>`
- **Why this does or does not meet the intended goal:** `<technical and visual conclusions separately>`

## Reproduction and next step

- **Reproduction status:** `<who repeated it, from which inputs, differences or missing pieces>`
- **Reusable lesson:** `<specific finding, with its evidence label and limits>`
- **Smallest next test:** `<bounded question, evidence needed and stopping condition>`
- **Authorization or access needed:** `<if any>`
- **Promotion status:** `<archive only / proposed derivative / accepted for named use; never inferred from a build>`
- **Related history:** `<earlier attempt and what changed>`

Before submitting, check links and source access, preserve failed evidence, and read [Contributing](../CONTRIBUTING.md), [Evidence status](../docs/evidence-status.md), and [Validation](../docs/validation.md).
