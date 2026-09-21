# Comprehensive Guide: 20 Laws of UX & Cognitive Psychology

This reference breaks down the 20 essential UX laws, their cognitive origins, practical Do's and Don'ts, and implementation guidelines for automated auditors and product designers.

---

## Table of Contents
1. [Hick's Law](#1-hicks-law)
2. [Fitts's Law (with Stretched-Link Caveat)](#2-fittss-law)
3. [Jakob's Law](#3-jakobs-law)
4. [Law of Proximity](#4-law-of-proximity)
5. [Miller's Law](#5-millers-law)
6. [Doherty Threshold](#6-doherty-threshold)
7. [Von Restorff Effect](#7-von-restorff-effect)
8. [Minimize Target Distance](#8-minimize-target-distance)
9. [Serial Position Effect](#9-serial-position-effect)
10. [Peak-End Rule](#10-peak-end-rule)
11. [Zeigarnik Effect](#11-zeigarnik-effect)
12. [Law of Prägnanz](#12-law-of-prägnanz)
13. [Law of Similarity](#13-law-of-similarity)
14. [Uniform Connectedness](#14-uniform-connectedness)
15. [Tesler's Law](#15-teslers-law)
16. [Postel's Law](#16-postels-law)
17. [Aesthetic-Usability Effect](#17-aesthetic-usability-effect)
18. [Parkinson's Law](#18-parkinsons-law)
19. [Occam's Razor](#19-occams-razor)
20. [Pareto Principle](#20-pareto-principle)

---

### 1. Hick's Law
> *Decision time increases logarithmically with the number and complexity of choices.*

* **Origin**: William Edmund Hick and Ray Hyman (1952).
* **Formula**: $T = b \cdot \log_2(n + 1)$
* **Primary Scope**: Core for Marketing (landing choices, pricing plans) & Forms (wizards, category selectors).
* **Do**:
  - Break multi-step processes into sequential steps (wizards).
  - Use progressive disclosure to show advanced options only when requested.
  - Highlight a single "Recommended" option to reduce decision paralysis.
* **Don't**:
  - Present flat menus of 15+ choices with identical visual weight.

---

### 2. Fitts's Law
> *The time to acquire a target is a function of the distance to the target and the width of the target.*

* **Origin**: Paul Fitts (1954).
* **Formula**: $MT = a + b \cdot \log_2 \left( \frac{2D}{W} \right)$
* **Primary Scope**: Core for SaaS dashboards & Forms; Contextual for Marketing CTAs.

#### ⚠️ Critical Auditor Heuristic: The Stretched-Link Pattern
When inspecting HTML/CSS or executing automated accessibility sweeps, **do not evaluate touch targets solely by the bounding box of `<a>` or `<button>` tags**.

Modern web patterns frequently stretch the interactive hit area of a small text link or icon across an entire card container:

```html
<!-- Example: Accessible Card with Stretched Link -->
<div class="card" style="position: relative; width: 320px; height: 220px;">
  <h3>Product Title</h3>
  <p>Description text...</p>
  <a href="/details" class="card-link">Learn More</a>
</div>
```
```css
/* Card Link stretches over the entire parent card */
.card-link::after {
  content: "";
  position: absolute;
  inset: 0; /* top: 0; right: 0; bottom: 0; left: 0; */
  z-index: 1;
}
```
* **Auditor Rule**: If an anchor has a pseudo-element (`::after` or `::before`) with `position: absolute` and `inset: 0`, trace up the DOM to the nearest ancestor with `position: relative` (or other positioned context). **The effective touch target $W$ is the dimensions of that container (e.g., $320 \times 220\text{px}$), NOT the inline text bounding box ($80 \times 16\text{px}$).**

* **Do**:
  - Ensure touch targets meet minimum accessible sizes ($\ge 44 \times 44\text{px}$ on mobile).
  - Place primary actions in comfortable reach zones (bottom of mobile viewports, screen edges on desktop).
* **Don't**:
  - Flag accessible container cards as Fitts's violations just because the text inside is small.

---

### 3. Jakob's Law
> *Users spend most of their time on other websites, so they prefer your site to work like the ones they already know.*

* **Origin**: Jakob Nielsen (2000).
* **Primary Scope**: Core across all site types.
* **Do**:
  - Use recognizable UI conventions (cart top-right, search in header, logo returns home).
  - Maintain established visual affordances (buttons look clickable, inputs look editable).
* **Don't**:
  - Reinvent common UI patterns purely for stylistic novelty (e.g., custom scrollbars that break wheel gestures).

---

### 4. Law of Proximity
> *Objects that are near each other tend to be grouped together.*

* **Origin**: Gestalt psychology (Max Wertheimer, 1923).
* **Primary Scope**: Core across all site types.
* **Do**:
  - Keep form field labels closer to their corresponding input than to neighboring inputs.
  - Employ a proportional spacing scale (e.g., 8pt grid) where outer section margins are $2\times$ to $3\times$ group margins.
* **Don't**:
  - Use equidistant whitespace between related sub-elements and unrelated section dividers.

---

### 5. Miller's Law
> *The average person can only keep 7 ± 2 items in their working memory.*

* **Origin**: George A. Miller (1956).
* **Primary Scope**: Core for SaaS dashboards and multi-field forms; Contextual for marketing.
* **Do**:
  - Chunk complex values (credit cards, phone numbers, serial keys) into 3–4 character segments.
  - Group long lists into distinct categories with max 5–7 items per section.
* **Don't**:
  - Require users to memorize values on screen A to type them on screen B.

---

### 6. Doherty Threshold
> *Productivity soars when computer and users interact at a pace (< 400ms) that ensures neither waits on the other.*

* **Origin**: Walter J. Doherty and Ahrin J. Thadhani (IBM, 1982).
* **Primary Scope**: Core for SaaS & interactive forms; Contextual for marketing pages.
* **Do**:
  - Provide immediate feedback (< 100ms) on clicks (active states, ripple animations).
  - Use skeleton screens to render layout immediately while async data loads.
* **Don't**:
  - Display uninformative full-screen spinners or freeze user input without feedback.

---

### 7. Von Restorff Effect (Isolation Effect)
> *When multiple similar objects are present, the one that differs from the rest is most likely to be remembered.*

* **Origin**: Hedwig von Restorff (1933).
* **Primary Scope**: Core for marketing & pricing grids; Contextual for dashboards.
* **Do**:
  - Give the primary recommended tier or conversion CTA distinctive elevation, border, or accent color.
* **Don't**:
  - Apply high-contrast accent colors to secondary or tertiary buttons simultaneously.

---

### 8. Minimize Target Distance
> *Reducing the distance a cursor or finger must travel speeds up interaction and reduces motor fatigue.*

* **Primary Scope**: Core for SaaS and complex forms; N/A for static content.
* **Do**:
  - Provide contextual actions (hover menus, right-click actions, inline edit buttons).
  - Place submission/confirmation controls close to the last entered field.
* **Don't**:
  - Force desktop users to move their cursor across 1920px between an input and its save button.

---

### 9. Serial Position Effect
> *Users best remember the first (primacy) and last (recency) items in a series.*

* **Origin**: Hermann Ebbinghaus (1885).
* **Primary Scope**: Core for marketing navbars and content indexes; N/A for simple forms.
* **Do**:
  - Place the most critical navigation anchors (e.g., Home, Features at start; Sign Up / Pricing at end).
* **Don't**:
  - Place the primary conversion link in the middle of a 7-item navigation menu.

---

### 10. Peak-End Rule
> *People judge an experience largely based on how they felt at its peak and at its end.*

* **Origin**: Daniel Kahneman and Barbara Fredrickson (1993).
* **Primary Scope**: Core for marketing funnels, checkout flows, and onboarding.
* **Do**:
  - Design memorable, positive confirmation states (e.g., celebration animations, clear receipt/next-steps).
  - Provide friendly, actionable recovery guidance on 404 or form failure states.
* **Don't**:
  - Leave users on an abrupt blank screen or vague message after completing a transaction.

---

### 11. Zeigarnik Effect
> *People remember uncompleted or interrupted tasks better than completed tasks.*

* **Origin**: Bluma Zeigarnik (1927).
* **Primary Scope**: Core for multi-step onboarding and checkout forms.
* **Auditor Note**: **N/A on marketing/landing pages** unless an interactive onboarding or multi-step quote tool is present.
* **Do**:
  - Show explicit progress bars (`"Profile 75% complete"`) and step indicators (`"Step 2 of 4"`).
* **Don't**:
  - Hide progress on complex, mandatory multi-page flows.

---

### 12. Law of Prägnanz (Simplicity)
> *The human eye interprets ambiguous or complex shapes in the simplest, most orderly form possible.*

* **Origin**: Gestalt psychology.
* **Primary Scope**: Core across all site types.
* **Do**:
  - Use clean grids, standard rectangular cards, and predictable alignments.
* **Don't**:
  - Layer irregular, overlapping asymmetrical shapes that force the user to mentally decode the UI.

---

### 13. Law of Similarity
> *Elements that share visual characteristics are perceived to have the same role or function.*

* **Primary Scope**: Core across all site types.
* **Do**:
  - Keep styling consistent across all interactive components (buttons, links, form fields).
* **Don't**:
  - Style regular text with blue underlined styling if it is not an anchor link.

---

### 14. Uniform Connectedness
> *Visually connected elements are perceived as more related than elements with no explicit link.*

* **Origin**: Irvin Rock and Stephen Palmer (1990).
* **Primary Scope**: Core across all site types.
* **Do**:
  - Group related form controls or metrics inside clear card containers, panels, or linked borders.
* **Don't**:
  - Rely exclusively on subtle whitespace when grouping disparate data tables or disparate actions.

---

### 15. Tesler's Law (Conservation of Complexity)
> *Every system has an irreducible amount of complexity that must be handled either by the system or the user.*

* **Origin**: Larry Tesler (mid-1980s).
* **Primary Scope**: Core for SaaS, web apps, and complex form flows.
* **Auditor Note**: **N/A on marketing pages** with no interactive application logic.
* **Do**:
  - Absorb complexity behind the scenes (auto-detect card issuer, auto-fill address from postal code).
* **Don't**:
  - Expose raw database configurations or complex internal settings directly to end users.

---

### 16. Postel's Law (Robustness Principle)
> *Be liberal in what you accept, and conservative in what you send.*

* **Origin**: Jon Postel (RFC 760 / TCP specification).
* **Primary Scope**: Core for forms and input fields.
* **Auditor Note**: **N/A on static content/marketing pages** without input controls.
* **Do**:
  - Accept phone numbers formatted with dashes, spaces, or parentheses and sanitize automatically.
  - Parse dates flexibly (`2026-09-21`, `09/21/2026`, `21 Sept 2026`).
* **Don't**:
  - Reject a form submission simply because a user included spaces in a credit card number.

---

### 17. Aesthetic-Usability Effect
> *Users perceive aesthetically pleasing designs as more usable and are more tolerant of minor defects.*

* **Origin**: Masaaki Kurosu and Kaori Kashimura (1995).
* **Primary Scope**: Core for marketing pages; Contextual for enterprise tooling.
* **Do**:
  - Invest in typographic hierarchy, balanced color palettes, and micro-interactions.
* **Don't**:
  - Use aesthetic polish to mask broken core functionality or broken navigation.

---

### 18. Parkinson's Law
> *Work expands to fill the time available for its completion.*

* **Origin**: Cyril Northcote Parkinson (1955).
* **Primary Scope**: Core for multi-step wizards, checkout funnels, and productivity apps.
* **Auditor Note**: **N/A on marketing and informational landing pages**.
* **Do**:
  - Provide autofill, browser credential autocomplete, and realistic completion time estimates (`"Takes ~2 minutes"`).
* **Don't**:
  - Drag out simple account creation over 6 disconnected screens.

---

### 19. Occam's Razor
> *Among competing designs that solve the problem equally well, the simplest one with the fewest assumptions is best.*

* **Origin**: William of Ockham (14th century).
* **Primary Scope**: Core across all site types.
* **Do**:
  - Eliminate redundant form fields, unnecessary confirmation dialogs, and decorative clutter.
* **Don't**:
  - Build complex multi-tier dropdowns when a simple segmented control suffices.

---

### 20. Pareto Principle (80/20 Rule)
> *Roughly 80% of user activity stems from 20% of features.*

* **Origin**: Vilfredo Pareto (1896).
* **Primary Scope**: Core for SaaS dashboards and primary navigation.
* **Do**:
  - Reserve prominent screen real estate for the top 20% most-used actions.
  - Move edge-case or administrative tools into secondary settings menus.
* **Don't**:
  - Give equal visual emphasis to a feature used daily and a feature used once a year.
