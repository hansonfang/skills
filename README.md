# Agent Skills

Reusable [Agent Skills](https://agentskills.io/) for Codex and other compatible agents.

## Install

Install a specific skill from this repository:

```bash
npx skills add hansonfang/skills --skill archiving-work
```

Add `-g` to install it globally:

```bash
npx skills add hansonfang/skills --skill archiving-work -g
```

Use `npx skills add hansonfang/skills --list` to inspect the available skills before installing.

## Skills

| Skill | Use when |
|---|---|
| [`archiving-work`](skills/archiving-work/SKILL.md) | Substantial discussion, research, planning, design, prototypes, or related work must be preserved for resuming after a long pause or in a future session. |

## Structure

Each skill lives under `skills/<skill-name>/` and contains a `SKILL.md` file.
