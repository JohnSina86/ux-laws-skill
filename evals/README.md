# Evals

Data files, a few inert fixtures and grader-only reference audits. Nothing here runs automatically.

- `evals.json` follows the Anthropic skill-creator schema: `skill_name` and `evals[]`, each with `id`, `prompt`, `expected_output`, `files` and `expectations[]`.
- `trigger-eval.json` is a list of `{query, should_trigger}`: ten positives and ten **near-miss negatives** (WCAG audit, style change, performance profiling, copywriting, research summary).
- `fixtures/` holds **inert** HTML (static markup, no script). `evals/expected/` holds the reference audits for graders only.

## Fixtures stay separate from the worked example
The worked audit in `examples/sample-audit.md` already contains its own answer, so **it is not an eval fixture**. Eval agents must not read `examples/` or `evals/expected/`. Eval 2 uses an unseen variant (`pricing-card.html`) whose delegated click handler is quoted as text in the prompt instead of shipping as code.

## Manual run: functional evals
1. Start a fresh session that has only this skill available, and tell it not to read `examples/` or `evals/expected/`.
2. Give it each `prompt` and attach the listed `files`.
3. Grade every entry in `expectations` as pass or fail, using `evals/expected/` as a reference. Record a reason for each failure.
4. Optional baseline: repeat without the skill and compare.

## Manual run: trigger evals
The queries alternate between positives and near-miss negatives, so each part of the split holds both labels. Use the first 12 queries as the tuning set and the last 8 as held-out. Look at held-out results only after you finish editing the description. A query is correct when whether the skill loaded equals `should_trigger`.

## Checking the hit-testing snippet
Serve `fixtures/` over HTTP, open each page in a browser at a phone-sized viewport, and run the snippet in `references/hit-testing.md`:
- `newsletter-card.html` with region `.promo` and target `.archive-link`: expect `interceptedControls` to list the input and the button.
- `pricing-card.html` with region `.plan` and target `.plan-link`: expect `delegated-unknown` for the details panel and `occluded: 0`. After attaching a click listener to `#plan-details` in DevTools, the result must not change (page JavaScript can't see it). After setting an inline `onclick` attribute on it, expect `delegated-possible`. Never fire a click.

## Automated run (not run in this repository's release process)
Anthropic's skill-creator ships `run_eval.py` and `run_loop.py`, which run trigger queries through the `claude` CLI and split the queries themselves. They need `claude -p`. The v1.2.0 release was prepared without that CLI, so the trigger set was reviewed by hand and **not** run through the automated tester.
