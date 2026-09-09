# Raw source inventory — what exists, where, and how reachable

The evidence base is larger than what is in this repository. This is the map,
recorded because working it out took a dozen calls and should not be repeated.

Reachability is the operative column: everything below exists, and the routes
differ sharply in cost.

## In the repository now

| Source | State |
| :--- | :--- |
| `old-wiki-export-2026-09-04/whole.txt` | 497 pages, 7.5 MB, byte-exact. Ingested as `src:old-wiki-export-2026-09-04`, `testimony = true` |
| `corpus/messages.csv` | 192,140 messages, 2011-03 → 2026-09. **Gitignored and re-pullable**: `bin/wb-corroborate --pull` fetches it and verifies sha256 against `corpus/manifest.json` before use |

## Reachable, not yet pulled

All of it sits in Google Drive under `wiki-brain-main-1/raw/`
(`1FoR0iAGdS3bAVdzFKYZPxnrLqyCckSdb`), mirroring the prior wiki's own `raw/`
tree: `self/`, `people/`, `places/`, `health/`, `legal/`, `mind/`, `music/`,
`interests/`, `timeline/`, `tech/`.

The richest is `raw/self/` (`16gzTW1PxZvwQMleiZ8iXKxh5rLeSDNM-`):

| Folder | What it is | Why it matters |
| :--- | :--- | :--- |
| `facebook/` | Full export, unzipped tree + an 82 MB zip | **Independent channel.** The prior wiki cites it directly; it covers years the iMessage corpus does not |
| `dox-scan/`, `dox-md/` | The document scans and markdown the prior wiki reasoned from | Includes `all_imessages_complete_dump.txt` — the **superseded** dump whose census produced `dat:0025`. Worth pulling precisely to measure how it differs |
| `twitter/` | Archive | Already load-bearing: the prior wiki's nicotine chronology and the Suboxone day-zero correction both rest on it |
| `location/` | Location history | The independent-corroboration channel `ROADMAP.md` §4 wants for the 2021–2022 corpus gap |
| `message-csv/`, `message-exports/`, `imessage/` | Earlier message extracts | Shelved by `CORPUS_POLICY.md`; useful only as evidence of what was believed |
| `gmail-captures/`, `chatgpt-export/`, `gemini-activity/`, `youtube-watch-history/`, `concerts/`, `captures/` | Assorted | Unassessed |

### The two routes, and their limits

**Drive connector, one file per call.** Works for anything small. Fine for
targeted retrieval — find the one conversation bearing on a claim and pull it.
Not viable for a tree of hundreds of files.

**Anonymous HTTPS.** Works *only* for files deliberately shared "anyone with the
link". The message corpus is, which is why `--pull` works and why the whole
corpus arrives in one request. The Facebook zip is **not**: a direct download
redirects to `accounts.google.com`. The connector also refuses it — 82 MB is
past its export limit, which is how the corpus behaves too (it refuses the
20 MB sheet while the HTTPS export serves all 48 MB of it).

**So bulk Facebook needs one action nobody has taken: sharing
`ihatedanfrank-20260623.zip` "anyone with the link", exactly as the messages
sheet already is.** One sharing change converts hundreds of connector calls into
a single request. Until then Facebook is reachable per-conversation and not in
bulk, which is enough to corroborate a specific claim and not enough to sweep.

## The rule this inventory serves

A claim extracted from the prior wiki is testimony until an independent source
says the same thing. `bin/wb-corroborate` does that against the message corpus
today. Every folder above is another channel it could run against, and the
independent ones — Facebook, Twitter, location — are worth more than the
message extracts, which are the same channel in an earlier state.

Two results so far are the argument for doing this rather than trusting the
pages: [`dat:0028`](../kb/data/0028-prescriber-quotes-partly-unverifiable.md)
(three of four quotes unverifiable, census ran on a superseded dump) and
[`dat:0030`](../kb/data/0030-combos-corroborated-first-person.md) (an admission
the prior wiki said did not exist, and its stated strongest evidence
misattributed).
