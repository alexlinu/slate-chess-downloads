# Slate Chess — downloads

The data that [Slate Chess](https://slatechess.com) ships with, published here
so each file can be obtained under the licence it is offered under.

The app itself is not here, and neither is the Slate engine. This repository
holds data, the terms it comes under, and enough detail to verify that the file
you downloaded is the file the app contains.

**Files are attached to [Releases](../../releases), not committed to git.** A
release keeps each version's file fixed, and keeps a clone small.

---

## What is published

| Release | File | Size | Plays for | Licence |
|---|---|---|---|---|
| [`book-v1.0.0`](../../releases/tag/book-v1.0.0) | `slate-book-v1.0.0-lichess-band0-lite.bin` | 0.8 MB | under 1400 online | **CC BY-SA 4.0** |
| [`book-v1.0.0`](../../releases/tag/book-v1.0.0) | `slate-book-v1.0.0-lichess-band1-lite.bin` | 1.3 MB | 1400–1799 online | **CC BY-SA 4.0** |
| [`book-v1.0.0`](../../releases/tag/book-v1.0.0) | `slate-book-v1.0.0-lichess-lite.bin` | 6.6 MB | 1800 online and up | **CC BY-SA 4.0** |

All three are shipped in Slate Chess, and all three are here because they have
to be. They include Lichess broadcast data under CC BY-SA 4.0, and share-alike
is not satisfied by a credit line — the work must be openly available on the
same terms. Everything else the app bundles is CC0, which asks for nothing, so
publishing it would be a courtesy rather than an obligation.

**Why three.** Below about 1,800 online, the openings someone plays say more
about their level than anything else in their game, so the weaker levels open
from books built from games at their own band — the lines those players
actually play. From 1,800 up they share the larger book.

---

## The opening book

A [Polyglot](http://hgm.nubati.net/book_format.html) `.bin`: 410,346 entries of
16 bytes each — big-endian key, move, weight and learn value, sorted by key — so
any GUI or engine that reads Polyglot will read this one. It is not specific to
Slate Chess and nothing about it is proprietary.

**Built from** Lichess broadcasts 2021–2026 (over-the-board tournaments, engine
games removed) and twelve months of Lichess rated online games, 2025-10 to
2026-09 (no bullet, both players rated 1000+, bot accounts removed).
**Changed how:** aggregated by position and filtered into a weighted Polyglot
book.

### Licence and attribution

**[CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/)** — full text
in [`LICENSES/CC-BY-SA-4.0.txt`](LICENSES/CC-BY-SA-4.0.txt).

Carry this with the file, or with anything built from it:

> Opening statistics from the Lichess.org open database (CC0) and Lichess
> broadcasts (CC BY-SA 4.0); opening names from lichess-org/chess-openings
> (CC0). This book is licensed CC BY-SA 4.0.

If you redistribute it, modified or not, it stays CC BY-SA 4.0, that attribution
travels with it, and you say what you changed. Commercial use is fine. Adding
terms that stop anyone else doing the same is not.

**Why the whole book is CC BY-SA when most of its input is CC0.** The rated
online games are CC0 and ask for nothing. The broadcast games are CC BY-SA 4.0,
and mixing them in makes the result an adaptation of CC BY-SA material.
Share-alike travels; the CC0 half does not dilute it.

### Verifying it

`SHA256SUMS` is in the release. The checksum is from the build that produced the
file, not computed afterwards from whatever was uploaded, and it matches the
copy inside the shipped app byte for byte:

```
shasum -a 256 -c SHA256SUMS
```

`slate-book-v1.0.0-lichess-lite.bin` is 6,565,536 bytes, SHA-256
`651ef2bcaa328c644fc30bda52c638715486dabdca8b267d5d4d2482045ba1ec`.

### One thing that catches people

**Polyglot stores castling as king-takes-rook**, so kingside castling reads
`e1h1`, not `e1g1`. Some libraries normalise this on read and some do not. If
castling moves look illegal, that is why — it is the format, not the file.

---

## Licences

**This repository has no single licence, deliberately.** Each file carries its
own, and a file added later carries whatever its own entry says. There is no
root `LICENSE` for the same reason: GitHub would show one licence beside the
repository name and every file would appear to be under it.

| Published file | Licence |
|---|---|
| `slate-book-v1.0.0-lichess-lite.bin` | CC BY-SA 4.0 |

### Upstream sources

Named because they deserve it, and because the chain should be checkable.

| Source | Licence |
|---|---|
| [Lichess.org open database](https://database.lichess.org/) — rated games | CC0 1.0 |
| Lichess broadcasts — over-the-board tournament relays | CC BY-SA 4.0 |
| [lichess-org/chess-openings](https://github.com/lichess-org/chess-openings) — opening names | CC0 1.0 |

CC0 requires no attribution. It is given because it is deserved.

---

## What is not here

- **The Slate Chess app** and the **Slate engine** — both closed source.
- **The full book build.** 151 MB playable, with a 4.8 GB companion database.
  Only the file the app ships is published, which is what the licence concerns.
- **Anything whose terms are unsettled.** A second v1.0.0 book variant exists
  internally that includes a games collection of unknown provenance. It is not
  distributed, it is not in the app, and it will not appear here unless that
  changes.

If the app ever bundles further book files — the per-rating-band books, or the
titled-players book — they are CC BY-SA 4.0 too and will be published here.
