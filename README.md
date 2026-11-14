# Minecraft dev skills

Agent skills that teach coding agents (Claude Code, Codex, Copilot, Cursor and any agent that reads `SKILL.md`) the
parts of Minecraft development they tend to get wrong.

## Skills

- **[minecraft-skins](skills/minecraft-skins/SKILL.md)**: putting a skin on a player's account through Mojang's API
  (a file upload only: JSON with a URL has been refused with 403 since October 2026), telling slim from classic arms
  by pixels, the 64x64 and legacy 64x32 layouts, UV on player models, and skin catalogues that have an API.

## Why

We gave Claude Code (Claude Opus 5.5) and Codex (GPT-6.1) the same task: add a skin browser with a "Wear" button to a
small Electron launcher. Each agent ran once with the skill and once without, in a clean folder.

- Without the skill, both agents sent the skin to Mojang as JSON with a URL, the request Mojang now refuses. Their
  tests passed only because they mocked `fetch`.
- With the skill, both found it on their own, uploaded the PNG as a file as Mojang requires, and credited the skin's
  author.

One run per case: a probe, not a benchmark. On a second task (slim or classic arms from a PNG) both agents did as
well without the skill as with it, so that part of the skill is kept short.

## Install

Claude Code:

```shell
/plugin marketplace add MopicMP/minecraft-dev-skills
/plugin install minecraft-skins@mosaicary
```

Codex:

```shell
codex plugin marketplace add MopicMP/minecraft-dev-skills
codex plugin add minecraft-skins@mosaicary
```

Any agent that supports skills: copy `skills/minecraft-skins` into its skills folder, for example
`.claude/skills/` or `.agents/skills/` in your project.

## Disclosure

This repository is kept by the people behind [mosaicary.com](https://mosaicary.com). The skill lists Mosaicary's open
API among the skin catalogues, next to MineSkin. Corrections and other catalogues are welcome as issues or pull
requests.

## License

MIT
