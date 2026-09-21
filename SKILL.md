---
name: ux-laws
description: >-
  Evaluate, critique, and audit UI/UX designs, web pages, and application flows
  using 20 core UX laws and cognitive psychology principles. Includes a standardized
  scoring rubric, N/A filtering rules, hit-area measurement heuristics (stretched-link
  detection), and a site-type applicability matrix.
---

# UX & Interaction Design Laws Skill

This skill equips the AI agent with a rigorous, reproducible framework for evaluating, critiquing, and scoring digital product interfaces, design systems, and code implementations against 20 fundamental laws of UX and human-computer interaction (HCI).

---

## 1. Audit Protocol & Standardized Scoring

To ensure comparability between runs, across different pages, and among different auditors, all reviews must adhere to this standardized scoring rubric and output structure.

### Scoring Scale per Law
Each applicable law is evaluated on a 3-tier scale:

| Rating | Points | Definition | Criteria |
| :--- | :---: | :--- | :--- |
| **Pass** | `1.0` | Compliant | The design follows the principle cleanly without notable friction or anti-patterns. |
| **Warning** | `0.5` | Minor Friction | Minor inconsistency or non-blocking defect (e.g., button is 38px instead of 44px, or secondary CTA has slight visual over-emphasis). |
| **Fail** | `0.0` | Violation | Clear breach of the principle causing cognitive overload, interaction failure, or disorientation. |
| **N/A** | `Excluded` | Not Applicable | The principle does not apply to this surface type or component (see Site-Type Filter). |

### The N/A Rule (Mandatory)
> [!IMPORTANT]
> **Never grade a law that does not apply to the surface.** 
> An agent must NEVER penalize a design or invent violations for principles that are non-applicable to the surface type (e.g., grading Postel's Law on a static blog, or Zeigarnik Effect on a single landing hero).
>
> **Score Formula:**
> $$\text{UX Health Score} = \left( \frac{\sum \text{Points on Applicable Laws}}{\text{Total Number of Applicable Laws (Excluding N/A)}} \right) \times 100\%$$
>
> - **90% – 100%**: Production-grade / Optimal UX
> - **75% – 89%**: Good (Minor polish or non-blocking friction detected)
> - **60% – 74%**: Needs Work (Multiple measurable law violations)
> - **< 60%**: Critical Redesign Required

---

## 2. Site-Type Applicability Matrix

Before evaluating, **classify the surface type**. Only score laws that are `Core` or `Contextual`. Mark all others as `N/A` unless specific interactive widgets justify their inclusion.

| Principle | Marketing & Landing | SaaS & Dashboards | Forms & Wizards | Content & Docs |
| :--- | :---: | :---: | :---: | :---: |
| **1. Hick's Law** | **Core** | Contextual | **Core** | Contextual |
| **2. Fitts's Law** | Contextual (CTAs) | **Core** | **Core** | Contextual (Nav) |
| **3. Jakob's Law** | **Core** | **Core** | **Core** | **Core** |
| **4. Law of Proximity** | **Core** | **Core** | **Core** | **Core** |
| **5. Miller's Law** | Contextual | **Core** | **Core** | Contextual |
| **6. Doherty Threshold** | Contextual | **Core** | **Core** | Contextual |
| **7. Von Restorff Effect** | **Core** | Contextual | Contextual | Contextual |
| **8. Minimize Target Distance** | Contextual | **Core** | **Core** | N/A |
| **9. Serial Position Effect** | **Core** | Contextual | N/A | **Core** |
| **10. Peak-End Rule** | **Core** | Contextual | **Core** | N/A |
| **11. Zeigarnik Effect** | N/A* | Contextual | **Core** | N/A |
| **12. Law of Prägnanz** | **Core** | **Core** | **Core** | **Core** |
| **13. Law of Similarity** | **Core** | **Core** | **Core** | **Core** |
| **14. Uniform Connectedness** | **Core** | **Core** | **Core** | **Core** |
| **15. Tesler's Law** | N/A* | **Core** | **Core** | N/A |
| **16. Postel's Law** | N/A* | **Core** | **Core** | N/A |
| **17. Aesthetic-Usability Effect** | **Core** | Contextual | Contextual | Contextual |
| **18. Parkinson's Law** | N/A* | Contextual | **Core** | N/A |
| **19. Occam's Razor** | **Core** | **Core** | **Core** | **Core** |
| **20. Pareto Principle** | **Core** | **Core** | Contextual | Contextual |

*\*Note on Marketing N/A*: If a marketing page contains an interactive pricing calculator, lead capture form, or onboarding teaser, evaluate Postel, Tesler, Parkinson, or Zeigarnik **strictly for that specific sub-component**, not the page as a whole.

---

## 3. Hit-Area Measurement & The Stretched-Link Caveat

When inspecting code or measuring touch/click targets for **Fitts's Law** and **Minimize Target Distance**, automated tools and AI agents frequently generate false-positive violations by measuring only the inner anchor's direct bounding box.

### The Stretched-Link Rule
> [!CAUTION]
> **Do not measure `<a>` or `<button>` inline bounding boxes in isolation.**
> Modern accessible web patterns (e.g., Bootstrap `.stretched-link`, Tailwind `after:absolute after:inset-0`, or CSS pseudo-elements) make an entire card or container clickable while maintaining semantic HTML.

#### Verification Procedure:
1. **Inspect for Pseudo-Elements**: Check if the anchor has a `::before` or `::after` pseudo-element with:
   - `position: absolute`
   - `inset: 0` (or `top: 0; left: 0; right: 0; bottom: 0;` / `width: 100%; height: 100%;`)
2. **Locate the Positioned Ancestor**: Follow the DOM tree up to the nearest ancestor with `position: relative`, `position: absolute`, or `position: fixed`.
3. **Measure the True Click Surface**: The effective touch target is the bounding box of that **positioned ancestor**, NOT the inline text or SVG icon.
4. **Inspect Container Handlers**: Check if the parent card or row has an active click handler (`onClick`, `@click`, `cursor: pointer`) or card-level event delegation.

---

## 4. The 20 Fundamental UX Laws Reference

1. **Hick's Law**: Decision time increases logarithmically with options ($T = b \cdot \log_2(n+1)$). Keep primary choices limited; use progressive disclosure.
2. **Fitts's Law**: Target acquisition time depends on target size and distance. Ensure effective hit areas $\ge 44 \times 44\text{px}$ (check for stretched links!). Place primary actions within natural reach zones.
3. **Jakob's Law**: Users expect your product to behave like the products they already use. Adhere to common conventions and standard affordances.
4. **Law of Proximity**: Related items belong together visually. Space between distinct groups must be visibly greater than space between grouped elements.
5. **Miller's Law**: Working memory capacity is $7 \pm 2$ chunks. Chunk complex strings and limit top-level navigation categories to 5–7 items.
6. **Doherty Threshold**: Keep response feedback under 400ms. Use optimistic UI, skeleton loaders, and instant pressed-states to sustain user flow.
7. **Von Restorff Effect**: The element that differs from its surroundings is best remembered. Ensure high visual contrast for primary CTAs or recommended choices.
8. **Minimize Target Distance**: Reduce cursor/thumb travel distance. Employ contextual menus, floating actions, or inline controls near the active task.
9. **Serial Position Effect**: Users best retain the first (primacy) and last (recency) items in a sequence. Place high-value navigation at the outer edges.
10. **Peak-End Rule**: Experiences are judged by their emotional peak and final moments. Polish milestone completion states and design empathetic error flows.
11. **Zeigarnik Effect**: Incomplete tasks stick in memory. Use visual progress bars, checklist indicators, and step completion meters.
12. **Law of Prägnanz**: The human eye organizes visual complexity into the simplest geometric forms. Keep container shapes clean, aligned, and predictable.
13. **Law of Similarity**: Elements sharing visual attributes (color, typography, shape) are assumed to have the same function. Maintain consistent interaction styling.
14. **Uniform Connectedness**: Connected elements (via borders, lines, or shared container cards) are perceived as more strongly related than elements linked only by proximity.
15. **Tesler's Law (Conservation of Complexity)**: Systems possess an inherent amount of complexity. Absorb it through smart backend defaults rather than offloading it to the user.
16. **Postel's Law (Robustness Principle)**: Be liberal in what you accept, conservative in what you send. Accept diverse user input formats (dashes, spaces) and normalize behind the scenes.
17. **Aesthetic-Usability Effect**: Attractive designs are perceived as more usable and tolerate minor defects. Visual polish builds fundamental trust.
18. **Parkinson's Law**: Tasks expand to fill available time. Provide autofill, sensible defaults, and clear completion estimates to avoid friction.
19. **Occam's Razor**: Between two designs that solve the problem equally well, the one with fewer elements and assumptions is superior.
20. **Pareto Principle (80/20 Rule)**: 80% of user activity centers around 20% of features. Allocate prime screen real estate exclusively to high-frequency actions.

---

## 5. Standard Output Template for Audits

When generating a UX review, use this exact report format:

```markdown
# UX Law Audit: [Page / Component Name]

- **Surface Type**: [Marketing & Landing | SaaS & Dashboard | Form & Wizard | Content & Docs]
- **Overall UX Health Score**: **XX%** ([Pass Count] Pass, [Warning Count] Warning, [Fail Count] Fail, [N/A Count] N/A)

---

### Score Breakdown

| Law | Status | Points | Observation / Finding |
| :--- | :---: | :---: | :--- |
| **1. Hick's Law** | Pass | 1.0 | Clear 3-tier pricing table with recommended tier highlighted. |
| **2. Fitts's Law** | Pass | 1.0 | Card uses `.stretched-link` (`::after { inset: 0 }`); effective hit area is 320x240px. |
| ... | ... | ... | ... |
| **16. Postel's Law** | N/A | - | No user input fields on this static showcase section. |

---

### Key Violations & Recommended Fixes

#### 1. [Law Name] – [Severity: Warning | Fail]
- **Observed Violation**: [Specific description of the UX issue]
- **Evidence / Location**: [DOM selector, screenshot reference, or CSS file]
- **Actionable Remediation**: [Code snippet, layout modification, or copy fix]
```
