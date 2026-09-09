# Extraction brief — `src:old-wiki-export-2026-09-04`

**Status: 9 of 497 pages extracted** (`legal/` and `health/` complete bar two index stubs, 2026-09-09). Delete this file
only when the work below is done for all of them.

| Area | Pages | Extracted |
| :--- | ---: | :--- |
| legal | 4 | **4** — `dat:0013`–`0017`, `evt:2015-02-possession-arrest`, `evt:2015-combos-retail-theft`, `con:2015-arrest-breath-test` |
| health | 6 | **5** — `dat:0018`–`0027`, `int:inference-from-refusal-is-unsound`, `pat:audit-strong-on-numbers-weak-on-meaning`. Remaining: `index` (stub) |
| places | 10 | 0 |
| meta | 12 | 0 |
| work | 15 | 0 |
| timeline | 42 | 0 |
| self | 59 | 0 |
| mind | 78 | 0 |
| interests | 96 | 0 |
| people | 175 | 0 |

**What the first pass established, for the next one.** Extraction yield was
roughly five data nodes per page in a dense area, and the highest-value nodes
were not facts about the subject but the prior system's records of its own
errors — see [`int:old-wiki-corrections-are-the-payload`](../../kb/interpretations/old-wiki-corrections-are-the-payload.md),
which also states the reading that would falsify that. Watch for `REVISED [`,
`CORRECTED [`, `CONTRADICTION [` and `GAP CLOSED [` blocks: they are the prior
wiki's own error markers and each one is a datum.

**The second pass sharpened the first pass's finding.** `health/` shows the
prior system's discipline was **real but uneven**, which is more useful than
either "careful" or "loose". Its intake ledger states the absence-of-instrument
rule better than most methodology sections (`dat:0019`) and withholds a
misleading rate figure rather than footnoting it (`dat:0018`). Its
hyperreflexivity page, same domain and weeks apart, reads a "no comment" as its
most incriminating available content and calls that reading *correct*
(`dat:0021`). Expect that unevenness across the remaining 491 pages: the
question to carry into each is not whether the page is careful but whether *this
claim on it* was checked.

**A prediction is now on the record, made before the pages were read.**
[`pat:audit-strong-on-numbers-weak-on-meaning`](../../kb/patterns/audit-strong-on-numbers-weak-on-meaning.md)
holds that the prior system was rigorous wherever a number or a document could
check it and loose wherever the claim was about meaning. It predicts `mind/`
(78) and `self/` (59) will show **markedly fewer** `REVISED`/`CORRECTED` blocks
and **more endorsed inference** than `legal/` and `health/` did. The competing
reading in
[`int:old-wiki-corrections-are-the-payload`](../../kb/interpretations/old-wiki-corrections-are-the-payload.md)
predicts the opposite. Count the error-marker blocks per page as you go — that
single tally discriminates them, and it costs nothing to collect.

**Two claims from `health/` are promotable out of testimony and should be.**
[`dat:0024`](../../kb/data/0024-old-wiki-happiness-counter-measure.md) (happiness
rates per 1,000 messages, 2015–2020) and
[`dat:0025`](../../kb/data/0025-old-wiki-prescriber-exists-routing-only.md) (four
dated messages establishing a prescriber) both terminate in computations over
the message corpus, which this system holds byte-exact and can re-pull. Every
other extracted claim terminates in "the prior wiki said so". Re-running those
two sweeps would convert them from testimony to first-party data — the cheapest
available upgrade in the whole backlog, and the template for how the other 488
pages get promoted.

One retrieval would upgrade a whole cluster at once: a **Fayette County MDJS
docket search**. It would convert `evt:2015-02-possession-arrest` from
single-source testimony to primary record and settle `con:2015-arrest-breath-test`.

| | |
| :--- | :--- |
| Source node | `kb/sources/old-wiki-export-2026-09-04.md` |
| Original | `raw/old-wiki-export-2026-09-04/whole.txt` |
| sha256 | `4037dedc019e2595fab9dca558a70ee466a39b5ed2a0d3ed58af3c25fb69d5a6` |
| Size | 7,536,214 bytes |
| Testimony | **yes** — assertions are the evidence |

## Scale, and how to work it

497 pages, ~1.86M tokens. This is not one sitting. `pages.json` gives byte
offsets, so work it page by page:

```python
import json, pathlib
d = pathlib.Path("raw/old-wiki-export-2026-09-04")
idx = json.loads((d/"pages.json").read_text())
raw = (d/"whole.txt").read_bytes()
page = next(p for p in idx["pages"] if p["path"].endswith("vaughn.md"))
text = raw[page["byte_offset"]:page["byte_offset"]+page["byte_length"]].decode()
```

Suggested order, highest evidential yield first: `timeline/` (42 pages, dated
and cross-referenced), then `people/` (175), then `health/` and `legal/` (10
together, small and dense), then `mind/` and `self/` — those two are mostly the
prior system's *conclusions* rather than its evidence, and are the pages where
the testimony discipline does the most work.

## What extraction owes

One datum per claim. The unit is *one claim about one thing, at one time, with
known provenance* — atomicity is what makes later reasoning possible, and a
paragraph compressed into a single datum cannot be cross-referenced against
anything.

```toml
+++
id            = "dat:NNNN-short-slug"
layer         = 1
type          = "datum"
title         = "..."
claim = "wiki-brain full corpus export, 2026-09-04 asserted that ..."
cites         = ["src:old-wiki-export-2026-09-04"]
attributed_to = "src:old-wiki-export-2026-09-04"    # REQUIRED — this source is testimony
confidence    = "high | moderate | low | speculative | unknown"
extraction    = "How this was obtained, and what limits it. Sample size belongs here."
+++
```

Work through, in order:

1. **Atomic datapoints** — every separable claim.
2. **Entities** — people, places, institutions, projects, artifacts. Do **not**
   merge an ambiguous match into an existing entity. An uncertain identity stays
   uncertain; a wrong merge is close to unrecoverable once things cite it.
3. **Events** — what happened, with `[when]`. Date precision is meaningful:
   `2018` and `2018-03-04` are different claims, so do not pad.
4. **Relationships** — first-class L2 objects, not adjectives on a person.
5. **Explicit beliefs**, kept apart from observations. What someone believed at
   the time is evidence about them regardless of whether it was correct.
6. **Observation vs interpretation.** Anything that is a reading goes to L3 with
   a `perspective`, never to L1.
7. **Cross-reference** against the existing corpus: what does this corroborate,
   contradict, or newly explain?
8. **Contradictions** — write the `contradiction` node. Do not resolve it.
   "The historical record is ambiguous" is a valid and often correct result.
9. **Gaps** — what did this raise that nothing answers?

## What extraction must not do

- Invent dates. Absent is `unknown`; approximate is `approx`.
- Silently merge entities on a partial name match.
- Promote a reading to L1 because it feels obvious.
- Normalise away the weird parts. Specific recurring strangeness is where the
  cognitive signature lives; generic descriptors are cheap and interchangeable.
- Restate an assertion as fact. This source is testimony: `attributed_to` is required.

## Verify when done

```sh
bin/wb-validate      # the layer invariant, testimony attribution, edge families
tests/test-invariant
```
