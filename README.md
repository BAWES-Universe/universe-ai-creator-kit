# Universe AI Creator Kit

**AI-assisted creation for BAWES Universe & WorkAdventure.**

Build maps, Woka characters, and assets with reusable skills, practical workflows, and lessons from real experiments. Made for human creators and the AI agents working alongside them.

[Get started](#get-started) · [Maps](docs/maps.md) · [Wokas](docs/wokas.md) · [Experiment history](docs/experiment-history.md)

## Get started

From your project folder, install the shared creator skill:

```sh
npx skills add https://github.com/BAWES-Universe/universe-ai-creator-kit --skill universe-creator
```

Choose your agent when prompted. The installer supports agents including **Claude Code, Codex, and Hermes**. It requires Node.js **22.20.0 or newer**. [Setup options and supported-agent sources →](docs/agent-setup.md)

Then give your agent a first task:

> Use universe-creator. Help me create a small BAWES Universe map. Start with one scene we can test before building the whole world.

Prefer a Woka or an asset? Change the task to suit. The skill helps you choose a reference, make a small proof, and check the result before expanding it.

**Just browsing?** Start with the [five-minute guide](docs/start-here.md). The handbook needs no installation. The skill provides guidance; your agent still needs the appropriate tools, source access, and runtime.

## Explore the experiments

| Butterfly Town v1 | Lantern Courtyard depth proof |
| --- | --- |
| [![Butterfly Town v1: a lantern-lit town square with a fountain and three buildings](https://raw.githubusercontent.com/BAWES-Universe/universe-maps/d818e6c4c001e5fa7ba76e02663a1fb9ce9460fd/map-mocks/butterfly-town-v1/screenshot.png)](https://github.com/BAWES-Universe/universe-maps/tree/d818e6c4c001e5fa7ba76e02663a1fb9ce9460fd/map-mocks/butterfly-town-v1) | [![Lantern Courtyard depth proof: an avatar among tiled paving, seating, trees, and a pool](https://raw.githubusercontent.com/BAWES-Universe/universe-maps/d818e6c4c001e5fa7ba76e02663a1fb9ce9460fd/map-mocks/lantern-courtyard-02-depth/screenshot.png)](https://github.com/BAWES-Universe/universe-maps/tree/d818e6c4c001e5fa7ba76e02663a1fb9ce9460fd/map-mocks/lantern-courtyard-02-depth) |

Historical views from the [14-entry map archive](https://github.com/BAWES-Universe/universe-maps/tree/d818e6c4c001e5fa7ba76e02663a1fb9ce9460fd/map-mocks). These are learning examples with their own limitations. [See what worked, what failed, and what to try next →](docs/experiment-history.md)

## Make one good thing, then build on it

1. **Choose a reference.** Agree on the look, scale, and behavior you want.
2. **Build a small proof.** One doorway, one foreground object, or one avatar change is enough to test a method.
3. **Check it and keep the lesson.** Inspect it in the intended runtime, record the evidence, and improve the next attempt.

The same workflow applies to people and agents. Useful failures belong here too.

## The handbook

| Create | Learn and contribute |
| --- | --- |
| [Start here](docs/start-here.md) | [Experiment history](docs/experiment-history.md) |
| [Map creation](docs/maps.md) | [Validation guide](docs/validation.md) |
| [Woka creation](docs/wokas.md) | [Evidence status](docs/evidence-status.md) |
| [Agent setup](docs/agent-setup.md) | [Experiment template](templates/experiment.md) |
| [Shared creator skill](skills/universe-creator/SKILL.md) | [Contributing](CONTRIBUTING.md) |

## Where things stand

The starting archive preserves **10 Tiled candidates and four visual/art studies**. Original art quality is still being worked out, and archived experiments are not automatically publishable templates. Technical checks and visual acceptance are tracked separately.

Each workflow needs validation against its exact **Universe or WorkAdventure version/fork**. Large assets stay in their source repositories. Check [evidence status](docs/evidence-status.md) and [asset rights and privacy](CONTRIBUTING.md#assets-rights-and-privacy) before reuse; this starter does not select a repository-wide license.
