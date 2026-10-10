# Contributing

Make the next creator's work easier. A useful contribution explains what was tried, preserves the source, and gives someone else enough evidence to reproduce or challenge the result.

Small, focused contributions are welcome: one recipe, one corrected claim, one failure analysis, or one tested improvement.

## Choose the right place

- Update the [map guide](docs/maps.md) or [Woka guide](docs/wokas.md) for reusable methods.
- Add reviewable map/Woka revisions to the [versioned catalogue](docs/catalogue/README.md) using the [map record](templates/map-record.md) or [Woka record](templates/woka-record.md). Keep stable IDs, parents, dated feedback, provenance and exact source links; preserve rejected versions.
- Update [experiment history](docs/experiment-history.md) for a specific attempt and its outcome.
- Use the [experiment template](templates/experiment.md) for a new reproducible record.
- Update [validation](docs/validation.md) when the review process itself improves.
- Keep agent setup instructions in [agent setup](docs/agent-setup.md); keep the underlying method in the shared guide.

## A simple contribution flow

1. **Name the question.** State the problem, intended result, and smallest example that will answer it.
2. **Check the history.** Link related attempts and explain what is different this time.
3. **Pin the inputs.** Record repository, commit, source paths, tool versions, asset provenance, and relevant configuration.
4. **Make a separate derivative.** Preserve the original evidence and identify what changed.
5. **Run the relevant checks.** Follow the [validation guide](docs/validation.md). Record actual commands only when they were run in the stated environment.
6. **Write the result.** Include evidence, limitations, and a precise [evidence status](docs/evidence-status.md). A useful failed attempt is worth keeping.
7. **Request review.** Use a focused pull request when the repository is available. Include a reproduction path and distinguish completed checks from checks needing another environment or person.

A documentation review can establish that a recipe is clear and sourced. Promoting the underlying asset or behavior requires its own runtime and visual checks.

## Minimum information for a new experiment

- Goal and explicit acceptance criteria.
- Parent source with an immutable revision or content hash.
- Changed files and exact reproduction steps.
- Tools, versions, target runtime, and relevant settings.
- Asset creator/source, license or permission, and redistribution restrictions.
- Screenshots or recordings with enough context to identify the tested revision and view.
- Technical, runtime, and visual results recorded separately.
- Known defects, checks not run, and the next useful test.

Use `unknown` or `not recorded` where necessary. Missing information is a limitation to fix, not a reason to invent a value.

## How to document a failure

Be specific and fair. Describe the visible or measurable problem, the circumstances, and the evidence. For example, “the avatar remains in front of the podium at this position” is stronger than “the layering is broken.”

Keep these parts separate:

- **Observation:** what happened and where it is visible.
- **Interpretation:** why it may have happened, with confidence stated.
- **Decision:** whether the attempt was rejected, paused, or kept for a narrower purpose.
- **Next test:** the smallest change that could confirm or disprove the interpretation.

Apply the same standard to human and agent work. Name the tool/model/version only when it was recorded and relevant. Do not infer a tool's capabilities from one attempt, invent prompts, or publish private transcripts as a substitute for a clear experiment record.

## Assets, rights, and privacy

This starter does not select a repository-wide license. A maintainer must choose the terms for original documentation and code before presenting the repository as openly licensed. Third-party assets retain their own terms.

- Prefer a fixed source link over duplicating large binaries.
- Copy an asset only when its license or specific permission allows the intended use and redistribution.
- Keep required attribution and notices with approved copies.
- Flag unclear provenance. Do not describe an unresolved asset as safe to publish.
- Remove credentials, signed/private download URLs, account details, private chat exports, and unrelated personal information from logs and screenshots.
- Check that intended readers can access linked sources. A private link may be appropriate, but label the access requirement.

## Pull request checklist

- [ ] The purpose and scope are clear.
- [ ] Relevant earlier work is linked, including failed attempts.
- [ ] Sources are pinned and provenance is recorded.
- [ ] Evidence labels accurately distinguish fresh tests from historical reports.
- [ ] Technical and visual results are separate.
- [ ] Failed, blocked, and unrun checks are visible.
- [ ] Local links resolve and navigation includes new material.
- [ ] Assets and screenshots have an appropriate rights/privacy review.
- [ ] No unrelated runtime, dependency, or large-asset changes were added.
- [ ] Any requested promotion, publication, or deployment is stated explicitly for review.

