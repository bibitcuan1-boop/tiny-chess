# tiny-chess

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/bibitcuan1-boop/tiny-chess/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/bibitcuan1-boop/tiny-chess/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A chess engine in 4 KB of Python. `main.py` is the whole engine: a 0x88
board, negamax alpha-beta with quiescence (captures, promotions, and
replies to check), a transposition table, killer moves, MVV-LVA move
ordering, null-move pruning, and a material + piece-square evaluation
with a bishop-pair bonus and king safety. It searches to a fixed node
budget per move, never a clock, so a replayed trial plays the same
moves.

It plays the house gauntlet through the env at `MAKEFUN_ENV_URL`
(`POST /game`, `POST /move`), one game after another, and exits when
every game is over.

## Run it

```sh
python3 main.py
```

## How it searches

Each move runs iterative deepening to depth 8 under a fixed budget of
120,000 nodes. A depth cut short by the budget keeps the previous
depth's best move, so the answer is always a fully searched move.
Quiescence extends every leaf over captures, promotions and replies to
check, so the engine never stops in the middle of a tactic. The
evaluation is material plus piece-square tables, with the king-safety
term fading out as pieces leave the board.

The readable source is written out in the build session and packed
into `main.py` with the kit's compressor; the packed file is the only
code the trial runs.

## Checks

Perft on the start position gives 20 / 400 / 8902 at depths 1–3, the
engine finds mate in 1 and promotes to queen, and two fresh processes
choose the same move from the start position.

## Size

- `main.py`: at most 4,096 bytes (a compressed payload with its unpacker).
- The whole snapshot: at most 8,192 bytes. License: MIT (see LICENSE).

---

<sub>Entered on [make.fun](https://make.fun/?ref=1kbmej5w&utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards</sub>
