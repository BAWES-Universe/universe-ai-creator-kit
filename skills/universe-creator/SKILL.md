---
name: universe-creator
description: Create BAWES Universe and WorkAdventure maps, Wokas, and visual assets through a brief, references, a small validated prototype, and evidence-led iteration. Use for creator tasks and reviews in these workflows.
---

# Universe Creator

Help a person turn a BAWES Universe or WorkAdventure creation idea into a small, inspectable result, then improve it from evidence. Use the same entry point for maps, Woka avatars, and reusable visual assets. Verify the exact product, version, and fork; findings from one runtime do not establish compatibility with another.

This is an instruction-only skill. It supplies no engine, source assets, generation credits, credentials, or permission to publish. Installing or invoking it does not authorize paid generation, uploading private source material, changing a live world, or merging work. Use the current task's actual permissions and the host's approval controls.

## Start with a brief

Use what the person has already provided. Ask only for missing decisions that change the work:

- **Create:** map/scene, Woka/avatar, or visual asset; intended user experience and one concrete outcome.
- **Source:** available repository or files, exact revision, target runtime and authoring tools.
- **Look:** a reference image or approved example, plus what to preserve or avoid.
- **First proof:** the smallest useful prototype and its separate visual and technical acceptance checks.
- **Bounds:** permitted files/actions, available tools, time or paid-generation limit if relevant.

When source access or a runtime is missing, produce an honest brief or concept proposal using the available inputs. Identify the missing check; do not invent source dimensions, API contracts, commands, or test results. Do not make the person fill a large form before helping.

## Load only the relevant handbook context

The canonical handbook lives in [BAWES-Universe/universe-ai-creator-kit](https://github.com/BAWES-Universe/universe-ai-creator-kit). A skill installer usually copies only this skill directory, not the rest of the repository. These absolute links work independently of the installed location:

- Shared workflow: [Start here](https://github.com/BAWES-Universe/universe-ai-creator-kit/blob/main/docs/start-here.md).
- Maps and scene assets: [Map creation](https://github.com/BAWES-Universe/universe-ai-creator-kit/blob/main/docs/maps.md).
- Wokas and avatar assets: [Woka creation](https://github.com/BAWES-Universe/universe-ai-creator-kit/blob/main/docs/wokas.md).
- Prior approaches and failures: [Experiment history](https://github.com/BAWES-Universe/universe-ai-creator-kit/blob/main/docs/experiment-history.md).
- Checks and claim labels: [Validation](https://github.com/BAWES-Universe/universe-ai-creator-kit/blob/main/docs/validation.md) and [Evidence status](https://github.com/BAWES-Universe/universe-ai-creator-kit/blob/main/docs/evidence-status.md).
- Recording a result: [Experiment template](https://github.com/BAWES-Universe/universe-ai-creator-kit/blob/main/templates/experiment.md).

Use a supplied local checkout of these documents when available. `main` links are discovery links, not immutable evidence: record the kit revision you actually use, and pin source citations in the experiment record. Read the target source repository's own instructions too. If a handbook link cannot be read, say so and use the self-contained workflow below; do not pretend its contents were loaded.

## Brief → reference → prototype → validate → iterate

1. **Set a visible target.** Inspect supplied reference images and actual source files before choosing an approach. Convert the look into a few observable criteria such as avatar scale, readable depth, silhouette, material separation, or frame alignment. Identify reference/licensing constraints.
2. **Choose a small proof.** Prefer one doorway or object-depth test, one avatar component across its required frames, or one asset at its intended scale. Preserve originals; give the derivative an explicit name and parent source. Read relevant failed attempts before repeating an approach.
3. **Build within the brief.** Follow the actual runtime/asset contract. For maps, treat collision, occlusion, shadow placement, and art quality as separate concerns. For Wokas, inspect the real sheet/layer dimensions, frame layout, naming, directions, and animation contract before editing. For assets, identify the consuming map or avatar contract, then check scale, perspective, alpha edges, palette/lighting, tiling or animation as applicable.
4. **Validate the prototype.** Check files/references and the target runtime when available. Inspect images at the intended viewing scale. For depth, move the avatar in front of, behind, and across the tested boundary; a still image cannot establish movement behavior. For animation, inspect every required frame/direction and transitions. A parse or build pass does not establish visual quality, multiplayer behavior, or user acceptance.
5. **Review and iterate.** Show the person the smallest useful visual proof with observed results and limitations. Change one meaningful hypothesis at a time and retest affected behavior. Continue within the agreed scope; expand to a full scene or set only when the small proof meets its stated criteria and that expansion is authorized.

## Preserve useful evidence

Label each consequential claim at its actual scope:

- **Verified in the stated environment:** you ran and inspected the named check on identified inputs; include versions, date, evidence, and limits.
- **Historical / reported:** an earlier record says it worked or failed; include its source and do not call it a fresh pass.
- **Experimental:** an implementation exists but relevant validation remains incomplete.
- **Unverified:** a proposal, assumption, or inference without adequate evidence; state the next useful check.

Keep outcome separate: accepted for a named purpose, needs revision, rejected for a direction, or not reviewed. Preserve failures with the approach, observable symptom, evidence, and next test. Do not promote an archived experiment or attractive render to a ready-to-use map. An art-only study has no implied TMJ, play link, collision, or multiplayer validity.

## Hand back a reproducible result

Deliver the changed source or artifact, a concise visual comparison when available, exact reproduction steps, checks run with outcomes, checks not run, and the next decision. Record source revisions and provenance. Keep source assets in their authorized repository rather than silently republishing them with this skill. A teammate should be able to reproduce the result without private temporary paths, secrets, or unstated inputs.
