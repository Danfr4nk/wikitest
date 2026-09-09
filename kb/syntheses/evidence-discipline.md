+++
id         = "syn:evidence-discipline"
layer      = 5
type       = "synthesis"
title      = "Why this system is built the way it is"
cites      = ["pat:partial-data-confident-error", "int:fragments-silently-partial", "con:gitignore-is-not-protection"]
confidence = "moderate"
importance = 5
created    = "2026-09-08"
tags       = ["meta", "architecture"]

falsifiers = [
  "The layer invariant proving insufficient in practice: a chain of well-formed citations, every link legal, that still lands a conclusion on a source nobody checked. That is already flagged as an open question below and would be a real failure of the design rather than of its use.",
  "The discipline costing more than it returns — extraction slowing to the point that the corpus stays unread, which would make a less rigorous system that actually processed 497 pages the better instrument.",
  "A conclusion this architecture forbids turning out to be both true and unreachable any other way, showing the rule excludes real knowledge rather than only unfounded claims.",
]

open_questions = [
  "Does the pattern hold outside this project's own history, against the biographical material the corpus contains?",
  "Is the layer invariant sufficient, or does provenance also need to be enforced transitively — can a well-formed citation chain still rest on a source nobody checked?",
  "What does the system do when a source is later found unreliable, given L0 is append-only?",
]
+++

## The argument

The system's architecture is a direct response to one observed failure mode:
**partial evidence produces conclusions that are wrong and confident at the same
time** (`pat:partial-data-confident-error`).

If that is the failure, then the defence cannot be care, diligence or good
intentions, because the failure is invisible to the person committing it. It has
to be structural. Hence the constitutional law:

> RAW DATA → STRUCTURED FACT → INTERPRETATION → SYNTHESIS. NEVER THE REVERSE.

and its mechanical form — a node may cite only strictly-lower layers — which
makes "this conclusion became a premise" a build failure rather than a thing
someone might notice later.

## What follows from it

- **Sources are append-only.** The evidence cannot be edited to agree with the
  conclusion drawn from it.
- **Interpretations declare perspective.** Self-model, external model and LLM
  model stay separate, so "Dan believes X, the record suggests Y" is expressible
  rather than a distinction that quietly disappears.
- **Contradictions are preserved unresolved.** "The record is ambiguous" beats
  invented certainty, and `con:gitignore-is-not-protection` is the working
  example.
- **Absence is typed.** `never_observed`, `explicitly_rejected` and
  `known_not_to_occur` are three different claims.

## Status

This is a synthesis: the most disposable node in the system, and a leaf that
nothing may cite. It rests on three instances inside one project's own history,
which is thin evidence for a claim this structural. It should be challenged as
the corpus is actually worked through, and replaced without hesitation if the
biographical material does not support it.
