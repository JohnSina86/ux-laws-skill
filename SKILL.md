---
name: ux-laws
description: >-
  Evaluate, critique, and guide UI/UX designs, interaction patterns, and user flows
  using 20 core UX laws and cognitive psychology principles (including Hick's Law,
  Fitts's Law, Miller's Law, Peak-End Rule, and Doherty Threshold).
---

# UX & Interaction Design Laws Skill

This skill equips the AI agent with a rigorous framework for evaluating, critiquing, and refining digital product interfaces, design systems, and interaction workflows based on 20 fundamental laws of UX and human-computer interaction (HCI).

---

## The 20 Fundamental UX Laws

### 1. Hick's Law
- **Core Principle**: The time required to make a decision increases logarithmically with the number and complexity of choices.
- **Application**: Minimize navigation choices, break complex multi-step processes into bite-sized funnels, highlight a single primary call-to-action (CTA).

### 2. Fitts's Law
- **Core Principle**: The time to acquire a target is a function of the distance to the target and the width of the target.
- **Application**: Make interactive controls large enough to tap/click comfortably (min 44x44px or 48x48px on mobile). Place critical buttons within natural thumb or cursor zones.

### 3. Jakob's Law
- **Core Principle**: Users spend most of their time on other products. They expect your product to work similarly to what they already know.
- **Application**: Avoid reinventing standard UI paradigms (e.g., e-commerce shopping cart at top-right, search bar patterns, standard form layouts).

### 4. Law of Proximity
- **Core Principle**: Objects that are near each other are perceived as a unified group or sharing a relationship.
- **Application**: Place labels immediately adjacent to their input fields. Ensure spacing between distinct sections is noticeably larger than spacing between related items.

### 5. Miller's Law
- **Core Principle**: The average human working memory can only hold 7 ± 2 chunks of information simultaneously.
- **Application**: Chunk long strings of data (phone numbers, credit cards, verification codes). Structure complex dashboards with clear categories.

### 6. Doherty Threshold
- **Core Principle**: Productivity and flow soar when human and computer interact at a pace under 400ms where neither waits on the other.
- **Application**: Provide optimistic UI updates, immediate feedback states on button taps, and skeleton screens instead of blank spinners for async operations.

### 7. Von Restorff Effect (Isolation Effect)
- **Core Principle**: When multiple similar items are present, the one that differs from the rest is most likely to be remembered.
- **Application**: Make primary pricing tiers ("Most Popular"), critical alerts, or primary conversion buttons visually distinct through contrast, color, or elevation.

### 8. Minimize Target Distance
- **Core Principle**: Reducing the physical travel distance to the next intended action accelerates completion and lowers fatigue.
- **Application**: Use contextual menus, inline editing, and floating action buttons near the active work area instead of forcing users to traverse across the screen.

### 9. Serial Position Effect
- **Core Principle**: Users remember the first (primacy) and last (recency) items in a sequence best, and forget the middle.
- **Application**: Place the most critical navigation links at the start and end of navigation bars or lists. Put secondary actions in the middle.

### 10. Peak-End Rule
- **Core Principle**: Experiences are judged primarily by how users felt at their emotional peak (best or worst point) and at the very end.
- **Application**: Celebrate milestones and task completions (delightful success states), and design error recovery flows with extreme empathy.

### 11. Zeigarnik Effect
- **Core Principle**: Incomplete or interrupted tasks remain active in human memory much longer than finished ones.
- **Application**: Use progress bars, step indicators, and onboarding checklists to tap into the human drive for task closure.

### 12. Law of Prägnanz (Law of Simplicity)
- **Core Principle**: The human eye interprets ambiguous or complex shapes in the simplest, most orderly form possible.
- **Application**: Avoid cluttered or overlapping geometry. Use clean grids and familiar rectangular containers to minimize visual noise.

### 13. Law of Similarity
- **Core Principle**: Elements that share visual characteristics (color, shape, styling) are perceived as having the same role or function.
- **Application**: Keep styling uniform across all interactive buttons, links, and system states. Never style non-clickable text like a link.

### 14. Uniform Connectedness
- **Core Principle**: Visually connected elements (via borders, lines, or shared container backgrounds) are perceived as more strongly related than elements with no explicit link.
- **Application**: Group form sections or list items inside explicit cards, background panels, or connected step-flows.

### 15. Tesler's Law (Law of Conservation of Complexity)
- **Core Principle**: Every application contains an irreducible amount of complexity. It must either be absorbed by the design/engineering or dealt with by the user.
- **Application**: Strive to absorb complexity behind the scenes (smart defaults, auto-detection, sensible presets) rather than exposing dozens of manual configuration knobs to the user.

### 16. Postel's Law (Robustness Principle)
- **Core Principle**: Be liberal in what you accept, and conservative in what you send.
- **Application**: Allow flexible user input (accept dates in multiple formats, strip spaces and formatting from phone/card numbers) while rendering clean, predictable feedback.

### 17. Aesthetic-Usability Effect
- **Core Principle**: Users perceive aesthetically pleasing designs as more usable and are significantly more forgiving of minor usability hiccups.
- **Application**: Invest in consistent typography, refined spacing scales, and visual polish; aesthetics directly enhance perceived quality and trust.

### 18. Parkinson's Law
- **Core Principle**: Work expands to fill the time allotted for its completion.
- **Application**: Streamline task flows with autofill, quick defaults, and transparent completion estimates so users do not linger or abandon tasks.

### 19. Occam's Razor
- **Core Principle**: When faced with competing solutions that achieve the same result, the simplest one with the fewest assumptions is best.
- **Application**: Eliminate redundant fields, decorative widgets, and non-essential confirmation steps.

### 20. Pareto Principle (80/20 Rule)
- **Core Principle**: Approximately 80% of user activity and value stems from 20% of core features.
- **Application**: Dedicate prime screen real estate to the critical 20% of actions; tuck niche or advanced features into secondary menus.

---

## Agent Instructions: Review & Audit Workflow

When asked to critique an interface, analyze a wireframe, or review code:

1. **Identify the Core Objective**: Determine what the user is trying to accomplish on this screen or flow.
2. **Apply Relevant Heuristics**: Select the 3–5 laws most pertinent to the context (e.g., Fitts's & Target Distance for mobile navigation; Hick's & Miller's for search/onboarding).
3. **Structure Feedback with Concrete References**:
   - Cite the law by name.
   - Describe the exact violation or area for improvement.
   - Provide an actionable, specific solution (code snippet, layout modification, or copy adjustment).
