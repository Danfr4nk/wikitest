+++
id            = "dat:0054-facebook-archive-completed-and-recounted"
layer         = 1
type          = "datum"
title         = "The Facebook archive is now enumerated to exhaustion: 403 distinct threads, and the earlier count was of a different thing"
claim         = "The Drive holds 701 `message_1` documents across several copies of the same Facebook export, enumerated to exhaustion by walking `createdTime <` backwards in slices of 100 until a page returned no continuation token. All 701 were fetched by anonymous HTTPS export (one failed) and deduplicated by sha256, yielding 403 distinct thread files against the 392 held before — **11 new distinct threads**, and 296 byte-identical duplicates removed. Of the 403, 396 parse and 7 contain no parseable message blocks. The searchable total is 15,558 messages against 15,823 present in the archive: 265 sit under a separator rule but do not fit the speaker/text/date block pattern. The manifest written 2026-09-08 reported 15,812 messages across 385 threads, and that figure was a count of separator rules, not of parsed blocks — a different measurement of the same files, which is why 34 threads appeared to lose messages when recounted."
cites         = ["src:facebook-export-2026-06-23",
                 "src:wikitest-rebuild-session-2026-09-09"]
measurement   = true
confidence    = "high"
extraction    = "Enumerated and fetched 2026-09-09. Counts produced by bin/wb-facebook-manifest, which imports the block pattern from bin/wb-corroborate rather than restating it, so the manifest reports what the search can actually find. Deduplication is by sha256 over file bytes."
importance    = 4
tags          = ["facebook", "tooling", "coverage", "provenance"]
created       = "2026-09-09"

[when]
start = "2026-09-08"
end   = "2026-09-09"
+++

## The gain is small and it is worth stating exactly

Eleven threads. Against 392 already held, that is 2.8%.

The enumeration was worth running anyway, because before it the archive's
completeness was an assumption. It is now a measurement: the Drive contains no
`message_1` document that has not been fetched, and the walk terminated on a page
with no continuation token rather than on a guess.

## Three wrong answers on the way to it, all mine

This is recorded because the reasoning failed the same way three times and the
failures were not symmetric — each one was confident.

**1. "701 files means substantial new coverage."** Inferred from the file count
without checking content. Wrong: most of the 701 are duplicate copies.

**2. "It is all duplicates."** Inferred after the first 73 fetched files came
back byte-identical to threads already held. Also wrong, and premature — the
first batch happened to be one duplicate copy of the export, which is a property
of the fetch order, not of the archive.

**3. "128 of the 226 unfetched are genuinely new."** Inferred from Drive
`fileSize`: 128 unfetched documents had sizes appearing nowhere among the
fetched set. This was the worst of the three because it looked like evidence.
Drive's `fileSize` for a Google Doc is its internal representation, which differs
between copies of identical text, so size-mismatch carries no information about
content at all. The true answer was 11.

The sha256 dedupe was the only step that produced a fact. Everything before it
was a heuristic that returned a confident number —
[`pat:partial-data-confident-error`](../patterns/partial-data-confident-error.md),
committed three times in twenty minutes by the thing that wrote the pattern.

## The recount, and why the manifest now reports two numbers

The 2026-09-08 manifest said 15,812 messages. Recounting the same files gave
15,558, and 34 threads individually came out lower. Neither count is wrong; they
measure different things.

- **15,823 message blocks** — every message in the archive, counted by the
  separator rule that precedes each one. This is what the old manifest counted.
- **15,558 searchable** — those that parse into speaker, text and date, and are
  therefore visible to `bin/wb-corroborate`.

The 265-message gap is attachment-only posts and messages whose body breaks the
block pattern. It is not archive loss; it is **tool coverage**, and until now
nothing stated it. `MANIFEST.json` now carries both numbers and a `denominator`
field saying in words that a null result is a null over the searchable 15,558.

That is [`dat:0052`](0052-old-wiki-instrument-layer-three-rules.md)'s rule 3
applied to an instrument that did not have it, and the discrepancy is what
forced the issue: an unexplained 254-message difference between two generations
of one file is exactly the shape of a number nobody can audit.

## And rule 2, applied to the manifest itself

`bin/wb-facebook-manifest` now generates it, and **imports the block pattern from
`bin/wb-corroborate` rather than copying it.** The two counts came apart in the
first place because the manifest was written by hand with one regex while the
search ran another. Whatever the search can find is now what the manifest
reports, by construction. If the parser is wrong they are wrong together, which
is recoverable; if they disagree, the manifest describes an archive nobody is
searching, which is not.
