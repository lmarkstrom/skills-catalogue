# skills-catalogue

A personal catalogue of Antigravity agent rules, skills, and agents.

## Structure

```
rules/     <- always-on rules, deployed to ~/.gemini/config/GEMINI.md
skills/    <- on-demand skills, symlinked to ~/.gemini/config/skills/
agents/    <- agent definitions, symlinked to ~/.gemini/config/skills/
```

## Deployment

Rules are copied into `~/.gemini/config/GEMINI.md` (combine if adding more rules).
Skills and agents are symlinked into `~/.gemini/config/skills/<name>`.

## Rules

| Rule | Description |
|---|---|
| [output-formatting](rules/output-formatting.md) | Always-on formatting and tone rules for every response. |

## Skills

| Skill | Description |
|---|---|
| [coding](skills/coding/SKILL.md) | Code style, comments, context, and editing behaviour (Python-first). |
| [code-review](skills/code-review/SKILL.md) | How to review diffs and PRs — priority tiers, feedback style, output format. |

## Agents

| Agent | Description |
|---|---|
| [planning](agents/planning/SKILL.md) | Task breakdown, clarifying questions, plan format, and approval flow. |
