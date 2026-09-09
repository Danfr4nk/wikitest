+++
id            = "dat:0045-facebook-graduation-claim-september-2009"
layer         = 1
type          = "datum"
title         = "A contemporaneous 2009 message says he graduated in September, which neither the claim nor its refutation accounts for"
claim         = "The prior wiki's testimony ledger scores t013 — \"Dan graduated Full Sail (AS Recording Arts) in August 2009\", stated `certain` — as REFUTED, citing tweets showing him still in classes through December 2009. The Facebook export, a channel the ledger did not use, holds two outbound messages dated 2009-09-26: \"I acually just graduated today for music production, and moving to LA in a month to work in a studio\" and, to a different correspondent the same day, \"well i moved down here like a year ago to go to this school, but yeah LA is going to be so amazzz\". A third, 2009-09-14, reads \"i STILL have no idea about what my schedule is going to be like. this fucking school is turning my brain into mush.\" The ledger's own first cited tweet, 2009-08-31 \"so weirded out i start my last month of college tomorrow\", places the last month of college in September and so predicts a late-September completion, in agreement with the Facebook messages and in tension with the December tweets it cites alongside."
cites         = ["src:facebook-export-2026-06-23", "src:old-wiki-export-2026-09-04"]
attributed_to = "src:old-wiki-export-2026-09-04"
confidence    = "high"
extraction    = "Run 2026-09-09 with bin/wb-corroborate --facebook over the 385 fetched threads, windows 2009-06 to 2010-12 (411 messages) and 2009-09 to 2010-03 outbound-only (244 messages). Both 2009-09-26 messages are outbound and attributed to Dan Frank in the export's own block structure. The ledger's tweet quotations are transcribed from the prior wiki; the tweet archive itself is NOT held here and has not been checked."
importance    = 4
tags          = ["old-wiki", "corroboration", "facebook", "testimony"]
created       = "2026-09-09"
updated       = "2026-09-09"

[when]
start = "2009-08-31"
end   = "2009-12-19"
+++

The verdict is right and the file behind it is not closed.

## Three dated accounts, and no two of them fit

| when | channel | what it says |
| :--- | :--- | :--- |
| 2026 | his own testimony | graduated **August 2009** |
| 2009-08-31 | tweet, via the ledger | "start my last month of college tomorrow" — so, **September** |
| 2009-09-26 | Facebook, outbound, twice | "I acually just graduated today" — **September 26** |
| 2009-11-30 to 12-19 | tweets, via the ledger | "pro tools lab", "aced my practical", "taking aws final" — **still enrolled in December** |

August is wrong on every other line, so the ledger's `refuted` stands and this
datum does not disturb it. What it disturbs is the account underneath the
verdict. The ledger reads its evidence as *he was in school until December, so
August is a misremembering of December* — a displacement of four months. The
Facebook messages, which it never saw, say he told two people on the same day
that he had graduated that afternoon, five weeks after August and three months
before December.

## The tension is inside the ledger's own evidence

The 2009-08-31 tweet it quotes first is not neutral between these readings. "My
last month of college" beginning on 1 September ends in late September. That
line points at the Facebook date, not at the December ones, and the ledger cites
both without remarking that they disagree. Whatever explains the December
material — a further programme, a retake, an extension — the ledger's summary
does not contain it, and its verdict is stated as though the evidence were of one
piece.

## The uncomfortable possibility, stated and not resolved

The contemporaneous record may itself be unreliable here. The 2009-09-26 message
is a reconnection with someone he had not spoken to in a long time, it pairs the
graduation with a move to Los Angeles to work in a studio, and the Los Angeles
move did not happen — five months later he was planning New York
([`dat:0046`](0046-facebook-corroborates-two-ledger-adjudications.md)). A claim
made to impress, in the same breath as a plan that evaporated, is not the same
kind of evidence as a class schedule.

That cuts both ways and neither way is established here. It might mean he
rounded a near-graduation up to a finished one on 26 September. It might mean he
finished the AS in September and the December coursework was something else. What
it definitely means is that **a contemporaneous record is not automatically
ground truth**, which is the assumption the whole ledger is built on — see
[`int:contemporaneous-is-not-the-same-as-true`](../interpretations/contemporaneous-is-not-the-same-as-true.md).

Recorded as an open question. Settling it needs the Full Sail transcript or the
tweet archive read directly rather than through the ledger's quotations, and
neither is held here.

---

## CORRECTED [2026-09-09] — the wiki did notice, on the pages where it belonged

Written hours earlier, this datum said the prior wiki cited the August-31 tweet
and the December tweets "without remarking that they disagree" and stated its
verdict "as though the evidence were of one piece." That is wrong, and it was
inferred from the one page I had read.

`wiki/self/twitter/2009.md` and `wiki/timeline/periods/full-sail-2008-2010.md`,
both modified 2026-09-03, each carry a dated `CONTRADICTION` block holding
exactly this open. From the second, verbatim:

> the August 2009 graduation date is contradicted by Dan's own contemporaneous
> public record, in two independent places. On **2009-08-31** he wrote *"so
> weirded out i start my last month of college tomorrow"*, which puts the final
> month in September. And across November and December 2009 he is plainly still
> enrolled … **The disagreement is held rather than resolved**: a Full Sail
> transcript would settle it and the corpus does not have one.

It identifies the same "last month of college" reading this datum offered as
its own observation. It refuses to resolve. It names the artefact that would
settle it. It propagates the consequence — the "five-month Florida tail" is
measured from the disputed date and is marked disputed with it — and it fences
off what is *not* in dispute, the top-5% class standing.

**The error I made is the one this repository keeps documenting.** I read
`meta/testimony-veracity.md`, found its one-line summary flat, and concluded the
system was flat. The ledger is a *generated* page — one row per claim, outcome
and what settled it — and the reasoning was never meant to live in it. It lives
on the pages, and on the pages it is better than my criticism of it.

**What survives, and it is the part that matters.** The Facebook message of
2009-09-26 is still not in that record. The wiki's contradiction rests on two
independent points: a September "last month" and December coursework. This adds a
third, on the September side and from a channel the wiki did not hold — a
same-day, first-person *"I acually just graduated today"*, told to two people.
The wiki said only a Full Sail transcript could move this. Something short of one
has moved it: the September side now has two independent channels, and the
question sharpens from *August or December?* to *what were the November and
December classes, if he had already finished in September?*

The reservation in the section above stands and is not weakened by any of this:
the 2009-09-26 message is shaped, sent alongside a Los Angeles plan that never
happened, and a claim made to impress is not a class schedule.
