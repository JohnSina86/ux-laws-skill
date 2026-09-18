# Comprehensive Guide: 20 Laws of UX & Cognitive Psychology

This reference breaks down the 20 essential UX laws, their cognitive origins, and practical Do's and Don'ts for product designers and software engineers.

---

## Table of Contents
1. [Hick's Law](#1-hicks-law)
2. [Fitts's Law](#2-fittss-law)
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

* **Origin**: Formulated by psychologists William Edmund Hick and Ray Hyman (1952).
* **Formula**: $T = b \cdot \log_2(n + 1)$
* **Do**:
  - Break complex multi-step processes into sequential steps (wizards).
  - Use progressive disclosure to show advanced options only on demand.
  - Recommend a "Default" or "Popular" option to reduce decision paralysis.
* **Don't**:
  - Overwhelm users with 15 flat choices in a single dropdown or navigation menu.

---

### 2. Fitts's Law
> *The time to acquire a target is a function of the distance to the target and the width of the target.*

* **Origin**: Paul Fitts (1954).
* **Do**:
  - Make primary touch targets at least 44x44 points (iOS) or 48x48 dp (Android).
  - Pin important actions to screen edges or corners on desktop (infinite target width).
  - Place primary mobile actions in the bottom "thumb zone".
* **Don't**:
  - Create tiny text-only links clustered tightly together without adequate padding.

---

### 3. Jakob's Law
> *Users spend most of their time on other websites, so they prefer your site to work like the ones they already know.*

* **Origin**: Coined by Jakob Nielsen (2000).
* **Do**:
  - Follow recognized design conventions (search icon top-right/center, shopping cart top-right).
  - Ensure affordances clearly signal interactability.
* **Don't**:
  - Invent novel navigation schemes that require a tutorial just to browse.

---

### 4. Law of Proximity
> *Objects that are near each other tend to be grouped together.*

* **Origin**: Gestalt psychology (Max Wertheimer, 1923).
* **Do**:
  - Keep form field labels closer to their corresponding input than to adjacent fields.
  - Use consistent spacing scales (e.g., 8pt grid) where outer margin > group padding.
* **Don't**:
  - Place equal whitespace between unrelated sections and related sub-elements.

---

### 5. Miller's Law
> *The average person can only keep 7 ± 2 items in their working memory.*

* **Origin**: George A. Miller (1956).
* **Do**:
  - Chunk complex numbers (e.g., `(555) 019-2834` or `4532 •••• •••• 8891`).
  - Limit top-level navigation categories to 5–7 items.
* **Don't**:
  - Expect users to remember codes or data across different screens without displaying context.

---

### 6. Doherty Threshold
> *Productivity soars when computer and users interact at a pace (< 400ms) that ensures neither waits on the other.*

* **Origin**: Walter J. Doherty and Ahrin J. Thadhani (IBM, 1982).
* **Do**:
  - Provide immediate visual feedback (< 100ms) on interaction (pressed states, micro-animations).
  - Use skeleton screens to indicate structure while data loads asynchronously.
* **Don't**:
  - Freeze the UI or show an empty white screen while awaiting an API response.

---

### 7. Von Restorff Effect (Isolation Effect)
> *When multiple similar objects are present, the one that differs from the rest is most likely to be remembered.*

* **Origin**: Hedwig von Restorff (1933).
* **Do**:
  - Highlight the recommended pricing plan with distinct background color or badge.
  - Use a high-contrast accent color exclusively for the primary CTA.
* **Don't**:
  - Accentuate multiple competing elements simultaneously, creating visual noise.

---

### 8. Minimize Target Distance
> *Reducing the distance a cursor or finger must travel speeds up interaction and reduces motor fatigue.*

* **Do**:
  - Employ contextual right-click menus, floating action bars, or inline editing tools.
  - Place confirmation buttons near the trigger element on desktop modal dialogues.
* **Don't**:
  - Require users to move across 1920px of screen space between an input and its save button.

---

### 9. Serial Position Effect
> *Users have a propensity to best remember the first (primacy) and last (recency) items in a series.*

* **Origin**: Hermann Ebbinghaus (1885).
* **Do**:
  - Position the most vital navigation links (e.g., Home, Checkout/Profile) at the far left/right or top/bottom.
* **Don't**:
  - Bury the most important action or notification in the middle of a lengthy list.

---

### 10. Peak-End Rule
> *People judge an experience largely based on how they felt at its peak and at its end.*

* **Origin**: Daniel Kahneman and Barbara Fredrickson (1993).
* **Do**:
  - Design memorable, delightful confirmation states (e.g., celebration animation on goal completion).
  - Make cancellation, unsubscribe, or error states graceful, helpful, and respectful.
* **Don't**:
  - End an otherwise smooth onboarding flow with an abrupt, confusing error screen.

---

### 11. Zeigarnik Effect
> *People remember uncompleted or interrupted tasks better than completed tasks.*

* **Origin**: Bluma Zeigarnik (1927).
* **Do**:
  - Use visual progress bars (`"Profile 80% complete"`), checklists, and step counters.
* **Don't**:
  - Artificially trap users in non-skippable flows without showing how many steps remain.

---

### 12. Law of Prägnanz (Good Figure / Simplicity)
> *People perceive ambiguous or complex images as the simplest shape possible.*

* **Origin**: Gestalt psychology.
* **Do**:
  - Use symmetrical layouts, clear alignments, and established geometric silhouettes.
* **Don't**:
  - Use chaotic, irregular shapes or overlapping asymmetrical containers that demand active decoding.

---

### 13. Law of Similarity
> *Elements that share visual characteristics are perceived to belong together or share functionality.*

* **Do**:
  - Ensure all primary buttons across the product share identical color, typography, and border radius.
* **Don't**:
  - Style regular text with blue underlined styling if it is not an anchor link.

---

### 14. Law of Uniform Connectedness
> *Visually connected elements are perceived as more related than elements with no connection.*

* **Origin**: Irvin Rock and Stephen Palmer (1990).
* **Do**:
  - Enclose related form controls or metrics cards inside an explicit container card or border.
* **Don't**:
  - Rely solely on subtle whitespace when grouping disparate data tables.

---

### 15. Tesler's Law (Conservation of Complexity)
> *Every system has an irreducible amount of complexity that must be managed either by the system or the user.*

* **Origin**: Larry Tesler (mid-1980s).
* **Do**:
  - Auto-fill location from postal codes; automatically detect credit card brand from digits.
* **Don't**:
  - Offload database schema complexity directly onto user-facing configuration forms.

---

### 16. Postel's Law (Robustness Principle)
> *Be liberal in what you accept, and conservative in what you send.*

* **Origin**: Jon Postel (RFC 760 / TCP specification).
* **Do**:
  - Accept phone numbers formatted with dashes, parentheses, or spaces, and normalize automatically.
* **Don't**:
  - Reject an entire form because a user entered a space in their credit card or postal code.

---

### 17. Aesthetic-Usability Effect
> *Users perceive aesthetically pleasing designs as more usable and tolerant of minor design defects.*

* **Origin**: Masaaki Kurosu and Kaori Kashimura (1995).
* **Do**:
  - Pay obsessive attention to typographic hierarchy, micro-interactions, and visual harmony.
* **Don't**:
  - Use aesthetic polish as a substitute for fixing fundamental usability architecture flaws.

---

### 18. Parkinson's Law
> *Work expands to fill the time available for its completion.*

* **Origin**: Cyril Northcote Parkinson (1955).
* **Do**:
  - Minimize unnecessary form fields, offer smart defaults, and provide autofill capabilities.
* **Don't**:
  - Leave forms open-ended without clear structure or progression indicators.

---

### 19. Occam's Razor
> *Among competing hypotheses or designs, the simplest one with the fewest assumptions is best.*

* **Origin**: William of Ockham (14th century).
* **Do**:
  - Remove unnecessary chrome, excessive decorative elements, and redundant confirmation dialogs.
* **Don't**:
  - Add complex widgets or multi-layer animations where simple static text suffices.

---

### 20. Pareto Principle (80/20 Rule)
> *Roughly 80% of consequences or usage come from 20% of the causes or features.*

* **Origin**: Vilfredo Pareto (1896).
* **Do**:
  - Identify the top 20% of actions users take daily and make them accessible in 1 click.
* **Don't**:
  - Clutter the primary toolbar with niche features used once a year by 1% of users.
