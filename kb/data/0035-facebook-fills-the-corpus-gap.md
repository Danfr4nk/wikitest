+++
id          = "dat:0035-facebook-fills-the-corpus-gap"
layer       = 1
type        = "datum"
title       = "The Facebook archive covers 17 months the message corpus cannot see at all"
claim       = "Comparing month-by-month message counts, 385 recovered Facebook threads (15,812 messages, 2007-01 to 2022-09) hold 1,304 messages in 17 calendar months for which the authoritative iMessage corpus holds exactly zero: 2021-05 through 2022-01, and 2022-03 through 2022-09. June 2021 alone holds 190 Facebook messages against a corpus count of 0, and July 2022 holds 500. Three months in that window (2022-02, 2022-10, 2022-11, 2022-12) are empty in both."
cites       = ["src:facebook-export-2026-06-23", "src:imessage-corpus-2026",
               "src:wikitest-rebuild-session-2026-09-09"]
confidence  = "high"
measurement = true
extraction  = "Computed 2026-09-09. Corpus months counted from corpus/messages.csv after sha256 verification against the manifest; Facebook months parsed from the thread bodies on the export's block structure. Both counts are of messages, not threads, and both are reproducible."
importance  = 5
tags        = ["corpus", "facebook", "coverage", "negative-data"]
created     = "2026-09-09"

[when]
start = "2021-05"
end   = "2022-09"
+++

The specific reason this retrieval was worth doing, and it lands on the exact
window the corpus policy flags as most dangerous.

`CORPUS_POLICY.md` records 2021–2022 as the place where absence-of-evidence
reasoning is least safe: the corpus has 282 messages in 2021 and none in 2022,
and nothing in it can distinguish *a life that went quiet* from *a database that
lost rows*.

The Facebook archive answers that directly. Seventeen months that were
completely dark now hold messages — and the distribution is not flat. Two months
are busy (2022-07 at 500, 2021-06 at 190) while others hold single digits, which
is the shape of a real life rather than of a uniform export artifact.

**So the corpus gap is a corpus artifact, not a silence.** Whatever was
happening in mid-2022, it was not nothing, and 500 messages in one month is
strong evidence against the quiet-life reading.

## What it still cannot settle

Facebook covers those months; it does not cover them *well*. Four months in the
window are thin or empty on both channels, and the corpus median month is 1,123
messages against a Facebook median of 32 — these are not comparable instruments,
and a Facebook month is a much smaller window onto the same period.

The right reading is that the gap is **narrowed and characterised**, not closed.
`bin/wb-corroborate --facebook --coverage YYYY-MM` grades any specific month
before a null result there is trusted.

## Why this argues for breadth

The corpus is the largest single source by two orders of magnitude and it is
blind for seventeen consecutive months. No amount of re-reading it would have
revealed that; only a second channel could. The same logic applies to the
channels still unretrieved — Twitter, location history, the Gmail captures —
each of which covers windows the first two do not.
