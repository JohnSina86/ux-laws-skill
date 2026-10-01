# Worked example: newsletter sign-up card

This example shows the rubric, the Contextual and Not assessed handling, the stretched-link check and the score arithmetic on a small fixture.

## Fixture (evidence source: source code only)

```html
<section class="promo" style="position: relative; width: 340px; padding: 24px; border: 1px solid #ccc; border-radius: 12px">
  <h2>Weekly design notes</h2>
  <p>One email every Friday. Unsubscribe any time.</p>
  <form action="/subscribe">
    <label for="email">Email</label>
    <input id="email" type="email" required>
    <button type="submit" style="height: 36px">Subscribe</button>
  </form>
  <a href="/archive" class="archive-link">Learn more</a>
</section>
<style>.archive-link::after { content: ""; position: absolute; inset: 0; }</style>
```

Surface type: **Marketing & Landing**. Only source code is available, so there is no live page, no timing and no analytics.

## Audit

# UX Law Audit: Newsletter sign-up card

- **Surface type**: Marketing & Landing
- **Evidence sources**: source code
- **UX Score**: **77%** (8 Pass, 1 Warning, 2 Fail, 6 N/A, 3 Not assessed). The calculation is (8 × 1.0 + 1 × 0.5 + 2 × 0.0) / (8 + 1 + 2) = 8.5 / 11.
- **Band**: Needs Work (capped by blocking rule: yes, because sign-up is the task-critical path and it fails)
- **Scope note**: Usability heuristics only; not a WCAG/accessibility conformance result.

### Score breakdown
| Law | Status | Points | Observation / evidence |
| :--- | :---: | :---: | :--- |
| 1. Hick's Law | Pass | 1.0 | One action (Subscribe) and one secondary link. |
| 2. Fitts's Law (size) | Warning | 0.5 | Contextual trigger: CTA present. The Subscribe button is 36px high, below the 44 touch goal (static estimate). |
| 3. Jakob's Law | Pass | 1.0 | A standard label, input and button pattern. |
| 4. Law of Proximity | Pass | 1.0 | The label sits directly above its input. |
| 5. Miller's Law | N/A | – | Contextual trigger absent: no comparison table. |
| 6. Doherty Threshold | N/A | – | Contextual trigger absent: the form posts to a new page and there's no interactive widget. |
| 7. Von Restorff Effect | Pass | 1.0 | The button is the only filled control. |
| 8. Minimize Target Distance | N/A | – | Contextual trigger absent: no interactive widget beyond a single field. |
| 9. Serial Position Effect | Pass | 1.0 | The primary action comes last in the reading order. |
| 10. Peak-End Rule | Not assessed | – | The trigger (conversion confirmation) exists, but its page isn't in the evidence. Needs the `/subscribe` response. |
| 11. Zeigarnik Effect | N/A | – | Contextual trigger absent: single step. |
| 12. Law of Prägnanz | Pass | 1.0 | One card with a simple vertical stack. |
| 13. Law of Similarity | **Fail** | 0.0 | The stretched `.archive-link::after` covers the whole `position: relative` section, **including the input and the button**, which aren't raised above the overlay. Clicking Subscribe opens `/archive`. |
| 14. Uniform Connectedness | Pass | 1.0 | A bordered card groups the offer and the form. |
| 15. Tesler's Law | N/A | – | Contextual trigger absent: no application logic. |
| 16. Postel's Law | Fail | 0.0 | Contextual trigger: input field. `type="email"` rejects addresses with surrounding spaces, and there's no trimming or hint. |
| 17. Aesthetic-Usability | Not assessed | – | Rendered visual quality can't be judged from source. Needs a screenshot. |
| 18. Parkinson's Law | N/A | – | Contextual trigger absent: single step. |
| 19. Occam's Razor | Pass | 1.0 | Only one field is requested. |
| 20. Pareto Principle | Not assessed | – | Core for Marketing, but how Subscribe and the archive link are prioritised needs usage data. N/A would be wrong here, because the law applies. |

### Key findings
#### 1. Law of Similarity – Fail
- **Observed**: the archive link's stretched overlay captures clicks on the form controls.
- **Evidence / location**: `.archive-link::after { position: absolute; inset: 0 }`, with the containing block `section.promo` (`position: relative`). The input and button have no `position` or `z-index`.
- **Remediation**: remove the stretched link (the card isn't a single destination), or raise the form: `.promo form { position: relative; z-index: 2; }`. Also rename the link to "Read past issues" (WCAG 2.4.4).

#### 2. Postel's Law – Fail
- **Observed**: pasted addresses with leading or trailing spaces are rejected.
- **Remediation**: trim the value before validating (`input.value = input.value.trim()` on `change`), and keep the server-side check.

#### 3. Fitts's Law – Warning
- **Remediation**: `min-height: 44px` on the button.

### Not assessed — evidence needed
- Peak-End: the confirmation page returned by `/subscribe`.
- Aesthetic-Usability: a rendered screenshot.
- Pareto: click data for Subscribe vs the archive link.

### Conformance notes (not scored)
- Link text "Learn more" doesn't describe its destination (WCAG 2.4.4).
- The 36px button is above the 24px minimum in 2.5.8, so there's no 2.5.8 issue.
