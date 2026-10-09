# Set up your creator agent

Install one shared skill, then give your agent a concrete task. The same handbook supports human teammates, so you can review the method and evidence together.

## Install the skill

Run this from the project folder where you want to use it:

```sh
npx skills add https://github.com/BAWES-Universe/universe-ai-creator-kit --skill universe-creator
```

Choose your agent when prompted. The `skills` CLI lists **Claude Code, Codex, and Hermes** among its supported agents. The CLI source reviewed for this setup was version **1.7.1**, which requires Node.js **22.20.0 or newer**.

Sources: [official CLI documentation](https://skills.sh/docs/cli), [supported agents](https://github.com/vercel-labs/skills#supported-agents), and [CLI package requirements](https://github.com/vercel-labs/skills/blob/958f4b7389ba698b0a6a26a1e505ae2af82364d2/package.json). The unpinned `npx` command can resolve a newer CLI release; check its requirements if they change.

Installation uses the project's scope by default. For agent-specific selection or user-wide installation, see the options below. Installing this skill does not install Tiled, a game runtime, image-generation tools, or private source repositories.

## Try your first task

> Use universe-creator. Help me create a small BAWES Universe map. Start with one scene we can test before building the whole world.

For a Woka, ask for a small avatar change instead. For WorkAdventure, name that target explicitly. The agent should establish the source, reference, and runtime before relying on version-specific behavior.

A useful first result includes a small source change or clear plan, visual evidence where available, the checks actually run, and the next decision. See [Start here](start-here.md) for the creation workflow.

## Confirm it is available

Ask your agent to identify the `universe-creator` skill and summarize its first steps. If it cannot see the skill, check the installer's output and the agent's own skill-loading instructions. An installation receipt alone does not prove the current agent session has loaded it.

The skill's [source file](../skills/universe-creator/SKILL.md) contains the portable workflow and links to the full handbook. External tools and runtime access remain separate requirements.

### Installation check recorded on 2026-10-09

A local-source test used Node.js 24.19.0, npm 11.9.0, and `skills` 1.7.1 in a disposable Git project. Discovery found one `universe-creator` skill. A project-scoped copy installation for Codex, Claude Code, and Hermes produced byte-identical skill files in their supported discovery locations.

This checked the local package and installer paths. It did not run those agents, validate their creative output, or test a game runtime. GitHub-source installation is a separate check from this local-source result.

## Installation options

Inspect the skills advertised by the repository without installing them:

```sh
npx skills add https://github.com/BAWES-Universe/universe-ai-creator-kit --list
```

Select a specific supported agent by adding one of these options to the install command:

| Agent | Option |
| --- | --- |
| Claude Code | `--agent claude-code` |
| Codex | `--agent codex` |
| Hermes | `--agent hermes-agent` |

Add `-g` only if you want user-wide installation rather than installation scoped to the current project. Consult the [official CLI documentation](https://skills.sh/docs/cli) for other options and current behavior.

**Hermes project-local setup:** the project must be a Git checkout and explicitly trusted by Hermes before its local skills load. Review the repository before granting trust, then follow the [Hermes project-local skills instructions](https://hermes-agent.nousresearch.com/docs/user-guide/features/skills#project-local-skills). The installer step alone does not complete that trust step.

CLI support is separate from end-to-end testing in a particular agent. A supported target name does not establish that its runtime, asset tools, or every workflow has been tested.

## Use the handbook without installation

For a chat-only assistant or an environment without skill installation, provide the relevant Markdown files through a supported file-sharing route, or supply accessible links. Ask it to read:

1. [README](../README.md) and [AGENTS.md](../AGENTS.md).
2. [Evidence status](evidence-status.md).
3. The relevant [map](maps.md) or [Woka](wokas.md) guide.
4. Related [experiment history](experiment-history.md) and [validation](validation.md).

Whether an agent automatically reads `AGENTS.md` depends on its environment. Ask explicitly when that behavior is unknown.

In ChatGPT web, the terminal command above is not a plugin installer. Use supported file upload or pasted context, such as a [ChatGPT Project](https://help.openai.com/en/articles/10169521-projects-in-chatgpt), to provide the skill text and relevant guides/source files.

A repository link does not grant access to private sources, configure credentials, provide tools, or authorize publication. Use the platform's normal access controls and never paste secrets into a prompt or this repository.

## Give the agent a useful brief

Once you know what you want to create, adapt this brief:

> Use universe-creator and read the relevant creator guide and experiment history.
>
> Goal: [one concrete outcome].
>
> Source: [repository, exact commit, and relevant paths].
>
> Reference and acceptance criteria: [visual reference and observable checks].
>
> Target environment: [authoring tool and exact runtime/product/fork, with known versions].
>
> Allowed changes: [files, working copy, and explicitly authorized actions].
>
> Deliver: a small reproducible result, changed files, visual evidence, test results, and remaining limitations. Preserve the original source. Label historical reports separately from tests you run now. Identify missing inputs, capabilities, or permissions before relying on them.

Replace bracketed fields with real information. Unresolved fields are questions to settle, not evidence that the environment or permissions exist.

## Keep shared knowledge shared

The handbook is canonical. The installable skill gives an agent a compact workflow and routes it to the relevant guides. General improvements belong in those guides so people and other agents benefit too.

Use the same [validation](validation.md) and [contribution](../CONTRIBUTING.md) standards for every creator. An agent's summary is useful context; source files, observed behavior, and visual review establish what actually worked.

Record failed attempts with the available evidence. If a model version, prompt, or environment was not preserved, say so rather than reconstructing it as fact.

[Back to the kit](../README.md) · [Start here](start-here.md)
