# Experiment history: keep the failures with the successes

This is a working record of what was tried, what it established, and what remains unproved. It prevents the next contributor from repeating a rejected direction or presenting an old proposal as a finished pipeline.

**Evidence cut: 9 October 2026.** The early sprite and map histories below summarize two owner-supplied research briefings, 7 October 2026. Their measurements and outcomes are **reported historical results**, not benchmarks rerun for this kit. Later map entries use the preserved archive and source studies. Private conversation exports are not included.

Use [Wokas](wokas.md) and [Maps](maps.md) for practical guidance, and [Evidence status](evidence-status.md) for the distinction between a report, inspected source, a build, a runtime test, and owner acceptance.

## 1. Woka research: twelve approaches, not one successful prompt

The historical target was a 96×128 RGBA PNG containing twelve 32×32 frames: three columns and down/left/right/up rows. That shape is consistent with the pinned loader and animation source inspected for this kit; it is not permission to assume every future engine revision has the same contract.

| # | Experiment | Reported outcome and useful lesson |
|---|---|---|
| 1 | Ask an image model for native 32×32 pixel art | It returned artwork around 130 px tall. Reducing it destroyed the face. Prompt wording did not enforce native pixel construction. |
| 2 | Request an explicit block grid, with each pixel a 16×16 block | The model antialiased block edges. Reported pitch fidelity was 0.42, rather than approximately 1.0 for lossless division. A pictured grid was not a reliable sampling grid. |
| 3 | Ask for a smaller figure | Requests for 40, roughly 100, and 120 px produced figures reported at 321, 277, and 736 px respectively. Numeric size instructions did not control the source silhouette. |
| 4 | Generate all twelve poses in one sheet | This gave the strongest identity consistency of the compared image-model attempts, attributed to shared attention in one generation. Figures were still about 270–330 px tall, requiring roughly 8–10:1 reduction. |
| 5 | Generate one directional row at a time, using identity anchors | The briefing names `aldegad/sprite-gen` v2.2.0, revision `ed960ac2`. Extraction was deterministic, but the character widened and narrowed between rows. That external revision was not independently recovered or rerun for this kit. |
| 6 | Local SDXL plus a pixel-art LoRA through ComfyUI on a 3090 | Genuine pixel texture appeared, but backgrounds would not matte cleanly, some frames broke, and faces were crude. The result was judged worse than the earlier R1 candidate. This was an actual reported experiment, not merely a suggestion to try local diffusion. |
| 7 | Klein/Flux twelve-frame ComfyUI workflow | Image-to-image at denoise 0.6 produced ghost faces and melted features. A grid-template attempt packed more than thirty characters into one cell. These settings describe the failed trial, not a recommended current recipe. |
| 8 | Zero-shot GPT-6 Astra with free choice of method and self-review | Three sheets were generated; the agent rejected two. The delivered 96×128 sheet had twelve colors and reported 100% dark-boundary and outline-continuity scores. Its black-and-white face still read as an insect. Numerical cleanliness did not imply a good character. |
| 9 | Three hand-authored face repairs | All three were rejected. Painting over noisy source detail, repeating a face stamp, and white eye blocks created bars or the same insect appearance. A clean skin field with a few dark feature pixels was more promising than tiny eye whites. |
| 10 | Custom conversion pipeline | A reported result measured 21 px wide, 533 ink pixels, nineteen colors, and 100% for both dark-boundary and continuity. It passed that experiment's gates and had a clean face, but remained plainer than the PIPOYA comparison. |
| 11 | Orthogonal “construction” prompting | Asking for large axis-aligned rectangles and deliberate stair-step corners was the largest reported prompting improvement. The first result measured 22 px wide, 584 ink pixels, 94.4% dark-boundary and 65.6% continuity. Replicates reached 95.3%/76.7% and 88.6%/60.2% for those last two measures. Width and ink still fell short of the chosen hero reference; faces remained soft. |
| 12 | Twenty-five-candidate sheet process | The briefing describes `make_woka.sh sheet/build`: one generated sheet, twenty-five designs, automated slicing, matting and reduction. A Kuwaiti pearl merchant retained a dallah and finjan in all four directions and reportedly passed the experiment's gates. A movement measurement of 213 px/frame was recorded without enough metric definition to reuse as a present acceptance threshold. |

### What the numbers actually compare

The reported front-standing PIPOYA Male 01-1 reference was 26 px wide, 647 ink pixels, forty colors, 88.3% dark-boundary and 73.8% continuity. The reported 300-sheet cohort medians were 24 px, 576 ink pixels, twenty-eight colors, 95.35% and 55.43% respectively. A result can beat one reference measure while still falling short of the cohort or of the visual target.

For context, the previously shipped sprites were reported at 21 px wide, 482 ink pixels, twenty-nine colors, 79% dark-boundary and 28% continuity, and were rejected as too small and flat. An earlier v1 attempt was 11 px wide with 238 ink pixels and sixteen colors. R1, before construction prompting, reached 24 px and 608 ink pixels. These are different candidates, not a continuous performance chart from a standardized benchmark suite.

Metric definitions, input hashes, extraction code and the full cohort were not recovered for this documentation pass. Do not compare fresh measurements to these values without first reconstructing the same methods. No single score substitutes for seeing the face, proportions, clothing and animation at native scale.

### Conversion was a major source of damage

The briefing identifies area-average reduction at about 10:1 followed by thirty-two-color median-cut quantization as a major cause of muddy outlines, skin and cloth. A two-stage reduction, smooth to 4× the target then exact nearest-neighbor to the final size, combined with a curated nineteen-tone palette containing four useful skin tones, reportedly removed much of that blur.

Other reported improvements were:

- Real chroma matting with fringe unmixing rather than a simple color threshold, which left magenta specks.
- Aspect-preserving height fitting rather than stretching every crop into a square.
- Connected-component slicing and one scale shared within each directional row. Per-frame scaling caused width/weight jitter; one scale for an entire sheet could leave a smaller row underfilled.
- Luma contrast repair, palette snapping and a one-pixel dark outline, with one continuity measure rising from 0.19 to 0.95. This was a measured trial, not a universal instruction to outline every style.
- Adding four brass palette entries so the merchant's coffee pot and cup did not collapse into skin colors.
- Checking the generated face before applying a manual face pass. In a direct comparison, the original bearded face was more recognizable than the stamped replacement.
- Exporting animation previews from the finished texture, so the preview could not conceal conversion errors.

The named converter, `gridgen`, `make_woka.sh`, `verify_wa.py`, and `MODEL-PLAN-CONTEXT.md` are historical tool references. Their executable implementations and full provenance have not been recovered into this kit. This document does not provide invented commands for them.

### The validator also failed

The historical `verify_wa.py` once returned “ALL PASS” for a 48×64 file. A test that only checks for the absence of a detected error can validate the wrong artifact. Require positive assertions for exact dimensions, RGBA/alpha behavior, twelve populated cells, the intended row/column order, and the content being measured.

Within-row ink swing was reported at 13.45% for one generated result versus 3.36% for PIPOYA. This is a useful warning about animation consistency, but not a current universal pass/fail limit.

### Historical decisions that must not become standing instructions

The briefing required raw-visual approval before conversion and preferred one decision per comparison image, with a default Woka at native size and an enlarged nearest-neighbor view. Preserve that as the review process used in those experiments. It is not an evergreen authorization rule for all future work.

At that time, choosing between the current 32 px quality ceiling and a 64×64 engine change was still pending, as was a base-character choice. The briefing also proposed composing 20–50k labeled sheets from a 277-part library, training completion from one hero frame plus twelve pose maps, and only later revisiting native hero generation. None of those proposals is established here as a completed training run, an approved roadmap, or a present request. Avoiding disappearing identity props, described through SSD's disappearing-gun example, was the central proposed consistency risk.

## 2. PixelLab: researched, not exercised

The second owner-supplied research briefing, 7 October 2026, explicitly says no hands-on PixelLab sprite-generation test was run. It reported documentation for reference-driven characters, directional rotation, text-directed animation, optional transparency, and rough-correction/regeneration loops. It also mentioned advertised skeleton controls.

The historical feature notes described eight directional views; 16×16, 32×32, 64×64 and 128×128 Rotate canvases; sixteen frames in a 4×4 sheet for 32/64 px animation inputs; and four frames in a 2×2 sheet for larger inputs up to 256 px. These vendor details are **unverified historical claims**, not a current product specification or an endorsement.

Even if those outputs are available, they need adapting to the target Woka contract. Generating animation art does not route the character, choose a seat, face a conversation partner, anchor its feet, slow it on arrival, or fix camera staging. The briefing's camera/table problem belonged to routing and staging, not to missing animation artwork. PixelLab and Retro Diffusion remain candidates to evaluate under a bounded test, not already-validated production dependencies.

## 3. Froggy's map experiments

Source: owner-supplied research briefing, 7 October 2026. These are reported outcomes from earlier work; the kit did not independently rerun those specific scenes or collision benchmarks.

| Method | What worked | Failure or limit |
|---|---|---|
| Whole-image / Nano Banana workflow | Generate a top-down scene, fit it to a 32 px grid, use it as an image-backed tileset, and place its cells in order. Conversion was reproduced on the owner's existing `empty.png`; spawn and map properties could be automated. | Sliced picture fragments do not become reusable architecture. Foreground masks and collision still require interpreting the scene. Good for an authored one-off room when those masks are deliberate. |
| Code-built maps from existing WorkAdventure/BAWES tilesets | Explicit rooms, walls, furniture, doors and zones produced an editable TMJ. A courtyard passed the official optimizer and renderer. A focus room was revised to one doorway; meeting/work layouts improved. Animated tile metadata and remapped frame IDs survived optimization. | Early layouts looked like generic technical offices: repetitive walls, disconnected furniture and weak composition. A valid tile ID can still be the wrong visual piece. |
| Midjourney complete scenes | Mood, composition and concept presentation were strong; some map loading and zone plumbing was demonstrated. | The rendered/illustrated look did not match the established pixel-art maps. Gradients, glass and shadows confused collision inference; large regions were blocked incorrectly while apparent solid objects remained walkable. |
| Midjourney “tileset sheets” | Produced an image with a visible grid. | Trees, pools and furniture crossed cell boundaries, and cut cells did not join predictably. A drawn grid did not create tile semantics or seamless edges. This route failed as a reusable tileset generator. |
| Aggressive palette reduction and a small simplified tile vocabulary | Produced a small asset set. | Detail and shading were destroyed. The comparison map had many specialized tiles and layers; the replacement had very few pieces and essentially one visual layer. It read as flat colored blocks. |
| Automatic collision from color, darkness, edge/texture density and cleanup | Combining color and texture improved the reported benchmark over either signal alone. | Approximately 89% overall tile agreement was misleading because most cells were open floor. False blockers, missed walls and wrong doorway/corridor connectivity remained. Matching the blocked-cell count did not mean matching the obstacles. |

The earlier “90% of the way there” characterization of collision inference was explicitly corrected in the briefing. Treat image-derived masks as drafts needing obstacle-class and route-level review. Overall agreement is particularly weak evidence on mostly empty maps.

Individual-tile generation followed by curation, hybrid reliable structure plus generated showpieces, semantic segmentation, human-painted color masks compiled into layers, and specialist pixel tools were proposed but not established as completed successes.

The durable map lessons were concrete: use wall ends/corners/tops/front faces, ground transitions with correct edges and shadows, purposeful furniture clusters, reachable doors and continuous routes. Foreground controls what covers a person; collision controls where the person can stand. A passing build proves neither composition nor enjoyment.

### Map Studio is a related editor project

[BAWES/map-studio](https://github.com/BAWES/map-studio) is a separate historical project, not this creator-kit repository. Its [README at revision 7595a12](https://github.com/BAWES/map-studio/blob/7595a1275f19bf1af0ac091fb272ddd6d888d72c/README.md), inspected on 9 October 2026, describes a Next.js/Supabase visual editor and claims AI layout, layers, collisions, TMJ export, cloud sync and GitHub deployment features. Repository existence and that README were verified; those advertised workflows were not exercised in this pass. Do not infer production readiness, a live connected backend, or compatibility with the pinned Universe engine from its feature list.

## 4. The preserved Universe map sequence

**10 October 2026 update:** [current archive](https://github.com/BAWES-Universe/universe-maps/tree/03d83f2dd74108a6f75847bd2f7d03c5d619c950/map-mocks) contains 26 records. See the [versioned catalogue](catalogue/README.md) for the expanded inventory, later Gate/Campus versions and named Woka histories. The original fourteen-entry snapshot and its historical checks below are retained unchanged.


The [map-mock archive](https://github.com/BAWES-Universe/universe-maps/tree/d818e6c4c001e5fa7ba76e02663a1fb9ce9460fd/map-mocks) contains fourteen entries: ten Tiled candidates, three visual-only proposals, and one offline art/lighting study. The snapshot is associated with [universe-maps PR #3](https://github.com/BAWES-Universe/universe-maps/pull/3); archiving does not establish merge, deployment or live catalog acceptance. Use the pinned snapshot rather than assuming the PR's current head is unchanged.

| Preserved entry or family | What to retain from it | What not to infer |
|---|---|---|
| Lantern Courtyard: original, depth proof, aligned olive beds | The sequence separates whole-scene appearance, layer/footprint corrections and alignment corrections. Each version is retained rather than replacing the record of what failed. | Offline checks and historical harness captures are not current full-client, multiplayer or physical-device acceptance. |
| Butterfly Town v1, then scenery/water v2 | V1 has the stronger magical atmosphere and coherent arrival composition. V2 records scenery/water changes and a partial pre-water checkpoint. | V1's enlarged/baked-art and geometric problems were not erased by its visual strength. The partial checkpoint is not a standalone recoverable map. |
| Butterfly Campus v3 dark, v3 light, monumental gate journey | Distinct snapshots preserve the rejected dark direction, lighter revision, and gate/reveal work. | Better mechanical organization does not validate flat or disconnected campus art. The dark version also preserves a historical return-portal overlap. |
| StudentHub connected-glass proof | Connected workspace and reveal/layer experiments remain inspectable. | The main-world art was rejected as flat and pasted. The frozen map also contains the conversation-disabling `silent: true` defect. |
| StudentHub first, refined-dark and light interior proposals | Three visual compositions preserve the evolution of furniture/layout choices. | They never had TMJs. A compositor and image must not be relabeled as a playable map. |
| StudentHub roofless outdoor office | A separately preserved future room/hangout candidate removes the roof, reveal script and erroneous `silent` property. | It is not the accepted main Universe office, live template, or proof of multiplayer seating. It still needs the documented import-schema fixes in a new derivative. |
| StudentHub arrival art/lighting study, including brown maquette | Packed Blender scenes retain calibrated native projection, common lighting, material experiments and the failure diagnosis. | The final result remained too regular and generic. It has no TMJ or play link, and its unvalidated compiler/harness was excluded from the archive. |

The archive's own verification records fourteen folders, twelve canonical TMJs across the ten Tiled candidates, 217 local references checked, unchanged canonical hashes, reproducible outputs for four included compositors/builders, and unchanged published build inputs. These are archived verification results, not fresh runtime tests performed by this kit. Both StudentHub TMJs retain area objects missing explicit visibility booleans and are rejected by the recorded pinned import schema. Preserve the originals; fix a named derivative.

## 5. The main art problem remains open

V1 and the monumental gate remain the atmosphere comparison. Splitting the campus into independently generated assets made it more editable but lost common light, material joins, scale relationships and contact shadows. The connected proof improved access while still looking like cutouts on a repeated texture. Changing global colors, sharpening, adding flowers or adding a dark vignette did not solve that relationship problem.

The offline Blender feasibility check established a narrow result: an orthographic camera could match the 32 px world footprint, and separate floor/receiver-light and object renders recomposed closely to the combined render. It did not prove painterly style, avatar shading, roof-state lighting or playable occlusion. The later arrival study used a coherent scene and original material textures, yet remained a generic maquette rather than the requested magical world.

The proposed next art test is bounded: one original painted threshold vignette using calibrated geometry/light guides, with architecture, planting, a water corner and a compact occupied furniture group. This remains a proposal. It is not an accepted recipe or permission to generate another whole campus. Carry the next result in the [experiment template](../templates/experiment.md), with visual acceptance and runtime evidence recorded separately.

## 6. What deserves a new experiment

- Recover the actual sprite converter/gridgen sources and their input/output hashes before claiming reproducibility.
- Test a specialist sprite tool with the same character and final twelve-frame target, rather than comparing promotional examples to a native Woka.
- Evaluate collision masks by missed obstacles, false blockers and route connectivity, not just aggregate cell agreement.
- Demonstrate the same avatar shaded by an overhead alpha mask, visible through glass, apparently seated behind a chair back and positioned behind a lectern rim.
- Keep roof/facade reveal independent from persistent collision and deliberately handle lighting in each visibility state.
- Find an art method that is genuinely better than v1 at native gameplay scale before scaling production to a full world.

None of these open questions is silently marked solved by this documentation.
