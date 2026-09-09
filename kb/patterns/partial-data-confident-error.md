+++
id              = "pat:partial-data-confident-error"
layer           = 4
type            = "pattern"
title           = "Partial data produces confident error, not visible uncertainty"
cites           = ["int:fragments-silently-partial", "con:gitignore-is-not-protection"]
evidence_count  = 3
counterexamples = ["dat:0003-attribution-gap"]
falsifiers      = [
  "A case where incomplete evidence produced visibly hedged output rather than confident error — the gap showing up in the conclusion's stated confidence without anyone having to go and find it.",
  "A case where the error WAS caught internally, by cross-reference or validation, rather than by someone outside the system supplying the missing piece. Every instance so far was closed by the operator.",
  "The pattern failing to appear in the 488 unextracted pages of the prior wiki, which are a large independent sample of the same failure mode's opportunity to occur.",
]
confidence      = "moderate"
importance      = 5
created         = "2026-09-08"
tags            = ["epistemics", "meta"]
+++

## The pattern

Incomplete evidence does not announce itself as incomplete. It yields
conclusions that carry the same confidence as well-founded ones, because the
missing material leaves no trace in the output. The error is not that the
answer is uncertain; it is that the uncertainty is invisible.

Instances so far:

1. **Per-counterparty message exports** (`int:fragments-silently-partial`) —
   inferences about what was absent, drawn from a source structurally incapable
   of showing presence.
2. **Privacy posture** (`con:gitignore-is-not-protection`) — a closed gitignore
   reads as "the data is protected" while a separate open channel goes
   unexamined. A partial view of the exposure surface, producing a confident and
   wrong conclusion about safety.
3. **The Drive staging copy** (`dat:0006-drive-copy-lossy`) — round-tripped
   markdown that is damaged but still plausible, so the corruption survives
   review.

## Counterexample

`dat:0003-attribution-gap` is the shape of the pattern *not* occurring: 3,086
messages that cannot be attributed are counted and declared rather than
inferred. The data is equally partial; the uncertainty is visible. That is the
difference the pattern turns on, and it is why the counterexample belongs here
rather than being tidied away.

## Confidence

Moderate. Three instances inside one project over one week is thin, and two of
them were identified by the same reasoner that named the pattern — which is
exactly the circularity the system is supposed to make visible rather than
launder.
