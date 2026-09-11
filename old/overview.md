# Minesweeper — build overview

## Deliverable
`minesweeper.html` — a single, self-contained file (HTML + CSS + JS, no dependencies, no build step).
Open it in any browser to play.

## What was built
Classic Minesweeper with three difficulty levels:

| Level | Grid | Mines |
|---|---|---|
| Beginner | 9 × 9 | 10 |
| Intermediate | 16 × 16 | 40 |
| Expert | 16 × 30 | 99 |

Features:
- **Safe first click** — mines are seeded *after* the opening move, excluding the clicked cell and its neighbours (falls back to only the clicked cell on very tight boards).
- **Flood fill** — revealing a zero-adjacency cell cascades to the whole empty region.
- **Flagging** — right click, or long-press on touch devices; the mine counter shows mines remaining.
- **Chording** — click a revealed number (or middle-click) to clear its neighbours when the surrounding flag count matches.
- **Timer** — starts on the first reveal, capped at 999s; per-level best time persisted in `localStorage`.
- **Win/loss** — on loss all mines are revealed and wrongly-placed flags are crossed out; on win remaining mines are auto-flagged.
- **Restart** — the face button, or the `R` key.
- Classic numbering colours (1–8) and a light 3D-bevel visual style.

## Verification
Smoke-tested with Node: the embedded script parses cleanly, and 500 simulated games confirmed
the first click never hits a mine, mine count is exact, and the win condition
(`opened === rows*cols - mines`) triggers precisely when all safe cells are open.

## Notes
- Best times are stored per browser in `localStorage` under `minesweeper.best.<level>`.
- No external network calls or assets — the file works fully offline.
