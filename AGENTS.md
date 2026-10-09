# Guidance for agents

This repository is a docs-first knowledge kit for AI-assisted map, Woka, and asset creation for BAWES Universe and WorkAdventure. Its purpose is to make creative work reproducible, preserve useful evidence, and avoid repeating known failures.

## Read first

1. [README.md](README.md) for scope and current limitations.
2. [Evidence status](docs/evidence-status.md) for claim labels.
3. The relevant [map](docs/maps.md) or [Woka](docs/wokas.md) guide.
4. [Experiment history](docs/experiment-history.md) before choosing an approach.
5. [Validation](docs/validation.md) before describing a result as tested or ready.

Read task-specific instructions in the target source repository as well. This kit does not replace them or grant permission to change that repository.

## Working rules

- Establish the requested outcome, allowed changes, target environment, and visual reference before implementation.
- Inspect the actual source and images when available. Say when a finding comes only from an earlier report or screenshot.
- Pin source repositories to a commit and record relevant tool/runtime versions. Do not silently substitute a newer branch.
- Identify the exact product or fork under test. Do not infer Universe/WorkAdventure compatibility from shared ancestry or a test in only one implementation.
- Test a small representative example before scaling the approach across a full map or avatar set.
- Keep collision, draw order, shadow treatment, and visual acceptance as separate checks.
- Preserve original snapshots. Make derivatives in a clearly named location and record their parent source.
- Record failed attempts with observable symptoms and evidence. Separate a suspected cause from a demonstrated cause.
- Retest affected behavior after changes. Never turn a planned check, static inspection, or historical result into a fresh runtime pass.
- Respect source licenses, privacy, and access boundaries. Do not copy secrets, private conversations, or assets with unresolved redistribution rights into this kit.
- Keep docs independent of any single agent vendor. Keep the shared installable skill small and point to canonical guides rather than copying them into every adapter.

## Repository scope

There is no application runtime, application dependency setup, test runner, or CI pipeline supplied by this starter. Do not invent commands or describe checks as automated unless an actual implementation is added and run.

The optional [creator skill](skills/universe-creator/SKILL.md) can be installed with the separately maintained `skills` CLI. Its installation provides instructions, not application dependencies or runtime access. Keep [agent setup](docs/agent-setup.md) consistent with the actual package and verified installer behavior.

Do not add a package manager, framework, asset bundle, generated website, or agent integration merely to edit the documentation. Use relative links for files in this repository and commit-pinned links for source evidence when possible.

Creating documentation does not authorize remote publication, a merge, deployment, asset redistribution, or changes to access permissions. Follow the current task's authorization for those actions.

## Before handing work back

- Check that every changed document has a clear purpose and useful next step.
- Check local file links and heading links, including links to newly added files.
- Review claims against their cited source and stated evidence status.
- List checks performed, checks that failed, and checks that were not run.
- State remaining visual, runtime, licensing, or access blockers plainly.
- Include the changed files and any decision the reviewer needs to make.

Use [Contributing](CONTRIBUTING.md) and the [experiment template](templates/experiment.md) for the complete contribution flow.
