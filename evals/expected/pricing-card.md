# Reference audit: pricing-card.html (grader only)

Not linked from `SKILL.md`. Eval agents must not read it. Measured at 400x800 with touch emulation. The script quoted in the eval prompt (a `click` listener on `#plan-details`) was attached temporarily in the browser and never fired.

## Measured facts
- Card 362x283. `#plan-details` is 320x52 (plain div, no `cursor: pointer`, no role). "Choose Pro" is 106x64. "Compare plans" is 72x14 at 12px, 4px to the right of the button.
- No stretched overlay: `::after` on `.plan-link` is not generated. The snippet reports the button as 4% of the sampled card region, with no intercepted controls.
- With only the `addEventListener` listener present, the snippet reports the details panel as `delegated-unknown` (page JavaScript can't see it). With an inline `onclick` attribute added temporarily, it reports `delegated-possible`. Zero clicks fired in both cases.

## Reference grades (touch-first marketing surface)
| Law | Status | Why |
| :--- | :---: | :--- |
| 1 Hick | Pass | One primary and one secondary action. |
| 2 Fitts (size) | Warning | "Compare plans" 72x14 is far below the 44 goal **and sits 4px from the primary button** (mis-tap risk), so it is graded even though it is a secondary link. The primary button (106x64) meets the goal. |
| 3 Jakob | Warning | A plain div carries a click handler (per the prompt) but has no pointer cursor, role or focusability, so there is no affordance for the action. Unconfirmed from page JavaScript. |
| 4 Proximity | Pass | Price, details and actions are grouped in one card. |
| 5 Miller | N/A | No comparison table. |
| 6 Doherty | Not assessed | `openCheckout` timing is unknown. |
| 7 Von Restorff | Pass | The blue filled button is the only strong accent. |
| 8 Minimize distance | N/A | No interactive widget beyond the CTA. |
| 9 Serial position | N/A | No navigation or ordered list. |
| 10 Peak-End | Not assessed | A conversion flow exists (checkout), but its result isn't in the evidence. |
| 11 Zeigarnik | N/A | Single step. |
| 12 Prägnanz | Pass | One card, simple stack. |
| 13 Similarity | Pass | The button and the link look like what they are. |
| 14 Connectedness | Pass | The border groups the content. |
| 15 Tesler | N/A | No application logic on this card. |
| 16 Postel | N/A | No input fields. |
| 17 Aesthetic-Usability | Pass | Consistent single card (judged from the render). |
| 18 Parkinson | N/A | Single step. |
| 19 Occam | Pass | No redundant elements. |
| 20 Pareto | Not assessed | Needs usage data. |

Counts: 8 Pass, 2 Warning, 0 Fail, 7 N/A, 3 Not assessed. Score (8 + 1.0) / 10 = **90%**, band Strong (no blocking Fail). Reasonable variation: Aesthetic-Usability and Von Restorff are render-dependent.

## Conformance notes (not scored)
- "Compare plans" (72x14, under 24px high) is undersized, but the **spacing test passes**: a 24px circle centred on its bounding box (centre about 36px from the button's edge) reaches neither the "Choose Pro" target nor another undersized target. So a 2.5.8 failure is **not established**. Note it as undersized and recommend padding, and keep it out of the score.
- The clickable div needs a semantic control (button or link) and keyboard access.
