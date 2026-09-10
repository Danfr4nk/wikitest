# Ingest coordinator notes

## Wave 1 (2026-09-09)
- Queue: 497 pages; wave 1 = 75 pages, dat 0059–0283, 5 workers.
- w4 done first: dat:0194–0211, 15 pages, commit ddb01cd. Verified clean.
- w1 done second: dat:0059–0078, 15 pages (index/nav pages read, no node warranted), commits 69b02fa/470d9a6/1fe1e67/d00b331/d4aac31. Verified clean.
- Schema gotcha found mid-wave: citing `src:old-wiki-export-2026-09-04` (marked testimony) without `attributed_to` fails wb-validate. Broadcast to all running workers.

## Known gaps / unavailable raw sources (do not block on these)
- raw/facebook-threads/ holds only MANIFEST.json; threads are gitignored/unavailable.
- Underlying message CSVs (ally-lubin bursts), concert table.csv, FAVS MASTERLIST.csv, dox-scan captures, twitter archive: not held locally — concert/favorites pages are prior-wiki relay, filed honestly.
- bin/wb-corroborate Twitter check returns "No Twitter sources found" even for tweet citations (may only cover FB/Telegram/YouTube); bin/corpus-query refused (corpus/manifest mismatch).
- Open discrepancies: corpus message counts 217,573 vs 203,626 vs 192,140 across passes (dat:0077); bald-eagle-cummings single uncorroborated 2026 retrospective (dat:0209, low confidence).

## Wave 2 must-include
- wiki/timeline/events/uniontown-hospital-vape-alarm.md — cross-check the 2018 vape-alarm summons MJ-14101-NT-0000082-2018 flagged by the legal/index reader (w1), docket disposition unknown.
- dat ranges continue at 0284. w1 left 0079–0103 unused (its pages done); treat as spare overflow.

## Flags from w5 (dat:0239–0257)
- Privacy: `raw/old-wiki-export-2026-09-04/whole.txt` carries third-party phone handles UNREDACTED (verified: Bill Ulmer, Brad Hubeaut, Brennan Meadows, Bruce Burish, Morgantown-call page) where the corpus snapshot redacts them as [phone redacted]. Workers followed the corpus convention (no numbers reproduced). Anything built directly from whole.txt must be redacted before publish — noted in dat:0251.
- Validation-report follow-up: the Morgantown validation report (2026-09-09) independently validated the Morgantown page's core claims; its one failing assertion ("never says yes") is on the **Jerel Coles people page**, which the Morgantown page had already corrected 2026-08-20. Wave 2: when the Coles page is ingested, confirm whether it has since been patched (report §441 recommends the patch).

## Wave 1 systemic findings (from w2, dat:0104–0125)
- Corrections don't propagate: the main Annie page corrected the June 1 exit-line attribution 2026-08-13 (it's Dan's line, not Annie's), but end-fight.md still carries the stale version. The 2015-annie-read impact analysis's "none applied" queue is partly stale too. A propagation pass over event pages quoting the June 1 closure is warranted once ingest is further along.
- Timestamp convention: the old wiki's timestamps are local Eastern; the held corpus (messages.csv) is UTC. Convert (EST/EDT) before declaring a displacement; ~5h offsets are timezone, 24h offsets are genuine.
- Cite registry: invented `src:web-2026-09-09` fails validation — web corroboration belongs in the extraction field, never as a cites id.
- Libby Titus identification: Libby = Libby Titus (Donald Fagen's wife), death 2024-10-13 confirmed three ways (dat:0116).

## Wave 2 (2026-09-09/10)
- 75 pages, dat 0284–0523. w6 = master-timeline.md solo (7654 lines, dat 0284–0343).
- Must-includes: jerel-coles.md (w8 — confirm "never says yes" patch per validation report §441), uniontown-hospital-vape-alarm.md (w10 — cross-check summons MJ-14101-NT-0000082-2018).
- w1's unused 0079–0103 held as spare overflow.

## Wave 2 partial (w10 done: dat:0479–0499)
- Vape-alarm must-include resolved: dat:0495 — summons MJ-14101-NT-0000082-2018 fully tabled, legal index carries nothing the page lacked; disposition still unknown, filed honestly.
- BFS Foods 2026-08-26 corrected sequence (cut first, killing retaliation theory) — corpus revision is newer than old-wiki export; nodes taken from fresher revision with divergence noted.
- New schema gotcha (in-progress drafts, w6/w7): invented source ids fail — `src:old-wiki-export-2026-09-09` does not exist (correct: `src:old-wiki-export-2026-09-04`); `src:imessage-corpus` does not exist (correct: `src:imessage-corpus-2026`).

## Wave 2 partial (w6 done: dat:0284–0305, master-timeline.md solo)
- 22 findings on the 7,654-line master timeline, committed as 080cf57, validates clean.
- Worker self-caught the `src:old-wiki-export-2026-09-09` typo pre-commit after the coordinator heads-up.
- Remaining repo errors (0357–0359, `src:imessage-corpus` typo) are w7's in-flight files; heads-up sent.

## Wave 2 partial (w7 done: dat:0344–0362, 19 pages)
- Direct Python CSV scans over corpus/messages.csv proved faster/more precise than bin/corpus-query (worker note).
- New contradictions: franki-faris 2016-05-09 "I just saw Franki" (held iMessage) vs page's "no contact after 2013" (dat:0357); timeline/index stats drift (3,249/360 vs master 3,661/386, dat:0362); july-2026-recontact count gap (page 624 vs held 430, dat:0358).
- ej-rags page rests entirely on unheld Facebook thread — load-bearing 2013-return dating has no re-verifiable anchor (dat:0356).

## Wave 2 partial (w9 done: dat:0434–0453, 18 pages)
- Recurring count-correction pattern: people pages counted one side only (clyde 256 not 125; davey 839 both-sides; dimitri 71 not 116; eric-springer 93 both-sides). Downstream volume work must re-derive from corpus.
- Structural held-corpus window gaps: Suz thread has 0 rows in 2016-06 and 2020-05; 11 of 16 Fred Adams rows live only in the richer 2026-09-04 export (dat:0448 extends dat:0291).
- fran-coldren death-moment story + its ~3h-later retraction both verified (dat:0446).
- Duplicate `synthesizes:` YAML bug fixed on 3 pages (fastly-fsly worker).
- dat:0454–0478 free for follow-on work.

## Wave 2 partial (w8 done: dat:0389–0420, 19 pages)
- Jerel Coles patch-state check (dat:0412): page is UNPATCHED as of 2026-09-04 snapshot — 'never says yes' categorical survives (defeated by 'Yes, save it' at 04:43), stale T2 disclaimer, stale fourteen-repetition count and timestamps. Validation report §441 rec #1 unaddressed. Flag for operator: the patch must happen in the wiki source itself.
- diane-moore, ellen-ulmer, emaly-minerd, eric-jester, felipe: thread-count corrections + verified quotes filed; unheld stories kept separate.
- james-analysis-pdf: sequence verified; aftermath superseded; unheld material flagged.

## Wave 3 partial (w13 done: dat:0614–0633, 15 pages)
- conflict-architecture's Aug 18, 2026 "love bomb" exchange verified verbatim to the second (dat:0624) — n=1 with primary backing.
- attachment-model RESOLVED 2026-08-23: 129 exit episodes corroborate dossiers' 127; 110-of-127 withdrawn (dat:0622).
- schrute-farms secret show primary-verified via 2019-09-02 iMessage (dat:0617), extends web verification.
- Honest gaps: folie-a-deux 2025 quotes absent from held corpus (dat:0618); node-locking/chaos-preference/institutional-out counts rest on unheld Gemini/dox/dansynth (dat:0623/0626/0627); jack-rusko thread entirely unheld (dat:0630).

## Wave 3 partial (w15 done: dat:0704–0731, 14 pages, 28 nodes)
- New schema gotcha: wb-validate rejects `measurement` + `attributed_to` together — remove `measurement` from relay-style count datums (broadcast to running workers).
- Full Sail page still prints August 2009 graduation with unresolved 2026-09-03 contradiction block — stale against dat:0058's September correction (propagation failure again).
- Uniontown-return: earliest-rows gap verified exactly — one attachment-only row 2011-03-19, first text 2015-11-12: a 4.5-year primary-source void covering all 2011–2015 claims.
- jajuan/jess threads: inherited MASTER dump's "everything Received" artifact; threads are two-way, not one-way.
- Dan's Law Lex-collapse: held export confirms the Casey attribution the page only inferred.

## Wave 3 partial (w11 done: dat:0524–0542, 15 pages)
- contact-gini INDEPENDENTLY REPLICATED from held corpus: inbound Gini 0.9556, top-1 33.6%, top-5 68.0%, per-year 2015–2026 (dat:0528–0531). Two-sided imputation impossible (outbound rows lack recipient handle; MASTER dump unheld).
- john-paci: 11 message artifacts verified verbatim, timestamps to the minute (dat:0539); staged-eviction arrangement stays operator testimony.
- johnny-dealer: thread recounts at 7,090 rows (page's 3,462 is a floor); page typo flagged ("Johnny is mia" 2018-04-14 → corpus 2019-04-14).
- Attribution correction: "I'm in love with Annie Ulmer" is Annie's coaching script for Dan, not his declaration (dat:0541).
- jamie-mohler: Ethan Kray alias in 2012 Twitter archive; post-transition refs begin March 2025, earlier than page's Sept 2025 floor.

## Wave 3 partial (w12 done: dat:0569–0591, 15 pages, 23 nodes)
- Note: worker's final report mentioned only the last 9 nodes; the first 14 (0569–0582) were verified present and committed separately. All 15 pages covered.
- jerad-friedline: March 2026 AI-jailbreak note is DAN's, not Jerad's; Roe-prediction attribution to Jerad has no support (dat:0585).
- john-felix: thread 156 rows to Jan 2018 (page said Jun 2016); 2026-08-18 revision's specific 2018 quotes have zero held hits.
- dec-2025-spike: strongest verification of the wave — Dec 4,620 vs 4,657, ratios replicate (dat:0591).
- calibrated-confidence: "22x" claim not reproducible (dat:0580).

## Wave 3 complete (w14 done: dat:0659–0681, 14 pages, 23 nodes)
- Direction-correction pattern: jay-lauer 11:07 runs Annie→Dan (corrects page AND dat:0064 — dat:0064 needs amendment); jim-vrabel 612 two-way not 313 one-way; jason-bermejo 761 not 1,200; james-dee dormancy framing contradicted by 147 post-July-21 messages.
- josh-brannan wav artifact verified; 2018 volume 40,500 held vs 40,514 claimed.
- Highest-value unheld sources: Jay Lauer Rick exchange (page's "single most important fact"), Bacharach discovery thread, Paci-arranged eviction.

## Wave 3 totals: 223/497 pages done, dat:0524–0731 minted.
