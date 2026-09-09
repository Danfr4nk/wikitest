+++
id            = "dat:0040-quoted-bankruptcy-message-absent"
layer         = 1
type          = "datum"
title         = "One of two quotes bracketing a weak source is verified; the other is not in the corpus"
claim         = "The prior wiki supported a bankruptcy account — sourced, by its own admission, to an AI-generated case audit — by bracketing it with two quoted messages. Checked against the authoritative corpus: \"I have to have a hearing\" is present verbatim, inbound 2026-06-22. \"I already AM bankrupt!\", attributed to November 2024, is absent; the word `bankrupt` occurs exactly twice in 192,140 messages, both in 2020 and both about politics rather than the speaker. November 2024 coverage is PARTIAL (367 messages against a median of 1,123)."
cites         = ["src:old-wiki-export-2026-09-04", "src:imessage-corpus-2026",
                 "src:wikitest-rebuild-session-2026-09-09"]
attributed_to = "src:old-wiki-export-2026-09-04"
confidence    = "high"
extraction    = "Corroboration run 2026-09-09 against the sha256-verified corpus and the 385 Facebook threads. Phrase searches plus a bare `bankrupt` search across the full corpus; the Facebook channel returns one hit across bankrupt/bankruptcy/jeffries combined."
importance    = 4
tags          = ["places", "corroboration", "old-wiki"]
created       = "2026-09-09"

[when]
start = "2024-11"
end   = "2026-06"
+++

The prior wiki did the right thing and it still did not hold.

Its source for a detailed bankruptcy account — case number, scheduled liabilities,
a court "drop dead" provision, a price history — was **an AI-generated case
audit pasted into a message thread**, and the page says so plainly: *AI-secondary,
evidently built from what she had told him.* Knowing that source was weak, it
braced the account with two contemporaneous quotes.

One brace holds. One is not there.

| Quote | Result |
| :--- | :--- |
| *"I have to have a hearing"* (June 2026) | **verified verbatim**, inbound 2026-06-22 |
| *"I already AM bankrupt!"* (Nov 2024) | **absent** |

The second is not a coverage miss in the ordinary sense. `bankrupt` appears
**twice in the entire 192,140-message corpus**, in 2020, in messages about
medical debt and the Postal Service. Nothing resembling the quoted line exists
anywhere in the record, in any year, from anyone. November 2024 is only
PARTIAL (367 messages), so it could have been said in an uncaptured window — but
the phrasing does not recur, which is unusual for a fact someone is living
inside for two years.

## Why this matters more than a single missing quote

The bracing was the page's evidence that the AI audit was tracking reality.
Half of it is now unverified, which means the case number, the liability figure
and the price history rest on the AI audit **alone** — a source the page itself
graded as secondary and built from one person's account.

This is the same shape as [`dat:0028`](0028-prescriber-quotes-partly-unverifiable.md):
a claim whose supporting quotations turn out to be partly unlocatable, where the
underlying finding may well be true and the *stated grounds for believing it*
are thinner than presented.

## A second, weaker observation, recorded as a question

The page describes the buyers' contingency as the sale of *"their own property
(19 Jeffries, ≤$229.9k)"* — Jeffries as an address. The only occurrence of
`Jeffries` in the corpus is a **person**, in a legal context, in the same message
that verified above: *"Jen Jeffries retired. But herb mitchell from Brownsville
is handling the cases."*

One occurrence is not enough to conclude the AI audit turned an attorney into a
street. It is enough to note that the corpus knows Jeffries as a name and not as
a place, and that the audit is the sort of source that makes such a conflation
possible. Filed as an open question, not a finding.
