# UX Laws AI Skill (`ux-laws`)

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Skill: Agents](https://img.shields.io/badge/Skill-Claude%20Code%20%2F%20Antigravity-purple.svg)](SKILL.md)

An agent skill and review framework built on **20 UX laws and cognitive-psychology principles**. It's designed for AI coding assistants (Claude Code, Google Antigravity, Cursor, Copilot), so their UX audits are **more consistent and evidence-backed**.

> **Scope:** usability heuristics only. A UX score from this skill is not an accessibility or WCAG conformance result, so pair it with an accessibility review.

## What makes it different

Generic AI UX critiques tend to fail in four ways. Here is how this skill handles each one:

1. **Uncalibrated grades.** Every Pass, Warning and Fail must cite the observable evidence listed in a per-law rubric. Option counts and similar numbers prompt a closer look but never decide a grade.
2. **Guessing.** When the evidence isn't available (timing on a screenshot, usage data for Pareto), the law is reported as **Not assessed** and the needed evidence is listed. It's excluded from the score, and an audit with no assessable laws reports *no score* instead of 0%.
3. **Misapplied laws.** An applicability matrix marks each law Core, Contextual (scored only when a named trigger is present) or N/A for four surface types. Declared visual styles are graded on structure, not aesthetic.
4. **False hit-area results.** Live hit-testing (`elementFromPoint`) is preferred. Static measurement accounts for stretched links, containing blocks, clipping, overlays and nested controls. Fitts's usability goal is kept separate from WCAG 2.2 2.5.8 conformance.

The score is the mean over assessed laws. A blocking rule caps the band whenever a task-critical path fails.

See [`SKILL.md`](SKILL.md) for the rubric, matrix and report template, [`references/principles-breakdown.md`](references/principles-breakdown.md) for origins and caveats, and [`examples/sample-audit.md`](examples/sample-audit.md) for a worked audit.

## The 20 laws

Hick · Fitts (target size) · Jakob · Proximity · Miller (memory load) · Doherty · Von Restorff · Minimize Target Distance · Serial Position · Peak-End · Zeigarnik · Prägnanz · Similarity · Uniform Connectedness · Tesler · Postel · Aesthetic-Usability · Parkinson (time expectations) · Occam's Razor · Pareto

## Installation

Install a tagged release, so you get the reviewed version.

### Claude Code
```bash
mkdir -p ~/.claude/skills && git clone --branch v1.1.0 https://github.com/JohnSina86/ux-laws-skill.git ~/.claude/skills/ux-laws
```
```powershell
New-Item -ItemType Directory -Force "$HOME\.claude\skills" | Out-Null; git clone --branch v1.1.0 https://github.com/JohnSina86/ux-laws-skill.git "$HOME\.claude\skills\ux-laws"
```
For project level, use `.claude/skills/ux-laws` under the project root. The folder name must be `ux-laws`. Claude Code loads the skill on demand from its description.

### Google Antigravity
```bash
mkdir -p .agents/skills && git clone --branch v1.1.0 https://github.com/JohnSina86/ux-laws-skill.git .agents/skills/ux-laws          # project
mkdir -p ~/.gemini/config/skills && git clone --branch v1.1.0 https://github.com/JohnSina86/ux-laws-skill.git ~/.gemini/config/skills/ux-laws   # global
```

### Cursor, Copilot and other tools without native skills
```markdown
When reviewing UI or UX, follow .agents/skills/ux-laws/SKILL.md (rubric, applicability matrix, report template).
```

## Companion skill

[ui-styles](https://github.com/JohnSina86/ui-styles-skill) provides 22 visual styles with verified tokens. When it's used, ux-laws grades the structure of the result, not the chosen aesthetic.

## Changelog

- **v1.1.0**
  - Evidence rubric and Not assessed status, with a corrected score formula and zero-denominator rule.
  - Blocking rule.
  - Contextual defined.
  - Fitts split into size (law 2) and distance (law 8), and separated from WCAG 2.5.8.
  - Live hit-testing and a complete stretched-link procedure.
  - Science corrections (Hick intercept, Miller recall vs recognition, Postel ambiguous dates, Zeigarnik and Parkinson reframed, Pareto evidence).
  - Declared-style rule.
  - Matrix and reference synced.
  - Claude Code install instructions.
- **v1.0.0**: Initial release.

## License

MIT License © 2026 [JohnSina86](https://github.com/JohnSina86). See [LICENSE](LICENSE).
