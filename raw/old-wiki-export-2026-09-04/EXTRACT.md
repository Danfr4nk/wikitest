# Extraction brief — `src:old-wiki-export-2026-09-04`

**Status: not extracted.** Delete this file only when the work below is done.

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
