+++
id              = "pat:audit-strong-on-numbers-weak-on-meaning"
layer           = 4
type            = "pattern"
title           = "The prior system audited measurement rigorously and inference loosely"
cites           = ["dat:0018-old-wiki-intake-ledger-discipline",
                   "dat:0019-old-wiki-absence-of-instrument",
                   "dat:0022-old-wiki-recheck-propagation",
                   "dat:0023-old-wiki-measured-flag-overstated",
                   "dat:0021-old-wiki-endorsed-inference-from-refusal",
                   "dat:0016-old-wiki-conflated-two-legal-matters",
                   "dat:0017-old-wiki-correction-instinct-overfired",
                   "int:inference-from-refusal-is-unsound"]
evidence_count  = 7
counterexamples = ["dat:0020-old-wiki-suboxone-hedonic-tension"]
falsifiers      = [
  "mind/ (78 pages) and self/ (59) show REVISED/CORRECTED/CONTRADICTION blocks at a rate comparable to legal/ and health/. Those areas are mostly conclusions with nothing external to check them against, so under this pattern they should carry markedly fewer. A per-page tally settles it and costs nothing to collect.",
  "A page in an externally-checkable domain endorses an inference as confidently as hyperreflexivity did the refusal reading, with no number or document behind it. One clean case shows the axis is not what this pattern says it is.",
  "The prior wiki is found to have run a self-audit pass over the whole corpus on a schedule, rather than page by page as material arrived. That would make correction density a function of when a page was last touched rather than of what could check it.",
]
confidence      = "low"
importance      = 4
created         = "2026-09-09"
tags            = ["old-wiki", "epistemics", "meta"]

[when]
start = "2026-07"
end   = "2026-09"
+++

## The shape

Across six extracted pages, the prior system's self-scrutiny is sharply
asymmetric — and the axis is not domain or date but **whether the claim had
something external to collide with.**

Where a number or a document could check it, the discipline is better than most:

- corrections append rather than overwrite, so the fact a correction was needed
  survives ([`dat:0018`](../data/0018-old-wiki-intake-ledger-discipline.md))
- a misleading rate figure is deleted rather than footnoted (same)
- silence is typed as absence-of-instrument, in place, beside the numbers
  ([`dat:0019`](../data/0019-old-wiki-absence-of-instrument.md))
- dependent pages are re-checked when a cited page moves, with null results
  logged ([`dat:0022`](../data/0022-old-wiki-recheck-propagation.md))
- and, most tellingly, it audited its own measurement flags and found them
  overstated — against its own interest, on the one dataset it had been missing
  ([`dat:0023`](../data/0023-old-wiki-measured-flag-overstated.md))

Where the claim was about meaning, the same system:

- read a "no comment" as its most incriminating available content, and called
  that reading *correct* ([`dat:0021`](../data/0021-old-wiki-endorsed-inference-from-refusal.md))
- carried a lawyer, a diversion programme and a magistrate's hearing attached to
  a snack theft for three weeks ([`dat:0016`](../data/0016-old-wiki-conflated-two-legal-matters.md))
- distrusted an accurate first-person date on a plausibility argument that was
  itself false ([`dat:0017`](../data/0017-old-wiki-correction-instinct-overfired.md))

## Why `confidence = "low"`

Seven instances from **six of 497 pages** — 1.2% of the corpus, drawn from the
two smallest areas, both chosen for extraction precisely because they were
tractable.

That is not a sample. It is the pages that were easiest to check, which is very
likely the same property that made the system check itself on them.

## The counterexample, and it is a real one

[`dat:0020`](../data/0020-old-wiki-suboxone-hedonic-tension.md) is an inference
handled correctly: two of its own pages disagreed about whether a maintenance
dose caps the capacity to regulate a separate system, and it recorded the
disagreement on both rather than resolving it. No number was available; it
declined anyway.

One clean counterexample against seven instances does not break the pattern. It
does establish that the failure is not mechanical — the discipline was
*available* for inference and was applied inconsistently, which is a different
and worse finding than not having it.

## What would falsify this

Three specific observations are in the `falsifiers` field above, and the first
is the load-bearing one. The extraction order is the test, and it was set before
this pattern existed.

`mind/` (78 pages) and `self/` (59) are last precisely because they are mostly
conclusions with nothing external to check them against. This pattern predicts
they will show **markedly fewer self-corrections and markedly more endorsed
inference** than `legal/` and `health/` did.

If they instead show the same density of `REVISED` and `CORRECTED` blocks, the
pattern is wrong and the better reading is the alternative already recorded in
[`int:old-wiki-corrections-are-the-payload`](../interpretations/old-wiki-corrections-are-the-payload.md):
that self-correction marks **where external checks existed**, not where the
system was careful. Those two readings make opposite predictions about the same
491 pages, which is the useful thing about having both written down before
reading them.
