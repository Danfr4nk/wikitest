+++
id         = "evt:2015-combos-retail-theft"
layer      = 2
type       = "event"
title      = "Retail theft citation, Combos"
cites      = ["dat:0016-old-wiki-conflated-two-legal-matters"]
confidence = "low"
importance = 2
created    = "2026-09-09"
tags       = ["legal", "uniontown-era"]

[when]
approx = "2015, a few weeks after the possession arrest"
start  = "2015-02"
end    = "2015-12"

[[edges]]
rel         = "about"
target      = "ent:dan"
strength    = "moderate"
asserted_by = "external"
+++

## Why this is `low` confidence and still worth a node

The prior wiki is explicit that the corpus holds **no contemporaneous account**
of this: no store, no date, no charge grading, no disposition. Under its own
Gaps heading it says "Everything specific."

What survives is second-order — a joke. A trooper handling paperwork on the
separate possession matter is quoted ribbing the subject, "DID YOU STEAL MORE
COMBOS," and the page reasons that "a trooper does not make that joke about
nothing." A partner is quoted taking it up as a running bit. A February 2016
message reads "My combos are paid off," which the page notes could refer to this
fine, the possession case's, or both.

That is a real inference and a weak one, and the prior wiki presents it as such.
It is recorded here at `low` because an event whose only evidence is other
people's jokes about it is exactly the kind of claim that should carry a visible
discount.

## The reason it exists at all

It is the wrong half of [`dat:0016`](../data/0016-old-wiki-conflated-two-legal-matters.md).
For three weeks the prior wiki attributed a criminal defence, a diversion
programme and a magistrate's hearing to this citation. Recording the theft as
its own thin, low-confidence event is what keeps that correction legible —
delete it and the error becomes unreconstructable.
