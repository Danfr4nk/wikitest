# MIGRATION.md

Rebuilding wiki-brain into `github.com/Danfr4nk/wikitest`. Delete this file when
the last row of the status table is done.

## Where things stand

| Piece | State |
| :---- | :---- |
| Six-layer architecture, schema, validator, builder, query tools | **Done** — ported from `Danfr4nk/wiki-brain` |
| Pages build-and-deploy pipeline | **Done** — `.github/workflows/pages.yml` |
| Knowledge-base seed (17 nodes, L0→L5) | **Done** — `kb/` |
| Corpus policy, manifest and derived aggregates | **Done** — `corpus/`, [`CORPUS_POLICY.md`](CORPUS_POLICY.md) |
| Authoritative `corpus/messages.csv` | **Local only, by design** — gitignored, never committed |
| Wiki body — `wiki/`, `raw/`, `app.py`, governing docs | **Blocked** — on the Mac and the external drive |
| Google Takeout | **Not started** — needs an ingestion decision first |

## Why the rebuild session could not finish this itself

The rebuild ran in a **cloud container**, not on the Mac. The paths holding the
source material —

```
/Users/daniel/Desktop/messages.csv
/Users/daniel/Desktop/wiki-brain-backup-20260907
/Volumes/MUSIC/alias/XXX/wiki-brain-main-1
/Volumes/MUSIC/wiki-brain2
/Volumes/MUSIC/TAKEOUT
```

— do not exist in that container and cannot be reached from it. A cloud session
can read what is on GitHub and nothing else. So everything recoverable *from
GitHub* was rebuilt; everything that exists only on local disk still has to be
pushed up by hand, from the Mac.

This is a transport problem, not a data-loss problem. Nothing below is lost.

## Triage before pushing anything

There are four candidate copies and they are not equal. Two of them are
probably worse than they look. Run this on the Mac first — it answers "which
copy is authoritative" without guessing:

```sh
for d in \
  ~/Desktop/wiki-brain-backup-20260907 \
  /Volumes/MUSIC/alias/XXX/wiki-brain-main-1 \
  /Volumes/MUSIC/wiki-brain2
do
  echo "=============== $d"
  [ -d "$d" ] || { echo "  MISSING"; continue; }
  echo "  files:     $(find "$d" -type f -not -path '*/.git/*' | wc -l)"
  echo "  markdown:  $(find "$d" -name '*.md' -not -path '*/.git/*' | wc -l)"
  echo "  size:      $(du -sh "$d" | cut -f1)"
  if [ -d "$d/.git" ]; then
    echo "  git:       yes"
    git -C "$d" log --oneline | head -3 | sed 's/^/    /'
    echo "  last commit: $(git -C "$d" log -1 --format=%cI 2>/dev/null)"
    echo "  dirty:     $(git -C "$d" status --porcelain | wc -l) uncommitted"
  else
    echo "  git:       NO — zip route, not push route"
  fi
  echo "  top level:"; ls "$d" | head -12 | sed 's/^/    /'
done
```

Read the output against this:

| Copy | What it probably is | Weight |
| :---- | :---- | :---- |
| `wiki-brain-backup-20260907` | Snapshot taken the day before the wipe. Newest content, and the date lines up with the corpus cutover. | **Most likely authoritative** |
| `wiki-brain2` | Unknown — a working copy or a second clone. Compare its last commit against the backup. | Tie-break |
| `wiki-brain-main-1` | Matches the name of the **Google Drive staging copy**, which is lossy — see below. If it came down from Drive, its Markdown is already damaged. | **Suspect — verify before trusting** |

The decision rule: **whichever copy has real git history and the newest commit
wins.** A copy with git history beats a copy without it even if the copy without
it looks newer, because history is the thing that cannot be reconstructed later.

### Checking whether `wiki-brain-main-1` is Drive-damaged

```sh
grep -rn '\\[-+#]\|](http://[A-Z_]*\.md)' /Volumes/MUSIC/alias/XXX/wiki-brain-main-1 --include='*.md' | head
```

Any hits mean it round-tripped through Google Docs. Do not use it as the
migration source; keep it only as a backup and as evidence of what the tree
contained.

## Why the Drive copy is not the source

`My Drive/wiki-brain-main-1` is a staging copy, not a faithful one. Every `.md`
file was converted to a Google Doc on upload, and the round-trip back is lossy.
Exporting `README.md` out of Drive returns, among other damage:

- backslash escapes through the prose — `\+`, `\-`, `\#`
- fenced code blocks flattened into paragraphs, fences gone
- relative links rewritten into invalid absolute ones —
  `[AGENT_ACCESS.md](AGENT_ACCESS.md)` came back as
  `[AGENT\_ACCESS.md](http://AGENT_ACCESS.md)`

Across 1,000+ files that corrupts every governing document, and it does it
*silently*: the output is plausible-looking Markdown, not an obvious break.

This is recorded as evidence in [`kb/data/0006-drive-copy-lossy.md`](kb/data/0006-drive-copy-lossy.md).

## Route A — the wiki body, from a copy that has git history

> **Do not force-push `main`.** `main` carries the architecture, the tooling,
> the schema and the corpus policy. A force-push deletes all of it, and
> `--force-with-lease` does **not** save you: once you have fetched, the lease
> is satisfied and the overwrite goes through.

Your local history and `main` have no commit in common, so they get joined once,
explicitly, with `--allow-unrelated-histories`. Both sides survive.

```sh
cd ~/Desktop/wiki-brain-backup-20260907     # or whichever copy triage picked

git status                      # confirm the tree is clean and complete
git log --oneline | head -5     # confirm the history you expect is here

git remote add origin https://github.com/Danfr4nk/wikitest
# already have an origin? point it here instead:
#   git remote set-url origin https://github.com/Danfr4nk/wikitest

git fetch origin
git merge origin/main --allow-unrelated-histories
```

Expect conflicts on `.gitignore` and `README.md`. Both are expected:

- **`.gitignore`** — take the **union**. Your rules (`exports/`, `site/`,
  `corpus_*.md`, the intake-ledger note) *plus* the corpus rules
  (`corpus/messages.csv`, `corpus/private/`, `shelf/**`). Drop nothing from
  either side; the corpus rules are what keep 498 people's messages out of a
  public git history.
- **`README.md`** — **merge, do not simply take one side.** This side documents
  the six-layer architecture, the tooling and the privacy split, none of which
  exists in your copy. Keep whatever your version says about the app and the
  capture/ingest loop, and keep the architecture, tooling and privacy sections
  from this side.

```sh
git add .gitignore README.md
git commit                      # completes the merge
git push -u origin main         # ordinary push, no force
```

Then confirm nothing was lost:

```sh
ls corpus/ bin/                 # tooling still present
python3 bin/wb-validate         # layer invariant still holds
git log --oneline | head        # both histories present
```

**No git history on the chosen copy?** If `git log` errors, the folder was never
a repository. Take the zip route instead: zip it, upload it, and it gets
committed here as a first import on top of `main`, with no merge needed.

## Route B — the corpus CSV stays local

`/Users/daniel/Desktop/messages.csv` is the authoritative 192,140-message export.
**It is gitignored and must stay that way.** It holds the phone numbers,
addresses and private words of 498 people who did not choose to be published,
and git history cannot be un-published.

Put it in place and verify it against the manifest rather than committing it:

```sh
cp ~/Desktop/messages.csv corpus/messages.csv
python3 bin/corpus-verify       # must match manifest.json: 48,004,305 bytes,
                                # sha256 2c53c540…d9f8cbb, 192,140 rows
```

If `corpus-verify` disagrees, the file on the Desktop is a *different* export
than the one the derived aggregates were built from. Do not overwrite the
manifest to make the error go away — re-derive instead:

```sh
python3 bin/corpus-verify --write   # re-record, only after a deliberate re-export
python3 bin/corpus-stats            # rebuild corpus/derived/
```

## Route C — Google Takeout

`/Volumes/MUSIC/TAKEOUT` is a **new L0 source** and is not yet ingested. It is
almost certainly large, mostly irrelevant, and mixed-sensitivity, so it does not
get bulk-imported. See [`ROADMAP.md`](ROADMAP.md) § "Takeout ingestion" for the
selection rule and the proposed order of work.

First step is inventory, not import:

```sh
du -sh /Volumes/MUSIC/TAKEOUT/*        # what is actually in there, by size
find /Volumes/MUSIC/TAKEOUT -maxdepth 2 -type d | head -40
```

Post that output and the ingestion plan gets written against real contents
rather than assumptions about what Takeout contains.

## Then: reconcile the wiki with the corpus

Once the wiki body is in, the corpus work has a job to do. Any claim resting on
message evidence from before 2026-09-08 traces to a shelved fragment and is
**unverified** — not wrong, just not yet read against the complete record.

```sh
grep -rln "imessage" wiki/ raw/            # what cites the old extracts
bin/corpus-query --who "Name" --context 3  # check it against the corpus
```

Procedure and the confirmed / corrected / withdrawn rule are in
[`CORPUS_POLICY.md`](CORPUS_POLICY.md). Fill in the `Pages built on it` column
of [`shelf/MANIFEST.md`](shelf/MANIFEST.md) as you go — that column is what
turns a pile of dead files into a finite re-verification queue.

Two `raw/` artifacts are already listed there awaiting the move onto the shelf:
`imessage_export_+1724XXXXXXX_20260715013702` and
`imessage_724XXXXXXX_both_all_now`.
