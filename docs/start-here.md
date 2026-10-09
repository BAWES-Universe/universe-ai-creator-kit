# Start here

This kit helps a creator move from an idea to a small, reviewable result without losing the reasoning or evidence along the way. It works as a handbook for people and as task context for AI agents.

You can browse the Markdown files directly. No build or installation is required for the handbook. Making a map or Woka still requires the appropriate source files, authoring tools, runtime, and access.

Working with an AI agent? [Install the shared creator skill](agent-setup.md#install-the-skill), then come back here for the workflow.

## 1. Choose a small outcome

Write one sentence describing what the next experiment should demonstrate.

Useful examples:

- A player can cross a doorway with the intended collision and foreground treatment.
- A chair or podium covers the correct part of an avatar at specific positions.
- One avatar change remains aligned across the required animation frames.

Keep the scope small enough to inspect properly. A full location or avatar collection is harder to evaluate when the underlying method is still uncertain.

## 2. Read what already happened

Start with [experiment history](experiment-history.md), then the [map guide](maps.md) or [Woka guide](wokas.md).

For map work, the [archive at the pinned source revision](https://github.com/BAWES-Universe/universe-maps/tree/d818e6c4c001e5fa7ba76e02663a1fb9ce9460fd/map-mocks) preserves 14 entries: 10 Tiled candidates and four visual/art studies. Some attempts were rejected; some retain known defects. The archive exists to preserve the evidence, and inclusion does not make an entry ready for use.

Read the candidate's own notes and provenance before reusing it. Identify whether the source is an editable map, a static composition, or an offline art study. Each supports different claims and tests.

## 3. Set the reference and acceptance criteria

For visual work, identify an explicit reference or an approved earlier result. Describe what matters: avatar scale, perspective, depth, material readability, lighting, silhouette, or animation continuity.

Define technical and visual checks separately. A correct file can still look wrong; a convincing screenshot can still fail in motion or multiplayer.

Record criteria before creating a new image or implementation. If there is no agreed visual reference, make the reference decision part of the small experiment rather than claiming final visual acceptance.

## 4. Confirm the source and environment

Record the source repository, exact commit, relevant paths, authoring tool version, and intended runtime. Identify whether the target is BAWES Universe, WorkAdventure, or another explicitly named fork. For Wokas, verify the actual asset/animation contract before choosing dimensions, frame order, naming, or composition rules.

Check compatibility against that implementation. A recipe tested in one fork is not automatically verified in another, even when file formats or terminology look familiar.

Check access and licensing. Reading this kit does not grant access to a private source repository, authorize redistribution, or install the tools needed to run it.

Use the target repository's existing setup and validation instructions. The skill installer loads creator guidance; it does not replace the target project's own runtime setup or run commands.

## 5. Make a named derivative

Preserve the source snapshot. Put your changes in a separately named experiment and identify its parent source.

Keep required assets together or document exactly how to obtain them. Avoid dependencies on a creator's temporary files, private absolute paths, or expiring links. Link large source assets rather than duplicating them into this handbook.

Use the [experiment template](../templates/experiment.md) while you work so reproduction details are not lost.

## 6. Test the actual result

Follow [validation](validation.md). Inspect source validity, runtime behavior, and visual quality at the smallest useful scope.

For depth work, show the avatar at multiple positions around the object and moving across its boundary. For avatar work, inspect all frames and directions required by the target runtime. Record what was run and what remains untested.

If a test fails, preserve the evidence. Fix it in the derivative or document a narrower conclusion. Do not relabel a failed visual direction as ready because its files load successfully.

## 7. Hand it to another creator

Ask a teammate or another agent to reproduce the result from the record alone. Have them report missing inputs, ambiguous steps, and differences from the expected outcome.

Update the record and assign an accurate [evidence status](evidence-status.md). Follow [Contributing](../CONTRIBUTING.md) to propose the change.

## What a first useful result looks like

A small source change, clear reproduction steps, a few informative screenshots or a short recording, a list of checks, and an honest outcome are enough. A failure with good evidence can save more time than a polished image with no reproducible source.

[Back to the kit](../README.md) · [Set up an agent](agent-setup.md)
