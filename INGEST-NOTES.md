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
