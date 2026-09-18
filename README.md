# UX Laws AI Skill (`ux-laws`)

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Skill: Antigravity](https://img.shields.io/badge/Skill-Antigravity%20%2F%20Agents-purple.svg)](SKILL.md)

An agentic AI skill and review framework based on **20 core UX laws and cognitive psychology principles**. 

Designed for AI coding assistants (Google Antigravity, Claude Code, Cursor, Copilot Workspace) to automatically critique, audit, and guide user interface implementations, design systems, and interaction flows.

---

## 20 Laws of UX at a Glance

| # | Principle | Key Takeaway |
|---|-----------|--------------|
| 1 | **Hick’s Law** | Simplify choices; decision time increases with options. |
| 2 | **Fitts’s Law** | Make touch targets large and place them close to natural reach zones. |
| 3 | **Jakob’s Law** | Follow familiar design patterns users know from other apps. |
| 4 | **Law of Proximity** | Group related elements close together with deliberate whitespace. |
| 5 | **Miller’s Law** | Chunk information into 7 ± 2 manageable pieces. |
| 6 | **Doherty Threshold** | Keep interactions responsive (< 400ms) to maintain user flow. |
| 7 | **Von Restorff Effect** | Make primary actions or recommended tiers stand out visually. |
| 8 | **Minimize Target Distance** | Bring actions near the user's focus (context menus, inline controls). |
| 9 | **Serial Position Effect** | Place critical items at the start and end of lists and navbars. |
| 10 | **Peak-End Rule** | Delight users at key milestones and ensure graceful exits. |
| 11 | **Zeigarnik Effect** | Use progress bars and checklists to encourage task completion. |
| 12 | **Law of Prägnanz** | Prefer clean, simple geometrical structures over visual chaos. |
| 13 | **Law of Similarity** | Elements with identical visual styling must share the same behavior. |
| 14 | **Uniform Connectedness** | Group related controls using cards, containers, or borders. |
| 15 | **Tesler’s Law** | Absorb complexity with smart backend defaults rather than burdening users. |
| 16 | **Postel’s Law** | Be liberal in what you accept (forgiving input) and conservative in output. |
| 17 | **Aesthetic-Usability Effect** | Polished, attractive visual designs increase perceived usability. |
| 18 | **Parkinson’s Law** | Provide autofill and sensible defaults to prevent task procrastination. |
| 19 | **Occam’s Razor** | Choose the simplest design solution with the fewest moving parts. |
| 20 | **Pareto Principle** | Optimize screen space for the 20% of features used 80% of the time. |

*For deep dive breakdowns with Do's and Don'ts, see [`references/principles-breakdown.md`](references/principles-breakdown.md).*

---

## Installation & Setup

### 1. In Google Antigravity

#### Workspace / Project Level
Copy or clone this repository into your project's `.agents/skills/` directory:
```bash
# In your project root:
mkdir -p .agents/skills
git clone https://github.com/JohnSina86/ux-laws-skill.git .agents/skills/ux-laws
```

#### Machine-Global Level
To make this skill available across all your projects:
```bash
# Windows PowerShell
git clone https://github.com/JohnSina86/ux-laws-skill.git "$HOME\.gemini\config\skills\ux-laws"

# macOS / Linux
git clone https://github.com/JohnSina86/ux-laws-skill.git ~/.gemini/config/skills/ux-laws
```

### 2. In Other Agentic AI Assistants (Claude Code, Cursor, Copilot)
You can include [`SKILL.md`](SKILL.md) in your project instructions, system prompts, or cursor rules (`.cursorrules`):
```markdown
Refer to the UX Laws Skill in .agents/skills/ux-laws/SKILL.md whenever designing or reviewing UI components.
```

---

## Example Prompts

Once installed, the AI agent will automatically pull this skill into context whenever you ask UX-related queries, such as:

* *"Review this checkout form wireframe against core UX laws."*
* *"Why is our conversion rate low on this pricing table? Critique the visual hierarchy."*
* *"Help me design a mobile navigation drawer that adheres to Fitts's Law and Miller's Law."*
* *"Audit this React form component for accessibility and Postel's Law compliance."*

---

## License

MIT License © 2026 [JohnSina86](https://github.com/JohnSina86). See [LICENSE](LICENSE) for details.
