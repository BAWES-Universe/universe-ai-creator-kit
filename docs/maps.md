# Building maps that look and behave like places

A map has at least four independent jobs: composition, walkable geometry, draw order, and interaction. A beautiful image can fail three of them. A valid TMJ can fail the first. Keep their acceptance evidence separate.

Read the [experiment history](experiment-history.md) before choosing a method. It records why whole-scene generation, automatic collision, simplistic tilesets and independently lit cutouts were insufficient. This guide extracts practical lessons; it is not an application, compiler, or universal WorkAdventure specification.

## Choose the smallest useful deliverable

Before generating art, identify:

- The exact target: BAWES Universe or a named WorkAdventure version/fork, pinned to a revision where possible.
- The intended use: one authored room, an expandable world section, a reusable tile library, a visual-only proposal, or a lighting/mechanics study.
- The unchanged comparison avatar and its native size. The studied Universe work uses 32×32 Woka frames; a camera zoom is not a new asset size.
- One visible experience to prove: arriving, meeting the receptionist, approaching a shared worktable, entering a glass room, or speaking at a lectern.
- The visual reference and who decides whether the result meets it.
- Required interactions, and which are intentionally outside this experiment.

Prefer one coherent section with a complete route over an empty full-campus overview. In the Universe case study, the owner's direction was a magical gate/arrival and one small team in a connected, visible workplace. That is context for the recorded decisions, not a requirement for your own space. Follow your own brief; learn from the case study's composition and scale problems. Earlier departmental buildings, palette concepts and brainstorm room lists were not a mandate to build all of them.

## First map exercise: one Lantern Courtyard change

This is a concrete source-based starting exercise, not a newly executed test result. It uses the archived aligned courtyard to study one foreground/footprint relationship without first solving a whole world's art.

1. Obtain `BAWES-Universe/universe-maps` at archive revision `d818e6c4c001e5fa7ba76e02663a1fb9ce9460fd` in a local working checkout. Read the [candidate README](https://github.com/BAWES-Universe/universe-maps/blob/d818e6c4c001e5fa7ba76e02663a1fb9ce9460fd/map-mocks/lantern-courtyard-03-aligned/README.md), `map/ART-PROVENANCE.txt`, `map/LICENSE.assets.txt` and `map/SOURCES.txt`. Confirm your intended use is covered before copying assets elsewhere.
2. From that checkout's root, run the existing archive check: `python3 map-mocks/tools/validate.py`. Then run the candidate's existing offline check: `node map-mocks/lantern-courtyard-03-aligned/map/validate.mjs`. Save the actual results. The candidate validator checks fixed source relationships, connectivity, assets and mocked script lifecycle; it does not launch Universe.
3. On a local experiment branch, copy the complete `map-mocks/lantern-courtyard-03-aligned/map/` folder into a new `creator-lantern-lab/` folder at the checkout root. Keep the archive unchanged. This location is outside the intentionally excluded `map-mocks/` tree, so it can become a local build input. It is not authorization to publish that branch or map.
4. Open `creator-lantern-lab/lantern-courtyard.tmj` in Tiled. Begin with one small question, such as whether a changed table edge still covers the right avatar pixels while its physical support remains blocked. Inspect `floorLayer`, `coffee-table-base`, `coffee-table-top` and `coffee-table-footprint` before editing. Do not move an image without reconciling its anchor, footprint and mask.
5. Follow the source checkout's [installation instructions](https://github.com/BAWES-Universe/universe-maps/blob/d818e6c4c001e5fa7ba76e02663a1fb9ce9460fd/README.md): its documented setup is `npm install`, and its [package scripts](https://github.com/BAWES-Universe/universe-maps/blob/d818e6c4c001e5fa7ba76e02663a1fb9ce9460fd/package.json) include `npm run build`, `npm run dev` and `npm run prod`. Run the build after the copy/change and confirm the derivative is actually included. Use the installed runtime versions and source lockfile deliberately; record any dependency changes.
6. Run `node creator-lantern-lab/validate.mjs` as a starting regression check. Some expectations are tied to the original coordinates and geometry. If your intentional edit changes one, inspect the failure and update the derivative's assertion to express the new contract; do not simply remove a failing test.
7. Serve with the documented development or production-preview command, then load the derivative using your chosen client's supported map-loading procedure. A Vite preview is a map host, not the Universe client. Record the actual client revision and map URL; if you cannot load it there, stop the runtime claim at “not run.” Walk in front, behind and beside the table, and capture the crossing at normal gameplay scale.

Use the standalone `lantern-courtyard.tmj` for this first exercise. The companion editable TMJ/WAM is a separate editor-entity proposal; merely serving its WAM beside a map does not activate entities. Complete the [experiment record](../templates/experiment.md), including any visual regression, before enlarging the exercise.

## Pick an authoring route honestly

### Authored whole-image room

A composed scene can retain a distinctive look. Gridding it and placing tiles in sequence is largely mechanical. The hard work is drawing accurate collision, foreground, glass, shade and reveal masks against the actual scene.

Use this for a bounded, intentionally authored room when editability limits are acceptable. It does not produce a reusable tileset just because the image has been cut into 32 px cells. Avoid enlarging a small finished painting and claiming that a larger PNG restores source detail.

### Construction from real tiles or modules

Use meaningful wall ends, corners, caps, fronts, thresholds, ground edges and shadow transitions. Maintain an inspected catalog showing each tile/module's visible shape, anchor, footprint, neighboring joins and intended layer.

Place desks, chairs, lamps and props as occupied groups. The visible seat/table edge matters more than the bounding box of transparent sprite padding. A valid GID and a passing optimizer do not show that the selected part is the right piece.

### Coherent offline scene with separated outputs

An orthographic 2.5D scene can provide common perspective, physical contacts and lighting. The Blender studies demonstrated useful camera and lighting separation, but their final art remained too generic. Do not describe that method as an accepted main-world pipeline.

A next bounded experiment could use geometry, object-ID and lighting guides for original painted shapes/materials. Keep diffuse/material design distinct from scene-wide light; otherwise individually baked highlights and shadows will conflict again. Judge the complete native-scale grouping before building an entire environment.

No route removes the need for deliberate gameplay masks or owner visual review.

## Write a layer and footprint contract

For each object or architectural module, specify the following separately:

| Component | What it does | Typical mistake |
|---|---|---|
| Ground and receiver light | Continuous walking surface, material joins, contact shadow and localized light received by the floor | Baking furniture into the floor, or detaching a shadow when the object moves |
| Base/body pixels | Supports, legs and structural parts that should sit below the avatar | Putting an entire rectangular furniture crop above the player |
| Foreground mask | Only the portions that actually cover the avatar: a chair back, canopy, front rim or selected facade | Treating foreground as collision, or expecting static layers to provide arbitrary per-object depth sorting |
| Broad shade overlay | Translucent environmental shade that also darkens a moving avatar | Shading the floor only, or applying the same shade twice |
| Glass | Controlled translucent pane pixels and intentional opaque frames/highlights | Using an alpha PNG without testing whether the face remains readable |
| Removable cover | Roof or facade removed by a defined local reveal state | Hiding permanent structural collision with the roof |
| Collision footprint | Where the player physically cannot move | Blocking all the visible art, transparent margins, a reachable chair position or a doorway |
| Interaction area | Trigger or service region with a defined purpose | Inferring a meeting, portal, bot or permission from a visual sign |

Keep anchors and coordinate conventions in the experiment record. A modular shadow can only move with its caster if its shape, receiver and light direction still make sense. Fixed scene lighting and freely movable furniture are different requirements.

## Pinned Universe behavior: layer hiding can also change collision

The locally inspected Universe source at commit `5e7670be6c79efc575a7193e8a1a1c8c379b293f` places tile layers before the `floorLayer` object group below the player, then switches later tile layers to overlay depth. This is static layer ordering, not a general furniture Y-sort system. See [GameMapFrontWrapper](https://github.com/BAWES-Universe/workadventure-universe/blob/5e7670be6c79efc575a7193e8a1a1c8c379b293f/play/src/front/Phaser/Game/GameMap/GameMapFrontWrapper.ts#L148-L170).

In that same source, `setLayerVisibility` changes visibility **and** calls `setCollisionByProperty({ collides: true }, visible)` before updating the collision grid. Hiding a layer or group through this path can therefore disable its collision. See the [visibility implementation](https://github.com/BAWES-Universe/workadventure-universe/blob/5e7670be6c79efc575a7193e8a1a1c8c379b293f/play/src/front/Phaser/Game/GameMap/GameMapFrontWrapper.ts#L291-L313).

For a roof reveal, place persistent physical boundaries in a separate, non-revealed layer/footprint. Test both enter and leave states. Do not assume “invisible” means “still solid,” or transfer this exact implementation to another engine revision without checking it.

The source inspection is evidence of the pinned implementation, not a claim about the precise build currently deployed in every room.

## Four concrete avatar-overlap examples

A read-only source study on 9 October 2026 examined the supplied Conference Campus map and its script. Its source-pixel crops and offline composites explain the mechanisms below; they were not new gameplay captures or art licensed for reuse. The map's artwork belongs to 100 Roads Design LLC.

Sources: [Conference Campus TMJ](https://workadventure-chat-uploads.s3.eu-west-1.amazonaws.com/upload/map-parteners/partners-162.map-storage.staging.workadventu.re/100-roads/conference-campus.tmj), [compiled map script](https://workadventure-chat-uploads.s3.eu-west-1.amazonaws.com/upload/map-parteners/partners-162.map-storage.staging.workadventu.re/100-roads/assets/main-f267d54e.js), and [script source map](https://workadventure-chat-uploads.s3.eu-west-1.amazonaws.com/upload/map-parteners/partners-162.map-storage.staging.workadventu.re/100-roads/assets/main-f267d54e.js.map). The audited TMJ SHA-256 is `5495f6f502208e486905adea889932e26c14e092d2cc5a3a53848c86ac1934e9`. These hosted URLs may change; the hash identifies the inspected bytes.

### 1. An apparently seated attendee

The full chair is drawn below avatar depth. Its rounded back is redrawn above the avatar, without foreground legs. The head remains visible while the lower body is covered. The audited foreground mask is visibly about 30×30 px inside a 32×64 allocation.

The studied map's 210 chairs occupy 420 collision-free cells. Its script has no seat-specific callback or pose change. The seated appearance comes from a reachable position plus precise layering. That does not establish a general sit-animation API, but a missing such API is not a reason to omit the appearance.

For new art, split the chair base and near backrest, make the intended occupied position reachable, and test it from the available approaches. A decorative chair with an unreachable center does not meet the same requirement.

### 2. A speaker behind a lectern

At zero-based cells `(27,26)` and `(28,26)`, `furniture-fg` contains the upper rim and microphone, GIDs 12670/12671. The pedestal sits below avatar depth one row lower, GIDs 7592/7593. Those lower cells have an independent 64×32 blocked footprint.

A north-side approach lets the avatar reach the base edge while the foreground rim covers its lower pixels. A transparent U-shaped opening in the rim matters; a full opaque rectangle would hide the speaker. Stage blockers leave staircase gaps, so a plausible visual position is also physically reachable.

### 3. Shade that falls on the avatar

The particular diagonal outdoor shadow is in `grounds-fg`, above `floorLayer`, rather than the separately named `shadow-light` layer. Representative interior pixels are RGBA `(40, 0, 79, 77)`, roughly 30% violet alpha, with a partially transparent diagonal edge. It is collision-free.

That overlay shades any avatar pixels crossing the same edge, including partial-body coverage. A floor-only baked shadow cannot do that. Separate contact shadow below the player from broad environmental shade above the player, and apply each contribution once. Do not fully bake broad shade into the floor and props and then darken them again with an equivalent overlay.

### 4. Visible people through revealable glass

The studied exterior glass is partly in the lower portion of `building2-roof`, above the avatar. At representative cell `(37,56)`, most pane pixels have alpha 125–132, approximately 49–52%, with opaque frame pixels. A lower strip is in `building2-walls`, below the avatar. The physical wall has its own blockers and doorway gaps elsewhere in the footprint.

Entering `building2-zone` hides the roof, walls layer and sign; leaving restores them. Other furniture, shade and dedicated collision remain. This reference therefore uses selected facade/glass reveal, not permanent glass over every interior view. Script visibility changes are local to each viewing client, not shared-state writes.

Design both outside-looking-in and inside-looking-out states. Keep enough rear/perimeter structure to preserve the building, remove obstructing cover intentionally, and verify actual avatar readability. Alpha presence alone is insufficient.

## Collision validation should follow routes and objects

The earlier automatic-collision result of approximately 89% overall tile agreement was overstated because the benchmark was dominated by open floor. Record false blockers and missed obstacles separately, then walk the important routes.

At minimum, check spawn to entrance, entrance to receptionist, shared work area, glass-room doorway, occupied chair position, speaker position, and the return route when those uses exist. Approach walls and furniture from relevant sides. Test corners and narrow gaps. Repeat after reveal transitions and after any art/footprint change.

Use explicit intended masks or reviewed drafts. Color, darkness and texture can suggest a draft, but a shadow is not a wall and translucent glass is not necessarily walkable.

## Keep ambience, conversation and service integration distinct

**Quiet ambience must not be implemented with the generic Tiled `silent` property.** In the preserved connected StudentHub proof, `silent: true` disabled proximity conversations. The roofless derivative removed it. A quiet shared office should retain people's conversation while avoiding unwanted map audio.

Treat these as separate test cases:

- Ambient audio loads from the intended deployment, loops correctly and is heard at a suitable level.
- Proximity conversation still works in the relevant area and across its boundaries.
- Meeting, presentation or interaction behavior works in the actual room configuration.

A TMJ, visual sign or public map URL does not demonstrate native room/WAM configuration, live occupants, an Explore destination, broadcasting, account links or bots. Within-map movement and inter-room navigation also need different evidence. Do not label a portal live until its destination and return route have been verified.

## Reuse the archive without rewriting history

Start with the [pinned archive index](https://github.com/BAWES-Universe/universe-maps/blob/d818e6c4c001e5fa7ba76e02663a1fb9ce9460fd/map-mocks/README.md), then the chosen candidate's README, provenance, `template.json` and checksums. Copy the candidate to a new named derivative and keep its complete map/assets folder together.

The archive records fourteen entries and keeps every candidate `catalogReady: false`. It does not populate the live template list. Important constraints include:

- The three StudentHub interior proposals are visual-only; no TMJ should be invented for their historical entries.
- Both StudentHub Tiled candidates need explicit visibility booleans on three area objects for the recorded pinned import schema. Fix derivatives, not frozen originals.
- The connected-glass proof retains its known `silent` bug. The roofless derivative removes that bug but remains unaccepted as the main-world direction.
- The arrival lighting study has packed Blender sources but no gameplay export or play link.
- Art provenance and redistribution rights remain attached to each asset; reference inspection grants no reuse rights.

The archive includes a real [validator](https://github.com/BAWES-Universe/universe-maps/blob/d818e6c4c001e5fa7ba76e02663a1fb9ce9460fd/map-mocks/tools/validate.py). Its README documents running `python3 map-mocks/tools/validate.py` from the **universe-maps repository root**. That is an archive integrity/source check, not a command supplied by this creator kit or a substitute for a gameplay walk.

## A useful final review packet

Provide the editable source and exact revision, one native-scale overview with the real avatar, a matching normal-gameplay view, and close evidence for the features actually changed. For a layered room, include the same avatar crossing shade, behind glass, at a chair and at the lectern, plus both roof states and collision checks.

State whether each image is a source crop, offline composition, harness capture, full-client screenshot or multiplayer observation. Finish with the owner's visual decision and a short list of failed, blocked or unrun checks. Use [Validation](validation.md) and the [experiment template](../templates/experiment.md).

The main-world art problem is still open. A technically coherent but generic maquette is useful research, not an aesthetic upgrade by default.
