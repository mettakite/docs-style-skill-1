# Style rules

Each rule has an ID so it can be cited in a compliance report, enforced in review, and eventually promoted to a lint check in CI. A rule that can't be checked isn't a rule; it's a mood.

## Terminology (T)

- **T1 — One name per concept.** Every product concept has exactly one name, and it matches the API's name for it. If the API says `Payment Instrument`, the docs never say "payment method," "card object," or "instrument" for the same thing.
- **T2 — Define on first use.** Every domain term is defined the first time it appears on a page, even if it was defined on another page. Pages are read out of order, by humans arriving from search and by AI agents retrieving one chunk.
- **T3 — Match casing and spelling to the schema.** Object, field, state, and event names are reproduced exactly as the API returns them: `SUCCEEDED`, not "Succeeded" or "succeeded," when the API returns `SUCCEEDED`.

## Formatting (F)

- **F1 — Monospace for machine-facing strings.** Field names, object names, endpoint paths, state values, event names, commands, and literal values are always in code font. Prose never contains a bare field name.
- **F2 — Units and formats stated where the value appears.** Amounts, timestamps, and identifiers state their unit or format at point of use: "amount in minor units (cents)," not a footnote three sections away.
- **F3 — Short sentences, active voice, one idea per sentence.** If a sentence needs a second comma to survive, it's usually two sentences.
- **F4 — No undefined jargon, no filler.** Cut "simply," "just," "easily," and any claim about how the reader will feel. The reader decides what's easy.

## Structure (S)

- **S1 — Every page is self-contained.** A page defines the objects it uses and links out for depth. It must make sense as the first and only page someone reads (Every Page Is Page One).
- **S2 — Headings are questions where readers have questions.** "How long can an Authorization be captured?" beats "Authorization capture window." Question-shaped headings land retrieval on the right chunk for humans and agents alike.
- **S3 — State the facts an agent must not guess, early and flatly.** Units, API version applicability, object names, and state names appear near the top of the page, as declarative sentences, not implied by examples.
- **S4 — Task pages follow task shape.** Title, one-line intent, prerequisites, numbered steps, verification, next step. Steps contain one action each.

## Examples (E)

- **E1 — One canonical example per concept.** Each operation or concept gets exactly one complete, correct, runnable example. Variation reads as richness to a human and as contradiction to a model. Additional variants must be explicitly labeled as variants of the canonical one.
- **E2 — Examples must be valid against the current schema.** An example that no longer matches the API is a bug, not a style issue. Flag it as `[DRIFT]`, severity above all style findings.
- **E3 — Examples show the response, not just the request.** The reader integrates against what comes back. Every request example is paired with its expected response or the event it emits.

## Release notes (R)

- **R1 — Lead with what changed for the reader,** not what the team did. "The `expires_at` field is now returned on all Authorizations" beats "We improved the Authorizations API."
- **R2 — Every breaking change is labeled `Breaking`** and states the migration action in the same entry. No reader should discover a breaking change by deploying it.
