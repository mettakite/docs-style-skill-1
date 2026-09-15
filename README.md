# docs-style: a documentation style guide as a Claude Code skill

Style guides fail the same way everywhere: they live in a wiki, new content drifts away from them, and the standard only holds as long as one person keeps enforcing it by hand. That stopped scaling the moment AI started drafting documentation. If a model is going to write alongside me, my editorial standard has to be something the model actually follows, and something I can audit.

This repo is my documentation style standard packaged as a [Claude Code skill](https://code.claude.com/docs/en/skills). Drop the `docs-style` folder into a project's `.claude/skills/` directory and Claude applies the standard whenever it writes, edits, or reviews documentation there.

## What makes it more than a style guide in a folder

**Every rule has an ID.** T1, F2, E1. Rules get cited, not vibed. A rule that can't be checked isn't a rule.

**Every run ends with a compliance report.** The skill requires Claude to close each response with a rule-by-rule table: applied, violation found, or not applicable, with a location for each. The human editor stays the finish line, and now has an audit trail instead of a feeling. This came out of my own workflow: I kept asking the model "what rules are you following?" after the fact. The skill makes it answer that question every time, unprompted.

**It refuses to guess.** If satisfying a rule would require a fact the model doesn't have (a unit, a default, a version), it inserts a visible `[NEEDS-SOURCE]` marker instead of writing something plausible. Stylistically perfect and factually invented is the worst possible documentation.

**The rules are written to graduate into CI.** Most of them (monospace for field names, one canonical example per operation, casing matched to the schema) can eventually become lint checks that block a merge. The skill is the human-readable and model-readable form of the same standard.

## The rules themselves

See [rules/style-rules.md](./rules/style-rules.md). They're mine, distilled from eight years of writing developer documentation for payments platforms: terminology standardized against actual API behavior, self-contained pages, question-shaped headings, facts an AI agent must not guess stated early and flatly, one canonical example per concept.

That last group overlaps with my other public sample, [docs for AI agents](https://github.com/mettakite/Portfolio), on purpose. Retrieval-ready structure and machine-enforceable style are two halves of the same position: documentation should be verifiably good, not reputationally good.

## Try it

```
mkdir -p .claude/skills
cp -r docs-style .claude/skills/
```

Then, in Claude Code, ask it to review any Markdown file: "Review payment-lifecycle.md against the docs style standard." You'll get findings plus the rule-by-rule report.

## Inital run results

The report from the first run returned:

| Rule | Status | Where / Notes |
|------|--------|---------------|
| T1 | violation found | `Payment_Instrument` vs `Payment Instrument` vs `payment_instrument.*` — three spellings of one object |
| T2 | applied | All five objects defined inline before use |
| T3 | flagged — unverifiable | No schema in repo to check casing against |
| F1 | violation found | Bare field name "id" in prose; all others correctly monospaced |
| F2 | applied | Minor units stated up top; payout timing stated at point of use |
| F3 | applied | Sentences short, active throughout |
| F4 | applied | No filler words found |
| S1 | applied | Page defines its own objects; readable standalone |
| S2 | applied | Common-questions headings are question-shaped |
| S3 | applied | Version, units, naming guarantees stated flatly at top |
| S4 | not applicable | Concept page, not a task page |
| E1 | applied | Exactly one canonical sequence, labeled as such |
| E2 | flagged — unverifiable | No schema to validate against |
| E3 | not applicable | No request examples on this page |
| R1 | not applicable | Not a release note |
| R2 | not applicable | Not a release note |

---

*Ketan Mehta · [Portfolio](https://github.com/mettakite/Portfolio) · [Docs Drift](https://github.com/mettakite/Docs-Drift-Script) · [kmehta853@gmail.com](mailto:kmehta853@gmail.com)*
