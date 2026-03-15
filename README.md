<div align="center">

<img src="assets/logo.png" width="760" alt="Meta Skill Generator logo">
<h1>Meta Skill Generator</h1>

[![License: MIT](https://img.shields.io/badge/License-MIT-2de1c2.svg)](./LICENSE)
[![Release](https://img.shields.io/github/v/release/Betswish/meta-skill-generator?color=d9ff63)](https://github.com/Betswish/meta-skill-generator/releases)
[![Discussions](https://img.shields.io/github/discussions/Betswish/meta-skill-generator?color=6cb6ff)](https://github.com/Betswish/meta-skill-generator/discussions)

English | [中文](./README.zh.md)

</div>

This repo hosts a meta skill for generating or revising `SKILL.md` files from a plain-language user brief.

The goal is simple: turn a vague workflow request into a concise, production-ready skill without bloating the context window. The skill helps choose the right structure, write trigger-aware frontmatter, decide whether extra resources are needed, and keep the final skill lean.

`SKILL.md` is the canonical behavior spec. This README is the practical quick-start.

## What The Skill Does

- Drafts a new `SKILL.md` from a user requirement.
- Revises an existing skill to improve scope, triggers, or structure.
- Chooses the lightest viable pattern for the task.
- Suggests whether `scripts/`, `references/`, or `assets/` are actually needed.
- Optionally scaffolds `agents/openai.yaml` for UI-facing metadata.

## Install As A CLI Skill

This repo follows the Agent Skills layout with `SKILL.md` at the skill root.

Run these commands from this directory:

### Claude Code

```bash
mkdir -p ~/.claude/skills
ln -s "$(pwd)" ~/.claude/skills/meta-skill-generator
```

### Codex

```bash
mkdir -p ~/.codex/skills
ln -s "$(pwd)" ~/.codex/skills/meta-skill-generator
```

### Cursor

```bash
mkdir -p ~/.cursor/skills
ln -s "$(pwd)" ~/.cursor/skills/meta-skill-generator
```

### Other CLI Tools

Place this folder in that CLI's skills directory with the folder name `meta-skill-generator`.

After installation, restart the CLI or refresh its skill list, then invoke `meta-skill-generator` using that tool's syntax.

## Quick Start

1. Install the skill.
2. Invoke `meta-skill-generator`.
3. Paste a short brief describing the skill you want.

Minimal prompt template:

```text
Create a skill for <task or domain>.
It should trigger when users ask about <request types>.
The output should help produce <deliverable>.
Constraints: <language, tools, tone, frameworks, file formats>.
```

## Demo

Example user prompt:

```text
/meta-skill-generator Create a skill for reviewing React pull requests.
It should trigger on code review requests, focus on bugs and regressions,
and keep the skill concise. English only.
```

Expected output shape:

- A short hyphen-case skill name
- A trigger-aware `description`
- A compact `SKILL.md` body with intake, workflow, and quality checks
- Optional resource guidance only if the task truly needs it

## Repo Contents

- `SKILL.md` contains the skill behavior and authoring workflow.
- `agents/openai.yaml` contains optional UI metadata.
- `assets/social-preview.png` is a GitHub-ready social preview asset.
- `LICENSE` clarifies the reuse terms.
- `README.md` and `README.zh.md` provide quick-start documentation.

## Community

- Ask questions or share ideas in [GitHub Discussions](https://github.com/Betswish/meta-skill-generator/discussions).
- Track stable milestones in [Releases](https://github.com/Betswish/meta-skill-generator/releases).
- If you build something with this skill, open a Discussion and share the generated skill.

## Design Principles

- Keep skills lean and specific.
- Prefer clear triggers over broad descriptions.
- Use progressive disclosure instead of stuffing everything into `SKILL.md`.
- Add resources only when they materially improve reliability.
- Infer reasonable defaults when the user brief is incomplete.

## Good Fit

Use this skill when you want to:

- create a new Codex-compatible skill from scratch
- convert a plain-language process into a reusable `SKILL.md`
- tighten an existing skill that feels vague or bloated
- scaffold a minimal skill package without overengineering it

## Not The Best Fit

This skill is less useful when:

- the user only wants general brainstorming with no skill output
- the task is really a one-off prompt, not a reusable workflow
- the work requires a full framework or codebase template rather than a skill
