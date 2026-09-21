# UX Laws AI Skill (`ux-laws`)

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Skill: Antigravity](https://img.shields.io/badge/Skill-Antigravity%20%2F%20Agents-purple.svg)](SKILL.md)

An agentic AI skill and review framework based on **20 core UX laws and cognitive psychology principles**. 

Engineered specifically for AI coding assistants (Google Antigravity, Claude Code, Cursor, Copilot Workspace) to perform **reproducible, false-positive-free UX audits** and guide interface implementations.

---

## What Makes This Skill Different

Generic AI UX critiques suffer from three common failure modes:
1. **Uncalibrated scoring**: Without a fixed scoring rubric and N/A rules, ratings vary widely between runs and between auditors.
2. **False-positive target measurements**: Measuring naive `<a>` bounding boxes flags accessible stretched-link card patterns (`::after { inset: 0 }`) as Fitts's Law violations.
3. **Over-application on marketing sites**: Flatly grading form- and app-centric laws (Postel, Tesler, Parkinson, Zeigarnik) on static landing pages produces nonsensical penalties.

This skill solves all three with built-in auditor guardrails:

* 🎯 **Reproducible Scoring Scale & N/A Rule**: Standardized 3-tier scoring (`Pass: 1.0`, `Warning: 0.5`, `Fail: 0.0`) with `N/A` strictly excluded from the score denominator.
* 🔍 **Stretched-Link & Hit-Area Heuristic**: Explicit instructions to inspect CSS pseudo-elements (`::after { inset: 0 }`), container click delegation, and positioned ancestors before measuring Fitts's Law touch targets.
* 🧭 **Site-Type Applicability Matrix**: Filters the 20 laws by surface type (*Marketing & Landing*, *SaaS & Dashboard*, *Forms & Wizards*, *Content & Docs*) so agents only evaluate relevant principles.

---

## 20 Laws of UX at a Glance

| # | Principle | Key Takeaway | Typical Scope |
|---|-----------|--------------|---------------|
| 1 | **Hick’s Law** | Simplify choices; decision time increases logarithmically with options. | Marketing, Forms |
| 2 | **Fitts’s Law** | Make touch targets large ($\ge 44\text{px}$) and close. *Account for stretched links!* | Apps, Forms, CTAs |
| 3 | **Jakob’s Law** | Follow familiar design patterns users know from other apps. | Universal |
| 4 | **Law of Proximity** | Group related elements close together with deliberate whitespace. | Universal |
| 5 | **Miller’s Law** | Chunk information into 7 ± 2 manageable pieces. | Dashboards, Forms |
| 6 | **Doherty Threshold** | Keep interactions responsive (< 400ms) to maintain user flow. | SaaS, Interactive |
| 7 | **Von Restorff Effect** | Make primary actions or recommended tiers stand out visually. | Marketing, Pricing |
| 8 | **Minimize Target Distance** | Bring actions near the user's focus (context menus, inline controls). | SaaS, Complex Forms |
| 9 | **Serial Position Effect** | Place critical items at the start and end of lists and navbars. | Navbars, Lists |
| 10 | **Peak-End Rule** | Delight users at key milestones and ensure graceful exits/error handling. | Funnels, Onboarding |
| 11 | **Zeigarnik Effect** | Use progress bars and checklists to encourage task completion. | Multi-step Wizards |
| 12 | **Law of Prägnanz** | Prefer clean, simple geometrical structures over visual chaos. | Universal |
| 13 | **Law of Similarity** | Elements with identical visual styling must share the same behavior. | Universal |
| 14 | **Uniform Connectedness** | Group related controls using cards, containers, or borders. | Universal |
| 15 | **Tesler’s Law** | Absorb complexity with smart backend defaults rather than burdening users. | SaaS, Complex Forms |
| 16 | **Postel’s Law** | Be liberal in what you accept (forgiving input) and conservative in output. | Forms, Inputs |
| 17 | **Aesthetic-Usability Effect** | Polished, attractive visual designs increase perceived usability. | Marketing, Branding |
| 18 | **Parkinson’s Law** | Provide autofill and sensible defaults to prevent task procrastination. | Forms, Checkouts |
| 19 | **Occam’s Razor** | Choose the simplest design solution with the fewest moving parts. | Universal |
| 20 | **Pareto Principle** | Optimize screen space for the 20% of features used 80% of the time. | Dashboards, Toolbars |

*For in-depth breakdowns, formulas, and Do's/Don'ts, see [`references/principles-breakdown.md`](references/principles-breakdown.md).*

---

## Site-Type Applicability Matrix

| Principle | Marketing & Landing | SaaS & Dashboards | Forms & Wizards | Content & Docs |
| :--- | :---: | :---: | :---: | :---: |
| **Hick's Law** | **Core** | Contextual | **Core** | Contextual |
| **Fitts's Law** | Contextual (CTAs) | **Core** | **Core** | Contextual (Nav) |
| **Jakob's Law** | **Core** | **Core** | **Core** | **Core** |
| **Law of Proximity** | **Core** | **Core** | **Core** | **Core** |
| **Miller's Law** | Contextual | **Core** | **Core** | Contextual |
| **Doherty Threshold** | Contextual | **Core** | **Core** | Contextual |
| **Von Restorff Effect** | **Core** | Contextual | Contextual | Contextual |
| **Minimize Target Distance** | Contextual | **Core** | **Core** | N/A |
| **Serial Position Effect** | **Core** | Contextual | N/A | **Core** |
| **Peak-End Rule** | **Core** | Contextual | **Core** | N/A |
| **Zeigarnik Effect** | N/A* | Contextual | **Core** | N/A |
| **Law of Prägnanz** | **Core** | **Core** | **Core** | **Core** |
| **Law of Similarity** | **Core** | **Core** | **Core** | **Core** |
| **Uniform Connectedness** | **Core** | **Core** | **Core** | **Core** |
| **Tesler's Law** | N/A* | **Core** | **Core** | N/A |
| **Postel's Law** | N/A* | **Core** | **Core** | N/A |
| **Aesthetic-Usability Effect** | **Core** | Contextual | Contextual | Contextual |
| **Parkinson's Law** | N/A* | Contextual | **Core** | N/A |
| **Occam's Razor** | **Core** | **Core** | **Core** | **Core** |
| **Pareto Principle** | **Core** | **Core** | Contextual | Contextual |

*\*Evaluated on marketing pages only if an interactive widget (e.g., pricing calculator, multi-step lead form) is explicitly present.*

---

## Installation & Setup

### 1. In Google Antigravity

#### Workspace / Project Level
Clone into your project's `.agents/skills/` directory:
```bash
# In your project root:
mkdir -p .agents/skills
git clone https://github.com/JohnSina86/ux-laws-skill.git .agents/skills/ux-laws
```

#### Global Level (Machine-Wide)
Make this skill available across all local projects:
```bash
# Windows PowerShell
git clone https://github.com/JohnSina86/ux-laws-skill.git "$HOME\.gemini\config\skills\ux-laws"

# macOS / Linux
git clone https://github.com/JohnSina86/ux-laws-skill.git ~/.gemini/config/skills/ux-laws
```

### 2. In Other Agentic AI Assistants (Claude Code, Cursor, Copilot)
Reference [`SKILL.md`](SKILL.md) in your project instructions, system prompts, or `.cursorrules`:
```markdown
Refer to the UX Laws Skill in .agents/skills/ux-laws/SKILL.md whenever designing or reviewing UI components.
```

---

## License

MIT License © 2026 [JohnSina86](https://github.com/JohnSina86). See [LICENSE](LICENSE) for details.
