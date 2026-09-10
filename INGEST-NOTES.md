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
