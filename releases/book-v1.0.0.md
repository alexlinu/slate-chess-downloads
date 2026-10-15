# Slate opening book v1.0.0 (lite)

The playable opening book bundled in Slate Chess 1.0, published under
CC BY-SA 4.0 because it must be.

## Asset

| File | Size | SHA-256 |
|---|---|---|
| `slate-book-v1.0.0-lichess-lite.bin` | 6,565,536 bytes | `651ef2bcaa328c644fc30bda52c638715486dabdca8b267d5d4d2482045ba1ec` |

A standard Polyglot book, 410,346 entries. Byte-for-byte the file inside the
shipped app.

## Sources

- Lichess broadcasts 2021–2026 — over-the-board tournaments, engine games
  removed (**CC BY-SA 4.0**)
- Lichess rated online games 2025-10 to 2026-09 — no bullet, both players rated
  1000+, bot accounts removed (**CC0 1.0**)
- Opening names from `lichess-org/chess-openings` (**CC0 1.0**)

## Changes made

Games aggregated by position and filtered into a weighted Polyglot book.

## Licence

**CC BY-SA 4.0** — https://creativecommons.org/licenses/by-sa/4.0/

> Opening statistics from the Lichess.org open database (CC0) and Lichess
> broadcasts (CC BY-SA 4.0); opening names from lichess-org/chess-openings
> (CC0). This book is licensed CC BY-SA 4.0.

## Verifying

    shasum -a 256 -c SHA256SUMS

## Note on castling

Polyglot encodes castling as king-takes-rook, so kingside castling reads `e1h1`,
not `e1g1`. Expected, not a defect — some libraries normalise it on read and
some do not.
