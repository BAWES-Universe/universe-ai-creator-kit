# Woka creation: native pixels, consistent identity

A Woka is an animated game asset. Its final texture, frame alignment and in-client behavior matter more than the full-resolution illustration used to make it. Read the [twelve-attempt history](experiment-history.md#1-woka-research-twelve-approaches-not-one-successful-prompt) before repeating a prompt or conversion experiment.

This kit documents inspected contracts and reported lessons. It does not yet contain the historical generator, converter or a fully reproducible end-to-end Woka pipeline.

## 1. Verify the target runtime first

For **BAWES Universe at commit `5e7670be6c79efc575a7193e8a1a1c8c379b293f`**, the locally inspected source defines this contract:

| Property | Pinned-source finding |
|---|---|
| Frame dimensions | 32×32 px, hardcoded in the texture-loading paths inspected |
| Complete twelve-frame sheet | 96×128 px for three columns by four rows |
| Row order | Down, left, right, up |
| Walking frames | Down `[0,1,2,1]`; left `[3,4,5,4]`; right `[6,7,8,7]`; up `[9,10,11,10]` |
| Walk timing | 10 frames per second, repeating |
| Standing/idle | Middle column: frames 1, 4, 7 and 10 |

Sources: [PlayerTexturesLoadingManager.ts](https://github.com/BAWES-Universe/workadventure-universe/blob/5e7670be6c79efc575a7193e8a1a1c8c379b293f/play/src/front/Phaser/Entity/PlayerTexturesLoadingManager.ts) and [Animation.ts](https://github.com/BAWES-Universe/workadventure-universe/blob/5e7670be6c79efc575a7193e8a1a1c8c379b293f/play/src/front/Phaser/Player/Animation.ts).

Be precise about idle: the source defines idle animation entries, each with **one held frame**. The historical briefing's “no idle animation” means there is no multi-frame idle sequence in that contract. It does not mean the code has no idle state.

Use an RGBA texture with real transparent background for this workflow. Recheck the loader, frame order, anchors, component composition and renderer in the actual target before exporting. This inspection is not proof that every deployed Universe room or another WorkAdventure version uses the same configuration. It also does not prove a universal no-scaling rule; distinguish native texture size from camera zoom and display behavior.

A 64×64 character is an engine/product compatibility change if the chosen loader still hardcodes 32×32. Merely uploading a larger sheet does not add support and can change the apparent relationship between avatars, furniture and maps. The old 32-versus-64 decision was pending in the historical briefing; it is not a current standing instruction to change the engine.

## 2. Preserve the accepted output without inventing its recipe

Greg Gulf Woka v3 is the accepted avatar used unchanged for scale in the subsequent map work. Local artifact inspection for this kit found:

- A 96×128 RGBA PNG named `greg-gulf-woka-v3.png`.
- SHA-256 `e88ba016c58f6bc7616c831c3c56a4656e66772794940af93c0c0835e85a987d`.
- A byte-identical copy in the campus QA material, where the [archived provenance](https://github.com/BAWES-Universe/universe-maps/blob/d818e6c4c001e5fa7ba76e02663a1fb9ce9460fd/map-mocks/butterfly-campus-v3-light/map/ART-PROVENANCE.md) identifies it as the previously accepted sheet, used only for testing.

Those facts establish the inspected output's identity and documented use. They do not identify the prompt, model, seed, conversion code or complete recipe that produced it. Do not equate Greg v3 with a particular historical converter candidate merely because both were discussed during Woka work.

The avatar is not bundled as a generally licensed asset in this handbook, and its use in a review image is not permission to install it into another account. Preserve the original bytes when using an authorized copy as a scale baseline. Do not enlarge the avatar to make an oversized room appear populated.

## 3. A bounded creation workflow

### Establish the character and comparison

Describe the silhouette, proportions, clothing, key props and internal value contrast. Identify the established default/accepted Woka used as the comparison and the intended runtime. Choose a small test before generating an avatar collection.

Use a native-size view plus a nearest-neighbor enlargement on a neutral background. An enlarged beauty image can hide native-size problems; a rejected tiny predecessor is a poor sole benchmark for a new result. Keep the comparison scale and background consistent.

Record the review checkpoint appropriate to the current task. The early experiments used owner approval of raw character art before conversion. That historical process is useful context, not an automatic rule that overrides the present task's agreed scope.

### Generate for final readability

The reported experiments favor a coherent multi-pose sheet over unrelated per-frame generations for identity consistency. They also found that construction language, such as large orthogonal shapes and deliberate stair-step corners, worked better than asking for an intricate miniature illustration.

These are hypotheses to test, not guarantees. Numeric pixel requests were repeatedly ignored, and identical prompts varied substantially. Keep several candidates and record failures. A specialist tool such as PixelLab is another candidate, but its historical research was not a hands-on success and its output layout must still be adapted and tested.

At native size, a face needs a readable skin field and a few intentional feature marks. Tiny high-contrast white eye blocks can dominate the whole head. Inspect before repairing: historical hand-stamped face passes made several results worse.

### Convert deliberately and retain every stage

Keep the raw source, extracted figures, final texture and a preview rendered from that final texture. Record exact versions, options, palette and intermediate dimensions. If a step is manual, describe it as manual.

The historical converter lessons worth testing are:

- Preserve aspect ratio while fitting the intended figure height.
- Matte the source cleanly, including color-fringe removal. A threshold key can leave colored specks.
- Use consistent sizing within each animation row, rather than independently fitting every frame. Check consistency between directions too.
- Compare reduction methods at the final size. The reported smooth-to-4× then nearest-neighbor method helped a particular source; blindly smoothing or blindly using nearest-neighbor can both lose important detail.
- Preserve useful skin, cloth and metal distinctions in the palette. An arbitrary small color count can erase identity props.
- Repair outlines and facial marks only when the native result requires it; do not let cleanup metrics force every character into the same face or silhouette.

The historical names `make_woka.sh`, `verify_wa.py`, converter and `gridgen` identify prior work, not scripts shipped here. Recover and inspect that code before writing a runnable recipe. No dependency installation or command in this guide implies that it is available.

## 4. Positive asset checks

Do not rely on a green summary whose tests can pass for an empty or wrong-sized input. The reported historical validator accepted a 48×64 file once. Make every required property an explicit assertion against the actual final bytes.

For the pinned twelve-frame target, check:

1. The PNG decodes, has exact expected dimensions and RGBA/alpha behavior, and matches the intended output hash.
2. Each of the twelve cells contains the intended frame in the intended row/column. No empty cell, duplicate substituted direction or crop overflow is silently accepted.
3. Transparent background exists where intended. Inspect fringes and stray islands on both light and dark backgrounds.
4. Feet and anchors behave consistently. Track visible bounds and silhouette/ink changes within a walk, without treating an arbitrary bounding-box rule as artistic truth.
5. Face, clothing and identity props remain recognizable across all directions. A disappearing cup, pot, tool or accessory is a real failure even if the sheet dimensions pass.
6. The middle column is a plausible standing pose in every direction. Review the complete looping sequence and transitions, not just twelve still cells.
7. Texture import and movement work in the named runtime, with the actual avatar composition or component combinations being claimed.

Do not require every outer row of pixels to be transparent by default. The inspected accepted Greg sheet has nontransparent pixels reaching the bottom of its cells, and one frame reaches the top. Record the target's actual clipping/anchor behavior instead of creating an unsupported padding gate.

Reported dark-boundary, outline-continuity, palette-size and ink-swing values are useful diagnostics. Their old implementations and cohorts have not been recovered here. Define and version any new metric before comparing it to the [historical numbers](experiment-history.md#what-the-numbers-actually-compare), and retain a human native-scale review.

## 5. Separate sprite quality from performance in a scene

Good frames cannot fix bad routing or staging. The scene system still controls direction changes, walking speed, arrival, feet anchoring, facing a person or painting, furniture clearance and camera framing.

Review at least one straight walk in each direction, start/stop transitions and a route around the furniture actually used. Where relevant, test the avatar under shade, behind glass, at a reachable chair position and behind a lectern. The [map guide](maps.md#four-concrete-avatar-overlap-examples) explains why these are layer/footprint problems rather than simply demands for more animation art.

An animation GIF demonstrates the exported texture and chosen playback logic. It does not prove full-client behavior, multiplayer synchronization, seating, or correct map occlusion. Label the evidence accordingly.

## 6. What a reusable Woka contribution needs

Provide the exact source/output identities, rights and permitted use; the target engine revision; the prompt/model or manual method actually used; extraction/conversion code with pinned dependencies; all material settings; and checks against the final output. Include native-size comparison, enlarged pixel inspection, four-direction playback and the relevant runtime capture.

If one part is missing, narrow the claim. An accepted artifact is valuable even when its original recipe is unrecovered. A failed but reproducible conversion is valuable even when the source character looked excellent. Record both in the [experiment template](../templates/experiment.md) and follow [Validation](validation.md).
